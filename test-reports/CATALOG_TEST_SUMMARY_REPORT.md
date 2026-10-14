# Catalog — Test Summary Report (American Eagle)

| Поле | Значение |
|---|---|
| Document ID | `TSR-AE-CATALOG-001` |
| Версия | `1.0` |
| Дата | `2026-10-14` |
| Автор | Ilya Sidorychev |
| Модуль | Catalog (Men's Clothes) |
| Execution Log | [CATALOG_EXECUTION_LOG.md](CATALOG_EXECUTION_LOG.md) |
| Test Cases | [CATALOG_TEST_CASES.md](../test-cases/CATALOG_TEST_CASES.md) |
| RTM | [Requirements Traceability Matrix](../coverage/REQUIREMENTS_TRACEABILITY_MATRIX.md) |

## 1. Цель

Подвести итоги пяти ручных проверок каталога: навигация, сортировка по цене, порядок выдачи, ценовой фильтр и совместная работа фильтра с сортировкой.

## 2. Окружение

Windows 10 Pro 22H2 (build 19045.6456, x64); Google Chrome 155.0.8059.80 (64-bit); US / English storefront; VPN USA; Guest; дата 14.10.2026. Время отдельных шагов не зафиксировано.

## 3. Итоги

| Метрика | Значение |
|---|---:|
| Спроектировано тест-кейсов Catalog | 5 |
| Выполнено | 5 |
| Passed | 5 |
| Failed | 0 |
| Blocked | 0 |
| Needs Clarification (итоговых статусов) | 0 |
| Подтверждённых дефектов | 0 |

| Test Case | Результат | Основание |
|---|---|---|
| `TC-AE-301` | **Passed** | Открылся Men's Clothes с карточками и фильтрами |
| `TC-AE-302` | **Passed** | Активировалась сортировка `Price: Low to High` |
| `TC-AE-303` | **Passed (sampled)** | Текущие цены проверенных карточек не убывают |
| `TC-AE-304` | **Passed (sampled)** | Фильтр `$25–$50` активен; проверенные цены в интервале |
| `TC-AE-305` | **Passed (sampled)** | Одновременно активны фильтр и сортировка; видимые цены согласованы |

## 4. Ограничения

- Метка `Passed (sampled)` означает положительный результат на видимой выборке, не подтверждение всего каталога.
- Не проверены точные граничные значения `$25.00` и `$50.00` и все правила скидочных цен.
- Обнаруженные рекламные блоки/промо-вставки не трактовались как товарные позиции при оценке порядка цен.
- Проверки проводились на публичном сайте; официальные бизнес-требования не предоставлены.

## 5. Общий статус документации

После добавления этого журнала: 20/20 спроектированных тест-кейсов имеют записи о выполнении — **18 Passed, 2 Needs Clarification, 0 Failed**. Это не означает полного покрытия всех функций American Eagle. Проектное покрытие реестра гипотез подробными тест-кейсами остаётся **20/23 = 87,0%**.

## 6. Связанные материалы

- [Catalog Execution Log](CATALOG_EXECUTION_LOG.md)
- [Catalog Checklist](../checklists/CATALOG_CHECKLIST.md)
- [Catalog Test Cases](../test-cases/CATALOG_TEST_CASES.md)
- [Requirements & Assumptions](../requirements/REQUIREMENTS_AND_ASSUMPTIONS.md)
- [RTM](../coverage/REQUIREMENTS_TRACEABILITY_MATRIX.md)

---

*Результаты относятся к выполненным сценариям и указанному окружению. Проект не связан с компанией American Eagle.*
