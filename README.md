# QA Test Documentation — American Eagle

**Портфолио-проект по ручному тестированию, анализу требований и тест-дизайну интернет-магазина American Eagle.**

![Manual QA](https://img.shields.io/badge/QA-Manual%20Testing-blue)
![Execution](https://img.shields.io/badge/Test%20Cases-20%20Executed-brightgreen)
![Results](https://img.shields.io/badge/Results-18%20Passed%20%7C%202%20Needs%20Clarification-informational)

## О проекте

Репозиторий демонстрирует полный цикл работы с QA-документацией: от формулирования проверяемых гипотез и планирования тестов до ручного исполнения, сбора доказательств, анализа результатов и трассируемости.

**Система под тестированием (SUT):** [American Eagle — US storefront](https://www.ae.com/us/en). Это **независимый учебный проект**, не связанный с American Eagle и не являющийся официальным тестированием компании. Официальные бизнес-требования не предоставлены: записи `REQ-AE-XXX` обозначают проверяемые гипотезы, а не согласованную спецификацию.

## Результаты ручного тестирования

Проверки выполнены **14 октября 2026 года** на публичном сайте в условиях: Windows 10 Pro 22H2, Google Chrome 155.0.8059.80 (64-bit), US / English storefront, VPN USA, гостевая сессия.

| Модуль | Выполнено | Passed | Needs Clarification | Отчёт |
|---|---:|---:|---:|---|
| Search | 5 | 3 | 2 | [Search Summary](test-reports/SEARCH_TEST_SUMMARY_REPORT.md) |
| Catalog | 5 | 5 | 0 | [Catalog Summary](test-reports/CATALOG_TEST_SUMMARY_REPORT.md) |
| Product Details | 4 | 4 | 0 | [Product Details Summary](test-reports/PRODUCT_DETAILS_TEST_SUMMARY_REPORT.md) |
| Shopping Bag | 6 | 6 | 0 | [Shopping Bag Summary](test-reports/SHOPPING_BAG_TEST_SUMMARY_REPORT.md) |
| **Итого** | **20** | **18** | **2** | [RTM](coverage/REQUIREMENTS_TRACEABILITY_MATRIX.md) |

**Подтверждённых дефектов: 0.** Два сценария поиска (`TC-AE-204`, `TC-AE-205`) имеют статус `Needs Clarification` из-за отсутствия подтверждённых правил обработки неизвестного и пустого запроса.

**Границы результатов:** выполнены все **20 разработанных подробных тест-кейсов**, но это не означает полное покрытие сайта. В матрице отражены **23 гипотезы, из которых 20 связаны с подробными тест-кейсами (87,0% проектного покрытия)**. Проверки Catalog в части сортировки и диапазона цен проведены по видимым выборкам; крайние значения диапазонов отдельно не проверялись. Для двух сценариев Shopping Bag фактические варианты отличались от исходных предусловий, что описано в журналах.

## Документация и доказательства

| Этап | Документы |
|---|---|
| Планирование | [Test Plan](test-plan/TEST_PLAN.md) · [Requirements & Assumptions](requirements/REQUIREMENTS_AND_ASSUMPTIONS.md) |
| Трассируемость | [Requirements Traceability Matrix (RTM)](coverage/REQUIREMENTS_TRACEABILITY_MATRIX.md) |
| Search | [Checklist](checklists/SEARCH_CHECKLIST.md) · [Test Cases](test-cases/SEARCH_TEST_CASES.md) · [Execution Log](test-reports/SEARCH_EXECUTION_LOG.md) · [Summary](test-reports/SEARCH_TEST_SUMMARY_REPORT.md) · [Screenshots](screenshots/search/) |
| Catalog | [Checklist](checklists/CATALOG_CHECKLIST.md) · [Test Cases](test-cases/CATALOG_TEST_CASES.md) · [Execution Log](test-reports/CATALOG_EXECUTION_LOG.md) · [Summary](test-reports/CATALOG_TEST_SUMMARY_REPORT.md) · [Screenshots](screenshots/catalog/) |
| Product Details | [Checklist](checklists/PRODUCT_DETAILS_CHECKLIST.md) · [Test Cases](test-cases/PRODUCT_DETAILS_TEST_CASES.md) · [Execution Log](test-reports/PRODUCT_DETAILS_EXECUTION_LOG.md) · [Summary](test-reports/PRODUCT_DETAILS_TEST_SUMMARY_REPORT.md) · [Screenshots](screenshots/product-details/) |
| Shopping Bag | [Checklist](checklists/SHOPPING_BAG_CHECKLIST.md) · [Test Cases](test-cases/SHOPPING_BAG_TEST_CASES.md) · [Execution Log](test-reports/SHOPPING_BAG_EXECUTION_LOG.md) · [Summary](test-reports/SHOPPING_BAG_TEST_SUMMARY_REPORT.md) · [Screenshots](screenshots/shopping-bag/) |

Журналы выполнения содержат идентификаторы запусков, тестовые данные, фактические результаты и ссылки на скриншоты. **Test Plan остаётся исходным плановым документом**; актуальные результаты следует смотреть в журналах, итоговых отчётах и RTM.

## Применённые подходы

- **Requirements analysis:** гипотезы, допущения, открытые вопросы и связь с проверками.
- **Risk-based testing:** приоритет ключевых покупательских сценариев — поиск, выбор товара, корзина.
- **Equivalence Partitioning (EP/ECP):** существующий, неизвестный и пустой поисковые запросы.
- **Boundary Value Analysis (BVA):** запланированные граничные проверки диапазонов цен и количества; не все граничные условия фактически исполнены.
- **Decision Tables:** предусмотрены для сочетаний доступности товара, выбора варианта и действия Add to Bag.
- **State Transition Testing:** пустая корзина → добавление → изменение количества → несколько позиций → удаление.
- **Positive / Negative / Exploratory Testing:** позитивные пути, неоднозначное поведение поиска и особенности production UI.

### Примеры проверенного поведения

- **Search:** по `jeans` отображается релевантная выдача; запрос `xyzqwerty987654` возвращает товарные рекомендации/результаты без понятного правила интерпретации — [Execution Log](test-reports/SEARCH_EXECUTION_LOG.md).
- **Catalog:** сортировка `Price: Low to High` и диапазон `$25–$50` работают совместно в проверенной видимой выборке — [Execution Log](test-reports/CATALOG_EXECUTION_LOG.md).
- **Product Details:** выбор размера, добавление в корзину и соответствие выбранного варианта — [Execution Log](test-reports/PRODUCT_DETAILS_EXECUTION_LOG.md).
- **Shopping Bag:** изменение количества `1 → 2`, две разные позиции, удаление и проверка отображаемых сумм с учётом скидок и доставки — [Execution Log](test-reports/SHOPPING_BAG_EXECUTION_LOG.md).

## Статусы и достоверность

- `Passed` — выполненный сценарий соответствует проверяемому ожиданию в указанных условиях.
- `Failed` — обнаружено отклонение от ожидаемого поведения, подлежащее анализу.
- `Blocked` — проверка не может быть завершена из-за ограничений данных или окружения.
- `Needs Clarification` — требуется подтверждение ожидаемой бизнес-логики.
- `Not Run` — тест не выполнялся.

Необычное поведение не объявляется подтверждённым дефектом без достаточного обоснования. Поэтому отдельные баг-репорты по текущему прогону не создавались; демонстрационные баги не выдаются за реальные.

## Ограничения

Проверки проводились на **production-сайте** в гостевой сессии без оформления заказов. Ассортимент, цены и состояние UI могут меняться; регион, VPN, промоакции и защита от автоматизации влияют на воспроизводимость. Не выполнялись обход anti-bot-защиты, нагрузочные испытания, операции оплаты и действия с чужими данными. Области Account (`REQ-AE-021`, `REQ-AE-022`) и API (`REQ-AE-023`) пока не имеют подробных тест-кейсов в данном репозитории.

## Связанные проекты по автоматизации

- [American Eagle — Java UI/API Automation](https://github.com/ISmeneger/American_Eagle_java_automation)
- [American Eagle — Python UI/API Automation](https://github.com/ISmeneger/American_Eagle_python_automation)

Этот репозиторий показывает **что, зачем и с каким результатом тестировалось вручную**; проекты автоматизации демонстрируют реализацию UI/API-проверок на Java и Python.

## Автор

**Ilya Sidorychev**  
GitHub: [ISmeneger](https://github.com/ISmeneger)  
Направление: **QA Engineer / Automation QA Engineer (Java, Python)**.
