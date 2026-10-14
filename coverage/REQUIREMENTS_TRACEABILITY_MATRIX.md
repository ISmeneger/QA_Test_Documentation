# Requirements Traceability Matrix (RTM) — American Eagle

| Поле | Значение |
|---|---|
| Document ID | `RTM-AE-001` |
| Версия | `0.3` — проектное покрытие и фактическое выполнение |
| Дата | `2026-10-13` |
| Автор | Ilya Sidorychev |
| Основание | [Requirements & Assumptions](../requirements/REQUIREMENTS_AND_ASSUMPTIONS.md) |
| Test Plan | [TP-AE-001](../test-plan/TEST_PLAN.md) |
| Статус выполнения | **9 test cases executed:** Search 3 Passed + 2 Needs Clarification; Product Details 4 Passed |

> **Ограничение:** `REQ-AE-001`–`REQ-AE-023` — проверяемые гипотезы независимого учебного проекта, **не официальные требования** American Eagle. Матрица отражает наличие спроектированных сценариев, но не их успешное выполнение. Связь с чек-листом означает наличие планируемой проверки, а не результат тестирования.

## 1. Сводка проектного покрытия

| Показатель | Значение |
|---|---:|
| Гипотез в реестре | 23 |
| Гипотез с хотя бы одним подробным тест-кейсом | 20 |
| Гипотез без подробного тест-кейса | 3 |
| Проектное покрытие гипотез тест-кейсами | **20 / 23 = 87,0%** |
| Создано подробных тест-кейсов | 20 |
| Выполнено вручную в рамках этого проекта | **9 из 20 тест-кейсов** |
| Passed | **7** |
| Needs Clarification | **2** |
| Not Run | **11** |

Все `REQ-AE-001`–`REQ-AE-020` имеют минимум один соответствующий тест-кейс. Дополнительные области `REQ-AE-021`–`REQ-AE-023` остаются **без подробных тест-кейсов**. Отдельные пункты чек-листов также не превращены в подробные тест-кейсы; метрика выше не означает 100% покрытие сценариев.

## 2. Матрица трассируемости

Обозначения: `Designed` — подробный тест-кейс существует; `Gap` — подробный тест-кейс отсутствует. Execution отражает фактические результаты, а не статус проектирования. Ссылки на чек-листы ведут к документам целиком, номера проверок указаны рядом.

