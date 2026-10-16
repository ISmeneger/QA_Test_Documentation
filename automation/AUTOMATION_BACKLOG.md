# Automation Backlog — American Eagle

| Поле | Значение |
|---|---|
| Document ID | `AB-AE-001` |
| Версия | `1.2` |
| Дата | 2026-10-16 |
| Автор | Ilya Sidorychev |
| Тип проекта | Независимый учебный QA-проект |
| Основание | [Test Plan](../test-plan/TEST_PLAN.md) · [RTM](../coverage/REQUIREMENTS_TRACEABILITY_MATRIX.md) · [Coverage Audit](AUTOMATION_COVERAGE_AUDIT.md) |
| Связанные проекты | [Java AQA](https://github.com/ISmeneger/American_Eagle_java_automation) · [Python AQA](https://github.com/ISmeneger/American_Eagle_python_automation) |

## Назначение

Backlog связывает ручные сценарии с существующей UI/API-автоматизацией и планом развития. **Подробная сверка всех 20 ручных сценариев с тестовыми методами обеих кодовых баз** приведена в [Automation Coverage Audit](AUTOMATION_COVERAGE_AUDIT.md). Наличие метода и assertions не гарантирует успешного прохождения последнего CI-запуска. Неподтверждённое бизнес-ожидание не является доказательством продуктового дефекта.

По итогам ручного тестирования: **20 executed, 18 Passed, 2 Needs Clarification**. Для гипотез `REQ-AE-001`–`023` проектное покрытие тест-кейсами составляет **20/23 (87%)**; это не покрытие всего сайта.

## Критерии приоритизации

- **Бизнес-ценность:** основные сценарии выбора товара, PDP и корзины — раньше второстепенной UI-индикации.
- **Определённость expected result:** непроверенную гипотезу сначала уточнить, а не кодировать как подтверждённый дефект.
- **Устойчивость данных:** использовать динамически доступные товары и SKU; очищать гостевую корзину.
- **Уровень теста:** UI для пользовательских состояний и отображения, API для операций с данными, где API доступен в разрешённых условиях.
- **Сопровождение:** учитывать production, VPN/регион, скидки, pop-up и anti-bot.

## Backlog

| ID | Manual TC | Автоматизируемая проверка | Уровень | Приоритет | Текущее состояние / действие |
|---|---|---|---|---|---|
| `AUTO-AE-01` | [201–203](../test-cases/SEARCH_TEST_CASES.md) | Поиск существующих товаров и повторный запрос | UI | P2 | Позитивный поиск есть в Java/Python; повторный `sweater` в той же сессии — расширение |
| `AUTO-AE-02` | [204–205](../test-cases/SEARCH_TEST_CASES.md) | Неизвестный и пустой запросы | UI | **P1 / Requires clarification** | Java `@KnownDefect`, Python `xfail`; ручной результат `Needs Clarification`. Уточнить правила выдачи; для пустого ввода нет отдельного теста |
| `AUTO-AE-03` | [301–302](../test-cases/CATALOG_TEST_CASES.md) | Переход в Men's Clothes и применение Low to High | UI | P2 | Навигация реализована в Java/Python; сортировка присутствует в Python |
| `AUTO-AE-04` | [303](../test-cases/CATALOG_TEST_CASES.md) | Сортировка неубывающих цен | UI | P2 | Python `test_products_are_sorted_by_price_low_to_high`; уточнить sale/regular/from |
| `AUTO-AE-05` | [304–305](../test-cases/CATALOG_TEST_CASES.md) | Диапазон `$25–$50` и совместная сортировка | UI | **Implemented (Python)** | `test_products_are_filtered_and_sorted_by_price` проверяет обе активные настройки, диапазон и порядок цен; локально 4/4 каталожных теста Passed (сообщено автором). последний Python CI 16.10.2026 успешно прошёл (общий набор) |
| `AUTO-AE-06` | [401–402](../test-cases/PRODUCT_DETAILS_TEST_CASES.md) | PDP и переключение размеров | UI | P3 | Открытие товара и перенос выбранного размера есть; усилить проверки полей и вариаций |
| `AUTO-AE-07` | [403–404](../test-cases/PRODUCT_DETAILS_TEST_CASES.md) | CTA до/после выбора размера; добавление в Bag | UI | P2 | Позитивное добавление и соответствие size/price есть; добавить проверку disabled/enabled CTA |
| `AUTO-AE-08` | [101–102](../test-cases/SHOPPING_BAG_TEST_CASES.md) | Добавление в пустую корзину, сопоставление товара | UI + API | P2 | Java/Python UI и API имеют релевантные тесты; явное empty Bag лучше установлено в API |
| `AUTO-AE-09` | [103–104](../test-cases/SHOPPING_BAG_TEST_CASES.md) | Quantity `1 → 2` и subtotal | UI + API | P2 | Прямые UI проверки присутствуют в Java/Python; проверка quantity также есть на API |
| `AUTO-AE-10` | [105–106](../test-cases/SHOPPING_BAG_TEST_CASES.md) | Два товара → удалить один → проверить второй и subtotal | UI + API | **P1** | **Implemented (Python):** `test_remove_one_of_two_products_from_cart` проверяет удаление первой позиции, сохранение второй, количество и итоговую сумму; подтверждено успешным CI 16.10.2026 |
| `AUTO-AE-11` | Вне 20 Manual TC | Unauthorized Bag, invalid SKU, invalid product | API | P3 | Есть API-тесты в Python/Java; в статистику ручных 20 кейсов не включать |

Полные ссылки на конкретные Java/Python тестовые файлы и методики сопоставления — в [Coverage Audit](AUTOMATION_COVERAGE_AUDIT.md).

## Очередность работы

1. **P1 — Search:** исследовать expected result неизвестного запроса и согласовать `KnownDefect` / `xfail` со статусом `Needs Clarification` ручного теста.
2. **Completed — Catalog:** совместная фильтрация и сортировка реализована в Python; полный CI 16.10.2026 прошёл. Снятие фильтра — необязательное расширение, не блокирует завершение портфолио.
3. **Completed — Bag:** добавлена проверка удаления одной из двух позиций с контролем сохранённой позиции и subtotal; успешный CI 16.10.2026.
4. **P2 — Search:** повторный запрос, пустое поле; не предполагать недокументированную реакцию на пустой ввод.
5. **P2 — PDP:** дополнить проверку Add to Bag до/после выбора размера.
6. **Completed — CI/Report:** Python CI 16.10.2026 — 52 сценария (47 passed, 4 skipped, 1 xfailed); объединённый Allure опубликован. Сбой внешней сборки отчёта был устранён повторным запуском без изменения тестовой логики.

## Definition of Done

- Тест имеет связь с `TC-AE-XXX` либо обозначен как отдельный сценарий.
- Есть достоверное, проверяемое ожидание и осмысленные assertions.
- Настройка и очистка данных воспроизводимы; используются доступные динамические SKU.
- UI/API-слои тестируются по назначению; результат отражён в Allure.
- Не обходится anti-bot-защита; secrets, cookies и credentials не публикуются.
- Локальный и CI-статусы фиксируются отдельно; `skip`, `xfail` и `@Disabled` не засчитываются как Passed.

## Источники

- [Automation Coverage Audit](AUTOMATION_COVERAGE_AUDIT.md)
- [Requirements Traceability Matrix](../coverage/REQUIREMENTS_TRACEABILITY_MATRIX.md)
- [Search Execution Log](../test-reports/SEARCH_EXECUTION_LOG.md)
- [Catalog Execution Log](../test-reports/CATALOG_EXECUTION_LOG.md)
- [Shopping Bag Execution Log](../test-reports/SHOPPING_BAG_EXECUTION_LOG.md)
- [Java repository](https://github.com/ISmeneger/American_Eagle_java_automation)
- [Python repository](https://github.com/ISmeneger/American_Eagle_python_automation)

## Статус сопровождения

Python-автоматизация используется как завершённый портфолио-проект. Дальнейшие пункты backlog — **возможные улучшения**, а не обязательства по постоянной адаптации к динамическому production-сайту. Повторные локальные и CI-запуски могут зависеть от рекламных Bloomreach popup, региональных окон, cookies, изменений DOM, цен, доступности товаров и anti-bot. Исторические 20 ручных результатов остаются самостоятельной выборкой и не изменяются по итогам CI.
