# Shopping Bag — Manual Execution Log (American Eagle)

| Поле | Значение |
|---|---|
| Document ID | `EXLOG-AE-BAG-001` |
| Версия | `1.1` |
| Дата ручной проверки | `2026-10-14` |
| Автор | Ilya Sidorychev |
| SUT | [American Eagle — US storefront](https://www.ae.com/us/en) |
| Test Cases | [Shopping Bag Test Cases](../test-cases/SHOPPING_BAG_TEST_CASES.md) |
| Requirements | [Requirements & Assumptions](../requirements/REQUIREMENTS_AND_ASSUMPTIONS.md) |
| Checklist | [Shopping Bag Checklist](../checklists/SHOPPING_BAG_CHECKLIST.md) |
| Источник результатов | Скриншоты и описание выполненных действий |

> **Область отчёта.** Зафиксированы шесть ручных сценариев Shopping Bag. Описаны фактически выполненные действия и отклонения от исходных предусловий для TC-AE-105 и TC-AE-106. Результаты относятся только к проверенным вариантам сценариев; официальные требования American Eagle не предоставлены.

## 1. Тестовое окружение

| Параметр | Значение |
|---|---|
| Дата | 2026-10-14 |
| Точное время отдельных действий | Не зафиксировано |
| ОС | Windows 10 Pro, 22H2, build 19045.6456, x64 |
| Браузер | Google Chrome 155.0.8059.80 (64-bit) |
| Storefront | US / English (`/us/en`) |
| VPN exit region | USA |
| Сессия | Guest (без авторизации) |
| Границы | Штатные действия в UI; заказ и оплата не выполнялись |

## 2. Сводка выполнения

| Run ID | Test Case | Сценарий | Результат | Evidence |
|---|---|---|---|---|
| `RUN-AE-BAG-20261014-01` | `TC-AE-101` | Добавление в пустую корзину | **Passed** | [Снимок 1](../screenshots/shopping-bag/TC-AE-101_empty_bag.png), [снимок 2](../screenshots/shopping-bag/TC-AE-101_one_item.png) |
| `RUN-AE-BAG-20261014-02` | `TC-AE-102` | Сохранение варианта и цены | **Passed** | [Снимок 1](../screenshots/shopping-bag/TC-AE-101_one_item.png) |
| `RUN-AE-BAG-20261014-03` | `TC-AE-103` | Изменение количества 1 → 2 | **Passed** | [Снимок 1](../screenshots/shopping-bag/TC-AE-103_qty_1.png), [снимок 2](../screenshots/shopping-bag/TC-AE-103_qty_2_summary.png) |
| `RUN-AE-BAG-20261014-04` | `TC-AE-104` | Расчёт стоимости при увеличении Qty | **Passed** | [Снимок 1](../screenshots/shopping-bag/TC-AE-103_qty_2_summary.png), [снимок 2](../screenshots/shopping-bag/TC-AE-101_one_item.png) |
| `RUN-AE-BAG-20261014-05` | `TC-AE-105` | Два разных товара | **Passed** | [Снимок 1](../screenshots/shopping-bag/TC-AE-105_two_products.png) |
| `RUN-AE-BAG-20261014-06` | `TC-AE-106` | Удаление одной позиции из двух | **Passed** | [Снимок 1](../screenshots/shopping-bag/TC-AE-105_two_products.png), [снимок 2](../screenshots/shopping-bag/TC-AE-106_after_removal.png) |

**Итог:** 6 executed · 6 passed · 0 failed · 0 blocked · 0 confirmed defects. Для TC-AE-105 и TC-AE-106 отражены различия между исходным тест-дизайном и фактическими условиями.

## 3. Подробные записи

### RUN-AE-BAG-20261014-01 — TC-AE-101

- **Название:** Добавление в пустую корзину
- **Requirements:** `REQ-AE-015`
- **Priority:** Critical
- **Status:** **Passed**

| Поле | Описание |
|---|---|
| Действия | Пустая корзина → выбран товар → Add to Bag → Shopping Bag |
| Expected Result (проверяемая гипотеза) | Корзина содержит одну позицию выбранного товара |
| Actual Result | Исходное состояние: «Your bag is empty», значок 0. После добавления джинсов отображаются «1 Item», Qty 1, цвет Light Vintage и размер 000 Regular. |

**Evidence:** [Снимок 1](../screenshots/shopping-bag/TC-AE-101_empty_bag.png), [снимок 2](../screenshots/shopping-bag/TC-AE-101_one_item.png).

**Defect:** None.

**Remarks:** Проверенные параметры зафиксированы на скриншотах.

### RUN-AE-BAG-20261014-02 — TC-AE-102

- **Название:** Сохранение варианта и цены
- **Requirements:** `REQ-AE-016`
- **Priority:** High
- **Status:** **Passed**

| Поле | Описание |
|---|---|
| Действия | Выбрать товар Light Vintage, размер 000 Regular → добавить → сопоставить PDP и Bag |
| Expected Result (проверяемая гипотеза) | Название, выбранный вариант и цена согласованы |
| Actual Result | В корзине: AE Lowest-Rise Baggy Wide-Leg Jean, Light Vintage, 000 Regular, Qty 1; `$48.71` после скидки, `$74.95` первоначальная цена. Соответствует ранее зафиксированным параметрам PDP. |

**Evidence:** [Снимок 1](../screenshots/shopping-bag/TC-AE-101_one_item.png).

**Defect:** None.

**Remarks:** Сравнение с ранее зафиксированными снимками PDP; актуальные промоусловия динамические.

### RUN-AE-BAG-20261014-03 — TC-AE-103

- **Название:** Изменение количества 1 → 2
- **Requirements:** `REQ-AE-017`
- **Priority:** Critical
- **Status:** **Passed**

| Поле | Описание |
|---|---|
| Действия | Shopping Bag → Edit → Qty 2 → Update Bag |
| Expected Result (проверяемая гипотеза) | Количество 2, без изменения товара и варианта |
| Actual Result | Qty изменилось с 1 на 2; Light Vintage и 000 Regular сохранились. Стоимость строки после скидки — `$97.42`. |

**Evidence:** [Снимок 1](../screenshots/shopping-bag/TC-AE-103_qty_1.png), [снимок 2](../screenshots/shopping-bag/TC-AE-103_qty_2_summary.png).

**Defect:** None.

**Remarks:** Промежуточное состояние панели Edit — дополнительный скриншот.

### RUN-AE-BAG-20261014-04 — TC-AE-104

- **Название:** Расчёт стоимости при увеличении Qty
- **Requirements:** `REQ-AE-018`
- **Priority:** Critical
- **Status:** **Passed**

| Поле | Описание |
|---|---|
| Действия | Сопоставить суммы для Qty 1 и Qty 2, скидку и доставку |
| Expected Result (проверяемая гипотеза) | Расчёт согласован с отображаемыми компонентами |
| Actual Result | Qty 2: Merchandise `$149.90`; Item Discounts −`$52.48`; Shipping Free; Sub Total `$97.42`. Равенство: 149.90 − 52.48 = 97.42. При Qty 1: `$74.95` − `$26.24` + `$7.95` = `$56.66` (отдельно подтверждено поздним скриншотом). |

**Evidence:** [Снимок 1](../screenshots/shopping-bag/TC-AE-103_qty_2_summary.png), [снимок 2](../screenshots/shopping-bag/TC-AE-101_one_item.png).

**Defect:** None.

**Remarks:** Отображаемый Sub Total в данном интерфейсе включает платную доставку; налоговая составляющая отдельно не подтверждена.

### RUN-AE-BAG-20261014-05 — TC-AE-105

- **Название:** Два разных товара
- **Requirements:** `REQ-AE-020`
- **Priority:** High
- **Status:** **Passed**

| Поле | Описание |
|---|---|
| Действия | К джинсам (Qty 2) добавить свитер (Qty 1) → открыть Bag |
| Expected Result (проверяемая гипотеза) | Два разных товара отображаются отдельно; стоимость согласована |
| Actual Result | В корзине две товарные позиции: джинсы Light Vintage / 000 Regular × 2 (`$97.42`), свитер Brown / XS × 1 (`$49.95`). Заголовок «3 Items». Sub Total `$147.37` = 97.42 + 49.95. |

**Evidence:** [Снимок 1](../screenshots/shopping-bag/TC-AE-105_two_products.png).

**Defect:** None.

**Remarks:** Отклонение от исходного TC: перед добавлением свитера джинсы уже были Qty 2 (не Qty 1); проверен вариант с двумя SKU и тремя единицами.

### RUN-AE-BAG-20261014-06 — TC-AE-106

- **Название:** Удаление одной позиции из двух
- **Requirements:** `REQ-AE-019`, `REQ-AE-020`
- **Priority:** High
- **Status:** **Passed**

| Поле | Описание |
|---|---|
| Действия | При двух позициях удалить свитер → проверить оставшиеся джинсы и суммы |
| Expected Result (проверяемая гипотеза) | Удалённый товар исчез, другая позиция сохранилась, сумма обновилась |
| Actual Result | После удаления свитера остались джинсы Light Vintage / 000 Regular × 2; Sub Total снизился с `$147.37` до `$97.42` (−`$49.95`). |

**Evidence:** [Снимок 1](../screenshots/shopping-bag/TC-AE-105_two_products.png), [снимок 2](../screenshots/shopping-bag/TC-AE-106_after_removal.png).

**Defect:** None.

**Remarks:** Отклонение от исходного TC: удалён свитер B, а не товар A; исходные количества были A × 2, B × 1. Эквивалентная проверка удаления отдельной позиции.

## 4. Проверка расчётов и терминологии

| Состояние | Merchandise | Item Discounts | Shipping | Отображаемый Sub Total |
|---|---:|---:|---:|---:|
| Джинсы × 1 | `$74.95` | −`$26.24` | `$7.95` | **`$56.66`** |
| Джинсы × 2 | `$149.90` | −`$52.48` | Free | **`$97.42`** |
| Джинсы × 2 + свитер × 1 | `$199.85` | −`$52.48` | Free | **`$147.37`** |
| После удаления свитера | `$149.90` | −`$52.48` | Free | **`$97.42`** |

Формулы **для наблюдавшихся состояний**, не универсальный бизнес-контракт:

- `74.95 − 26.24 + 7.95 = 56.66`
- `149.90 − 52.48 = 97.42`
- `199.85 − 52.48 = 147.37`

**Примечание:** на странице названия `Sub Total` и `Merchandise` относятся к конкретному интерфейсу; при платной доставке на снимке `Sub Total` включает Shipping. Не приравнивать термин автоматически к общепринятому «subtotal без доставки» и не утверждать формулу для других корзин, налоговых режимов и промоакций.

## 5. Ограничения и дальнейшие действия

- Повторно проверить исходные варианты `TC-AE-105` (A × 1 + B × 1) и `TC-AE-106` (удаление A), если требуется буквальное выполнение утверждённой версии тест-кейсов.
- Уточнить бизнес-правила применения скидок, расчёта Sub Total, shipping и taxes (`Q-AE-05`).
- При следующих прогонах фиксировать точное время, часовой пояс, регион и версию браузера.
- [RTM](../coverage/REQUIREMENTS_TRACEABILITY_MATRIX.md) отражает выполненные сценарии и сохраняет проектное покрытие без изменений.

---

*Независимое ручное тестирование публичного сайта American Eagle. Проект не связан с компанией American Eagle.*