| Гипотеза | Область | Чек-лист (ID) | Тест-кейсы | Design status | Execution |
|---|---|---|---|---|---|
| `REQ-AE-001` | Search: открытие поля | [Search](../checklists/SEARCH_CHECKLIST.md) `CL-SR-001–003` | [TC-AE-201](../test-cases/SEARCH_TEST_CASES.md) | Designed | [Passed](../test-reports/SEARCH_EXECUTION_LOG.md) |
| `REQ-AE-002` | Search: релевантный товар | [Search](../checklists/SEARCH_CHECKLIST.md) `CL-SR-006–008` | [TC-AE-202](../test-cases/SEARCH_TEST_CASES.md) | Designed | [Passed](../test-reports/SEARCH_EXECUTION_LOG.md) |
| `REQ-AE-003` | Search: отправка запроса | [Search](../checklists/SEARCH_CHECKLIST.md) `CL-SR-004–005, 009` | [TC-AE-202, 203](../test-cases/SEARCH_TEST_CASES.md) | Designed | [Passed (`TC-AE-202`, `TC-AE-203`)](../test-reports/SEARCH_EXECUTION_LOG.md) |
| `REQ-AE-004` | Search: неизвестный запрос | [Search](../checklists/SEARCH_CHECKLIST.md) `CL-SR-012–013` | [TC-AE-204](../test-cases/SEARCH_TEST_CASES.md) | Designed; Needs Clarification | [Needs Clarification](../test-reports/SEARCH_EXECUTION_LOG.md) |
| `REQ-AE-005` | Search: пустой запрос | [Search](../checklists/SEARCH_CHECKLIST.md) `CL-SR-010–011` | [TC-AE-205](../test-cases/SEARCH_TEST_CASES.md) | Designed; Needs Clarification | [Needs Clarification](../test-reports/SEARCH_EXECUTION_LOG.md) |
| `REQ-AE-006` | Catalog: переход в категорию | [Catalog](../checklists/CATALOG_CHECKLIST.md) `CL-CT-001–004` | [TC-AE-301](../test-cases/CATALOG_TEST_CASES.md) | Designed | Not Run |
| `REQ-AE-007` | Catalog: выбор сортировки | [Catalog](../checklists/CATALOG_CHECKLIST.md) `CL-CT-005–007` | [TC-AE-302](../test-cases/CATALOG_TEST_CASES.md) | Designed | Not Run |
| `REQ-AE-008` | Catalog: порядок цен | [Catalog](../checklists/CATALOG_CHECKLIST.md) `CL-CT-008–009` | [TC-AE-303](../test-cases/CATALOG_TEST_CASES.md) | Designed; Needs Clarification | Not Run |
| `REQ-AE-009` | Catalog: фильтрация цен | [Catalog](../checklists/CATALOG_CHECKLIST.md) `CL-CT-011–020` | [TC-AE-304, 305](../test-cases/CATALOG_TEST_CASES.md) | Designed; Needs Clarification | Not Run |
| `REQ-AE-010` | Catalog: состояние UI | [Catalog](../checklists/CATALOG_CHECKLIST.md) `CL-CT-007, 013, 018–020` | [TC-AE-302, 304, 305](../test-cases/CATALOG_TEST_CASES.md) | Designed | Not Run |
| `REQ-AE-011` | PDP: открытие товара | [Product](../checklists/PRODUCT_DETAILS_CHECKLIST.md) `CL-PD-001–003` | [TC-AE-401](../test-cases/PRODUCT_DETAILS_TEST_CASES.md) | Designed | **Passed** — [PD Log](../test-reports/PRODUCT_DETAILS_EXECUTION_LOG.md) |
| `REQ-AE-012` | PDP: данные товара | [Product](../checklists/PRODUCT_DETAILS_CHECKLIST.md) `CL-PD-004–009` | [TC-AE-401](../test-cases/PRODUCT_DETAILS_TEST_CASES.md) | Designed | **Passed** — [PD Log](../test-reports/PRODUCT_DETAILS_EXECUTION_LOG.md) |
| `REQ-AE-013` | PDP: выбор варианта | [Product](../checklists/PRODUCT_DETAILS_CHECKLIST.md) `CL-PD-010–013` | [TC-AE-402](../test-cases/PRODUCT_DETAILS_TEST_CASES.md) | Designed | **Passed** — [PD Log](../test-reports/PRODUCT_DETAILS_EXECUTION_LOG.md) |
| `REQ-AE-014` | PDP: доступность Add to Bag | [Product](../checklists/PRODUCT_DETAILS_CHECKLIST.md) `CL-PD-014–017` | [TC-AE-403](../test-cases/PRODUCT_DETAILS_TEST_CASES.md) | Designed; Needs Clarification | **Passed** — [PD Log](../test-reports/PRODUCT_DETAILS_EXECUTION_LOG.md) |
| `REQ-AE-015` | Bag: добавление | [Bag](../checklists/SHOPPING_BAG_CHECKLIST.md) `CL-BAG-003–005` | [TC-AE-101](../test-cases/SHOPPING_BAG_TEST_CASES.md), [TC-AE-404](../test-cases/PRODUCT_DETAILS_TEST_CASES.md) | Designed | **Partial: TC-AE-404 Passed; Bag test cases Not Run** — [PD Log](../test-reports/PRODUCT_DETAILS_EXECUTION_LOG.md) |
| `REQ-AE-016` | Bag: размер и цена | [Bag](../checklists/SHOPPING_BAG_CHECKLIST.md) `CL-BAG-006–007` | [TC-AE-102](../test-cases/SHOPPING_BAG_TEST_CASES.md), [TC-AE-404](../test-cases/PRODUCT_DETAILS_TEST_CASES.md) | Designed; Needs Clarification | **Partial: TC-AE-404 Passed; Bag test cases Not Run** — [PD Log](../test-reports/PRODUCT_DETAILS_EXECUTION_LOG.md) |
| `REQ-AE-017` | Bag: quantity | [Bag](../checklists/SHOPPING_BAG_CHECKLIST.md) `CL-BAG-008–014` | [TC-AE-103](../test-cases/SHOPPING_BAG_TEST_CASES.md) | Designed | Not Run |
| `REQ-AE-018` | Bag: subtotal | [Bag](../checklists/SHOPPING_BAG_CHECKLIST.md) `CL-BAG-011–012, 017` | [TC-AE-104, 105](../test-cases/SHOPPING_BAG_TEST_CASES.md) | Designed; Needs Clarification | Not Run |
| `REQ-AE-019` | Bag: удаление | [Bag](../checklists/SHOPPING_BAG_CHECKLIST.md) `CL-BAG-018–020` | [TC-AE-106](../test-cases/SHOPPING_BAG_TEST_CASES.md) | Designed | Not Run |
| `REQ-AE-020` | Bag: несколько товаров | [Bag](../checklists/SHOPPING_BAG_CHECKLIST.md) `CL-BAG-015–018` | [TC-AE-105, 106](../test-cases/SHOPPING_BAG_TEST_CASES.md) | Designed | Not Run |
| `REQ-AE-021` | Account: обязательные поля | — | — | **Gap** | Not Run |
| `REQ-AE-022` | Account: формат email | — | — | **Gap** | Not Run |
| `REQ-AE-023` | API: guest/browse/inventory/bag | — | — | **Gap / Needs Clarification** | Not Run |

