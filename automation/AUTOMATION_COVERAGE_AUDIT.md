# Manual QA ↔ Java/Python Automation — Coverage Audit

| Поле | Значение |
|---|---|
| Document ID | `ACA-AE-001` |
| Версия | `1.0` |
| Дата аудита | 2026-10-15 |
| Автор | Ilya Sidorychev |
| SUT | [American Eagle US storefront](https://www.ae.com/us/en) |
| Основа | [Manual Test Cases](../test-cases/) · [Java AQA](https://github.com/ISmeneger/American_Eagle_java_automation) · [Python AQA](https://github.com/ISmeneger/American_Eagle_python_automation) |
| Связанный документ | [Automation Backlog](AUTOMATION_BACKLOG.md) |

## Методика и статусы

Сопоставлены все 20 ручных тест-кейсов с опубликованными тестовыми методами Java и Python. Исходный код проверялся по конкретным тестам и assertions; это **аудит реализации**, а не проверка последнего CI/Allure запуска.

- **Direct** — существует автотест, проверяющий ключевое поведение ручного сценария; шаги и тестовые данные могут различаться.
- **Partial** — покрыта часть ручного сценария либо похожий пользовательский поток.
- **Not found** — при просмотре тестовых классов не найден соответствующий отдельный тест; вспомогательные методы могут существовать.
- **Review expected** — требуется уточнить бизнес-правило, прежде чем утверждать наличие дефекта.

## Сопоставление 20 тест-кейсов

| Manual ID | Проверяемый сценарий | Java | Python | Пробел / рекомендация |
|---|---|---|---|---|
| `TC-AE-201` | Открыть поиск | Partial: `shouldDisplaySearchInputAfterClickingSearchButtonTest` | Direct: `test_search_input_is_visible_after_click` | Сверить фокус и состояние поля |
| `TC-AE-202` | Поиск `jeans` | Direct: `searchExistingProductsTest` | Direct: `test_search_existing_products` | В Java используется подсказка, в Python отправка запроса |
| `TC-AE-203` | Повторный поиск `sweater` | Partial: позитивный поиск `jeans` | Partial: позитивный поиск `jeans` | Добавить повторный поиск в той же сессии |
| `TC-AE-204` | Неизвестный запрос | Partial / Review expected: `searchNonExistingProductTest` + `@KnownDefect` | Partial / Review expected: `test_search_non_existing_product` + `xfail` | В Manual QA — `Needs Clarification`; согласовать expected result |
| `TC-AE-205` | Пустой запрос | Not found | Not found | Проверить Enter и иконку поиска при пустом поле |
| `TC-AE-301` | Переход в Men's Clothes | Direct: `checkMensFormPageTest` | Direct: `test_mens_clothes_page_opens_correctly` | Основная навигация покрыта |
| `TC-AE-302` | Включить сортировку | Not found как отдельный UI-тест | Direct: `test_products_are_sorted_by_price_low_to_high` | Выбор сортировки включён в Python-тест |
| `TC-AE-303` | Неубывание цен | Not found | Direct: `test_products_are_sorted_by_price_low_to_high` | Учесть правила regular/sale |
| `TC-AE-304` | Фильтр `$25–$50` | Not found | Direct: `test_products_are_filtered_by_price_25_to_50` | Проверяется диапазон видимых цен |
| `TC-AE-305` | Фильтр и сортировка вместе | Not found | Direct: [`test_products_are_filtered_and_sorted_by_price`](https://github.com/ISmeneger/American_Eagle_python_automation/blob/main/tests/ui/mens_clothes/test_mens_clothes.py) | Реализована проверка обоих выбранных элементов, диапазона и порядка цен; локально Passed, CI отдельно не проверен |
| `TC-AE-401` | Открыть PDP, проверить данные | Partial: `addItemFromCatalogToCartTest`, `priceMatchesBetweenCatalogAndCartTest` | Partial: `test_add_item_from_catalog_to_bag`, `test_product_price_matches_cart_price` | Проверить весь набор полей PDP |
| `TC-AE-402` | Выбор размера | Partial: `selectedProductSizeMatchesCartSizeTest` | Partial: `test_selected_product_size_matches_cart_size` | Добавить проверку переключения вариантов |
| `TC-AE-403` | Доступность Add to Bag | Partial: позитивное добавление | Partial: позитивное добавление | Проверить состояния до/после выбора размера |
| `TC-AE-404` | Добавление и сопоставление с Bag | Direct: `addItemFromCatalogToCartTest`, `selectedProductSizeMatchesCartSizeTest` | Direct: `test_add_item_from_catalog_to_bag`, `test_selected_product_size_matches_cart_size` | Assertions распределены между тестами |
| `TC-AE-101` | Добавление из пустой Bag | Partial: UI add; API `guestUserShoppingBagLifecycleTest` | Partial: UI add; API `test_bag_item_lifecycle` | Предусловие пустой Bag явно проверено в API |
| `TC-AE-102` | Размер, товар и цена в Bag | Direct: `priceMatchesBetweenCatalogAndCartTest`, `selectedProductSizeMatchesCartSizeTest` | Direct: `test_product_price_matches_cart_price`, `test_selected_product_size_matches_cart_size` | Проверки разнесены по тестам |
| `TC-AE-103` | Quantity `1 → 2` | Direct: `addItemAndChangeQuantityInBagTest`, API `updateItemTest` | Direct: `test_change_product_quantity_and_verify_subtotal`, API lifecycle | UI и API покрытие реализовано |
| `TC-AE-104` | Subtotal после изменения количества | Direct: `addItemAndChangeQuantityInBagTest` | Direct: `test_change_product_quantity_and_verify_subtotal` | Нужна оговорка о динамических скидках |
| `TC-AE-105` | Два товара и subtotal | Partial: API `addDifferentProductsFromSameCategoryTest` | Direct: `test_two_different_products_in_cart` | Python UI проверяет обе позиции, цены, размеры и сумму |
| `TC-AE-106` | Удалить одну из двух позиций | Partial: `removeItemFromCartTest`, API `deleteItemTest` | Partial: `test_remove_product_from_cart`, API lifecycle | Добавить сохранение второй позиции и проверку subtotal |

## Проверенные файлы реализации

**Java** (ветка `master`): [SearchTests.java](https://github.com/ISmeneger/American_Eagle_java_automation/blob/master/src/test/java/tests/ui/search/SearchTests.java), [HomePageTests.java](https://github.com/ISmeneger/American_Eagle_java_automation/blob/master/src/test/java/tests/ui/HomePageTests.java), [MensClothesChapterUnauthorizedUserTests.java](https://github.com/ISmeneger/American_Eagle_java_automation/blob/master/src/test/java/tests/ui/MensClothesChapterUnauthorizedUserTests.java), [BagApiTests.java](https://github.com/ISmeneger/American_Eagle_java_automation/blob/master/src/test/java/tests/api/BagApiTests.java), [E2EApiTests.java](https://github.com/ISmeneger/American_Eagle_java_automation/blob/master/src/test/java/tests/api/E2EApiTests.java).

**Python** (ветка `main`): [test_search.py](https://github.com/ISmeneger/American_Eagle_python_automation/blob/main/tests/ui/home_page/test_search.py), [test_mens_clothes.py](https://github.com/ISmeneger/American_Eagle_python_automation/blob/main/tests/ui/mens_clothes/test_mens_clothes.py), [test_product_cart.py](https://github.com/ISmeneger/American_Eagle_python_automation/blob/main/tests/ui/mens_clothes/test_product_cart.py), [test_bag_api.py](https://github.com/ISmeneger/American_Eagle_python_automation/blob/main/tests/api/test_bag_api.py).

## Приоритеты следующей итерации

1. **P1:** уточнить ожидаемый результат поиска неизвестного запроса; согласовать `@KnownDefect` / `xfail` с `Needs Clarification` ручного проекта.
2. **Completed in Python:** `TC-AE-305` — совместная сортировка и фильтрация в одной UI-сессии; проверить CI отдельно.
3. **P1:** `TC-AE-106` — две позиции, удаление одной, проверка оставшейся позиции и subtotal.
4. **P2:** `TC-AE-205` — поведение пустого запроса.
5. **P2:** `TC-AE-203` — повторный запрос в той же сессии; `TC-AE-403` — Add to Bag до/после выбора.
6. **P3:** расширить PDP-проверки `TC-AE-401/402`.

**Ограничения:** наличие метода в репозитории не подтверждает его успешное прохождение в последнем CI-запуске. `@Disabled`, `skip` и `xfail` не считаются успешными результатами выполнения. Полная трассировка требований представлена в [RTM](../coverage/REQUIREMENTS_TRACEABILITY_MATRIX.md).
