# Product Details — Manual Execution Log (American Eagle)

| Поле | Значение |
|---|---|
| Document ID | `EXLOG-AE-PRODUCT-001` |
| Версия | `1.0` |
| Дата ручной проверки | `2026-10-14` |
| Автор | Ilya Sidorychev |
| SUT | [American Eagle — US storefront](https://www.ae.com/us/en) |
| Test Cases | [Product Details Test Cases](../test-cases/PRODUCT_DETAILS_TEST_CASES.md) |
| Requirements | [Requirements & Assumptions](../requirements/REQUIREMENTS_AND_ASSUMPTIONS.md) |
| Checklist | [Product Details Checklist](../checklists/PRODUCT_DETAILS_CHECKLIST.md) |
| Источник результатов | Скриншоты и описание выполненных действий |

> **Область отчёта.** Зафиксированы четыре ручных сценария Product Details. Результат `Passed` относится к выполненным основным шагам; дополнительные условные проверки (в частности, sold-out SKU и переключение цвета при выбранном размере) не выполнялись полностью. Точное время отдельных действий не фиксировалось.

## 1. Тестовое окружение

| Параметр | Значение |
|---|---|
| Дата | 2026-10-14 |
| Время отдельных действий | Не зафиксировано |
| ОС | Windows 10 Pro, 22H2, build 19045.6456, x64 |
| Браузер | Google Chrome 155.0.8059.80 (64-bit) |
| Storefront | US / English (`/us/en`) |
| VPN exit region | USA |
| Сессия | Guest (без авторизации) |
| Ограничения | Production, штатный UI; реальные заказы не оформлялись |

## 2. Сводка выполнения

| Run ID | Test Case | Сценарий | Статус | Evidence |
|---|---|---|---|---|
| `RUN-AE-PD-20261014-01` | `TC-AE-401` | Карточка товара и основные данные | **Passed** | [Обзор](../screenshots/product-details/TC-AE-401_product_overview.png), [список размеров](../screenshots/product-details/TC-AE-401_size_options.png) |
| `RUN-AE-PD-20261014-02` | `TC-AE-402` | Переключение размеров | **Passed** | [Regular](../screenshots/product-details/TC-AE-402_size_regular.png), [Long](../screenshots/product-details/TC-AE-402_size_long.png) |
| `RUN-AE-PD-20261014-03` | `TC-AE-403` | Add to Bag и обязательный размер | **Passed** | [Открыт список размера](../screenshots/product-details/TC-AE-403_size_required.png), [подтверждение](../screenshots/product-details/TC-AE-403_added_to_bag.png) |
| `RUN-AE-PD-20261014-04` | `TC-AE-404` | Проверка товара в корзине | **Passed** | [Shopping Bag](../screenshots/product-details/TC-AE-404_bag_item.png) |

**Итог:** 4 executed · 4 passed · 0 failed · 0 blocked · 0 confirmed defects. Частичное покрытие условных ветвей указано ниже и не означает их успешного прохождения.

## 3. RUN-AE-PD-20261014-01 — TC-AE-401

- **Название:** Открытие карточки товара и отображение основных данных
- **Requirements:** `REQ-AE-011`, `REQ-AE-012`
- **Checklist:** `CL-PD-001`–`CL-PD-009`
- **Priority:** High
- **Товар:** `AE Lowest-Rise Baggy Wide-Leg Jean`
- **Status:** **Passed**

| № | Действие | Expected Result (гипотеза) | Actual Result |
|---|---|---|---|
| 1 | Открыть страницу выбранного товара | Отображается PDP выбранного товара | Открылась PDP `AE Lowest-Rise Baggy Wide-Leg Jean` |
| 2 | Проверить название, фотографии и цены | Основная информация присутствует | Видны название, фотографии спереди/сзади, цена `$45.46`, перечёркнутая `$69.95` и обозначение скидки `35%` |
| 3 | Проверить цветовые варианты | Варианты отображаются | Выбран цвет `Medium Tinted Indigo`; представлены другие варианты |
| 4 | Открыть список размеров | Видны размеры и состояния вариантов | Список открылся: `000 Short`, `000 Regular`, `000 Long`; `00 X-Short` показан зачёркнутым |
| 5 | Проверить Add to Bag | Кнопка присутствует | Кнопка `Add to Bag` видна |

**Actual Result:** основные элементы PDP доступны. Обновление набора фотографий при переключении галереи отдельно не проверялось; сравнение цены с исходной карточкой каталога не протоколировалось.

**Evidence:** [Обзор PDP](../screenshots/product-details/TC-AE-401_product_overview.png), [Size](../screenshots/product-details/TC-AE-401_size_options.png).

**Defect:** None.

**Remarks:** сведения о цене относятся к выбранному на этом снимке цвету и времени наблюдения.

## 4. RUN-AE-PD-20261014-02 — TC-AE-402

- **Название:** Выбор размера и переключение между доступными вариантами
- **Requirement:** `REQ-AE-013`
- **Checklist:** `CL-PD-010`–`CL-PD-013`
- **Priority:** High
- **Цвет:** `Light Vintage`
- **Status:** **Passed**

| № | Действие | Expected Result (гипотеза) | Actual Result |
|---|---|---|---|
| 1 | Выбрать `000 Regular` | Выбор отображается в поле Size | Отображается `000 Regular` |
| 2 | Повторно выбрать другой доступный размер | Поле отражает новый выбор | Отображается `000 Long` вместо `000 Regular` |
| 3 | Проверить сохранение контекста | Остальные данные PDP не подменены | Название товара и цвет `Light Vintage` не изменились; цена `$48.71` на обоих скриншотах |

**Actual Result:** переключение `000 Regular` → `000 Long` выполнено; актуальный размер ясно виден.

**Evidence:** [Regular](../screenshots/product-details/TC-AE-402_size_regular.png), [Long](../screenshots/product-details/TC-AE-402_size_long.png).

**Defect:** None.

**Remarks:** поведение размера при смене цвета (условный шаг исходного тест-кейса) не исследовалось; отдельное покрытие этой комбинации остаётся открытым.

## 5. RUN-AE-PD-20261014-03 — TC-AE-403

- **Название:** Состояние Add to Bag при выбранном и невыбранном варианте
- **Requirement:** `REQ-AE-014`
- **Checklist:** `CL-PD-014`–`CL-PD-017`
- **Priority:** High
- **Цвет:** `Light Vintage`
- **Status:** **Passed**

| № | Действие | Expected Result (гипотеза) | Actual Result |
|---|---|---|---|
| 1 | Попробовать Add to Bag без размера | UI запрашивает обязательный вариант либо показывает штатное ограничение | Открылся список размеров; товар не подтверждён как добавленный на этом шаге |
| 2 | Выбрать `000 Regular` | Выбранный размер отображается | В поле Size отображается `000 Regular` |
| 3 | Нажать Add to Bag | Отображается подтверждение добавления | Открылась панель `Added to bag!` |
| 4 | Проверить данные подтверждения | Отображается выбранная позиция | Товар `AE Lowest-Rise Baggy Wide-Leg Jean`, цвет `Light Vintage`, размер `000 Regular`, Qty `1`, цена `$48.71` |

**Actual Result:** без выбранного размера интерфейс предложил выбрать вариант; после выбора `000 Regular` появился штатный экран подтверждения.

**Evidence:** [Выбор размера](../screenshots/product-details/TC-AE-403_size_required.png), [Added to bag](../screenshots/product-details/TC-AE-403_added_to_bag.png).

**Defect:** None.

**Remarks:** попытка Add to Bag без размера описана по последовательности действий; один кадр открытого списка сам по себе не подтверждает причину открытия. Отдельная проверка недоступного SKU не выполнялась.

## 6. RUN-AE-PD-20261014-04 — TC-AE-404

- **Название:** Сохранение характеристик выбранного товара в корзине
- **Requirements:** `REQ-AE-015`, `REQ-AE-016`
- **Checklist:** `CL-PD-018`–`CL-PD-022`
- **Priority:** Critical
- **Status:** **Passed**

| № | Действие | Expected Result (гипотеза) | Actual Result |
|---|---|---|---|
| 1 | Открыть Shopping Bag после добавления | Корзина отображает выбранный товар | Отображается `AE Lowest-Rise Baggy Wide-Leg Jean` |
| 2 | Сверить варианты | Цвет и размер совпадают с PDP | `Light Vintage`, `000 Regular` |
| 3 | Проверить количество | Отображается добавленное количество | `Qty: 1`, в корзине одна позиция после удаления других ранее присутствовавших товаров |
| 4 | Сверить цену | Отображаемая цена соответствует PDP с учётом скидки | `$48.71`; перечёркнутая первоначальная цена `$74.95` |

**Actual Result:** название, выбранные цвет и размер, количество и текущая цена соответствуют подтверждённой добавленной позиции.

**Evidence:** [Корзина с товаром](../screenshots/product-details/TC-AE-404_bag_item.png), [подтверждение добавления](../screenshots/product-details/TC-AE-403_added_to_bag.png).

**Defect:** None.

**Remarks:** перед проверкой пользователь удалил другие позиции из своей корзины. На снимке видно `Merchandise $74.95` и `Savings -$26.24`; доставка `$7.95` показана отдельно. Расчёт итоговой суммы заказа этим тестом не проверялся.

## 7. Следующие действия

1. Провести отдельные проверки недоступного размера и переключения цвета в рамках дополнительного Product Details покрытия.
2. Проверить `TC-AE-101`–`TC-AE-106` для Shopping Bag, отдельно записывая расчёт скидок и корзину до/после действия.
3. При новых прогонах фиксировать точное время и часовой пояс.
4. Обновить [RTM](../coverage/REQUIREMENTS_TRACEABILITY_MATRIX.md) и [Test Summary](PRODUCT_DETAILS_TEST_SUMMARY_REPORT.md).

---

*Независимый учебный QA-проект. Фактические результаты ограничены описанными действиями и снимками экрана.*