## 3. Незакрытые области и ограничения

1. **Account (`REQ-AE-021`, `REQ-AE-022`):** в реестре гипотез обозначены проверки формы, но отдельные чек-лист и тест-кейсы ещё не созданы. Успешная регистрация может блокироваться anti-bot-защитой; обход не планируется.
2. **API (`REQ-AE-023`):** эта область пока представлена гипотезой. Существующие Java/Python API-автотесты не подменяют ручную документацию и отдельный протокол исполнения.
3. **Чек-листы шире тест-кейсов:** exploratory, условные и дополнительные проверки могут не иметь отдельного подробного сценария. Не трактовать метрику `87,0%` как покрытие всех возможных тестов.
4. **Неопределённая бизнес-логика:** поиск рекомендаций, сортировка sale/regular price, границы цен, SKU, скидки и subtotal остаются открытыми вопросами; до уточнения использовать `Needs Clarification`.

## 4. Что обновлять после реального прогона

В каждой выполненной записи необходимо указать `Run ID`, дату/время/часовой пояс, браузер/ОС, регион/локаль/VPN, URL/данные товара, `Actual Result`, достоверный источник `Expected Result`, статус и `Evidence` (если есть). Ссылки на запись запуска и на подтверждённый дефект можно впоследствии добавить в матрицу отдельными столбцами или в отдельном execution report.

Для Search выполнены пять сценариев; см. [Execution Log](../test-reports/SEARCH_EXECUTION_LOG.md) и [Search Test Summary](../test-reports/SEARCH_TEST_SUMMARY_REPORT.md). Следующая итерация — Product Details и Shopping Bag.

## 5. Связанные документы

- [Search Execution Log](../test-reports/SEARCH_EXECUTION_LOG.md)
- [Search Test Summary](../test-reports/SEARCH_TEST_SUMMARY_REPORT.md)

- [README](../README.md)
- [Requirements & Assumptions](../requirements/REQUIREMENTS_AND_ASSUMPTIONS.md)
- [Test Plan](../test-plan/TEST_PLAN.md)
- [Search Test Cases](../test-cases/SEARCH_TEST_CASES.md)
- [Product Details Execution Log](../test-reports/PRODUCT_DETAILS_EXECUTION_LOG.md)
- [Product Details Test Summary](../test-reports/PRODUCT_DETAILS_TEST_SUMMARY_REPORT.md)
- [Catalog Test Cases](../test-cases/CATALOG_TEST_CASES.md)
- [Product Details Test Cases](../test-cases/PRODUCT_DETAILS_TEST_CASES.md)
- [Shopping Bag Test Cases](../test-cases/SHOPPING_BAG_TEST_CASES.md)

---

*Версия 0.3 — проектное покрытие и результаты пяти выполненных сценариев Search.*
