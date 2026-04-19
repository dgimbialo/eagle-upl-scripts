# Pin Usage Analyzer — EAGLE ULP Script

<img width="1662" height="1281" alt="Screenshot " src="https://github.com/user-attachments/assets/99d8241c-d642-4b79-a9c7-a7a4b6e291f3" />

## Overview

**Pin Usage Analyzer** is a User Language Program (ULP) for Autodesk EAGLE / Fusion 360 Electronics.  
It analyzes pin connections of any schematic component and displays them in a color-coded interactive table.

## Purpose

When working with complex schematics — especially large ICs like MCUs, FPGAs, or memory chips — it is often difficult to quickly see which pins are connected, where they go, and which pins remain unconnected (N/C). This script solves that problem by providing a clear, filterable, sortable view of all pin connections for any selected component.

## How to Run

1. Open a schematic (`.sch`) in EAGLE or Fusion 360 Electronics.
2. In the command line at the bottom of the editor, type:
   ```
   RUN "path/to/pin-usage-analyzer.ulp"
   ```
   Or use the menu: **File → Execute ULP** and select the file.

## User Interface

### Controls

| Control | Description |
|---------|-------------|
| **Source** | Select the component whose pins you want to analyze |
| **Target component** | Optionally filter connections to a specific component only |
| **Analyze** | Run the analysis and populate the table |
| **Reset** | Clear all filters and sorting back to defaults |
| **Filter** (text) | Live text filter across all columns |
| **Status** | Filter by connection status: All / Connected / Free (N/C) |
| **Sort** | Sort by any column in ascending or descending order |
| **Apply** | Apply the current filter and sort settings |
| **Export** | Save the table to a file |
| **Close** | Close the dialog |

### Table Columns

| Column | Description |
|--------|-------------|
| **Component Name** | Name and value of the source component |
| **Pin Name** | Logical pin name (e.g. `PA0`, `VCC`) |
| **Pin #** | Physical pad number on the component |
| *(spacer)* | Visual separator |
| **Net** | Schematic net name the pin is connected to; highlighted green (N/C) or yellow (connected) |
| *(spacer)* | Visual separator |
| **Target Pin #** | Physical pad number on the target component |
| **Target Pin Name** | Logical pin name on the target component |
| **Target Component** | Name and value of the connected component |

### Color Coding

| Color | Meaning |
|-------|---------|
| 🟩 Green (`#88DD88`) | Pin is **not connected** (N/C) |
| 🟨 Yellow (`#FFEE77`) | Pin is **connected** to a net |
| ⬜ Gray (`#C0C0C0`) | Table header row |

### Export

Supported formats:
- **CSV** (`;` separated) — for spreadsheet applications (Excel, LibreOffice Calc)
- **Text** (tab separated) — for plain text editors
- **HTML** — full colored table, identical to what is shown in the dialog

The export filename is **automatically generated** based on the selected components:
- Source only: `IC1_STM32H743IIT6.csv`
- Source + Target: `IC1_STM32H743IIT6_to_IC2_W9825G6KH-6.csv`

The dialog remembers the last used export directory within the session.

## Requirements

- Autodesk EAGLE 7.x or later, or Fusion 360 Electronics
- Must be run from the **schematic editor** (not board editor)

---

---

# Pin Usage Analyzer — EAGLE ULP Скрипт

## Опис

**Pin Usage Analyzer** — це User Language Program (ULP) для Autodesk EAGLE / Fusion 360 Electronics.  
Скрипт аналізує з'єднання пінів будь-якого компонента схеми і відображає їх у кольоровій інтерактивній таблиці.

## Призначення

При роботі зі складними схемами — особливо з великими ІС типу мікроконтролерів, FPGA або чипів пам'яті — важко швидко побачити, які піни підключені, куди вони ведуть і які залишились незадіяними (N/C). Цей скрипт вирішує цю проблему, надаючи зручний перегляд всіх з'єднань пінів з можливістю фільтрації та сортування.

## Як запустити

1. Відкрийте схему (`.sch`) в EAGLE або Fusion 360 Electronics.
2. В командному рядку внизу редактора введіть:
   ```
   RUN "шлях/до/pin-usage-analyzer.ulp"
   ```
   Або через меню: **File → Execute ULP** і виберіть файл.

## Інтерфейс

### Елементи керування

| Елемент | Опис |
|---------|------|
| **Source** | Вибір компонента, піни якого аналізуються |
| **Target component** | Фільтрація з'єднань до конкретного компонента |
| **Analyze** | Запуск аналізу і заповнення таблиці |
| **Reset** | Скидання всіх фільтрів і сортування до початкових значень |
| **Filter** (текст) | Текстовий фільтр по всіх колонках |
| **Status** | Фільтр за статусом: All / Connected / Free (N/C) |
| **Sort** | Сортування за будь-якою колонкою у зростаючому або спадаючому порядку |
| **Apply** | Застосувати поточні налаштування фільтра і сортування |
| **Export** | Зберегти таблицю у файл |
| **Close** | Закрити діалог |

### Колонки таблиці

| Колонка | Опис |
|---------|------|
| **Component Name** | Назва та значення вихідного компонента |
| **Pin Name** | Логічна назва піна (наприклад `PA0`, `VCC`) |
| **Pin #** | Фізичний номер паду компонента |
| *(роздільник)* | Візуальний відступ |
| **Net** | Назва мережі схеми; виділяється зеленим (N/C) або жовтим (підключено) |
| *(роздільник)* | Візуальний відступ |
| **Target Pin #** | Фізичний номер паду на цільовому компоненті |
| **Target Pin Name** | Логічна назва піна на цільовому компоненті |
| **Target Component** | Назва та значення підключеного компонента |

### Кольорова схема

| Колір | Значення |
|-------|---------|
| 🟩 Зелений (`#88DD88`) | Пін **не підключений** (N/C) |
| 🟨 Жовтий (`#FFEE77`) | Пін **підключений** до мережі |
| ⬜ Сірий (`#C0C0C0`) | Рядок заголовка таблиці |

### Експорт

Підтримувані формати:
- **CSV** (роздільник `;`) — для табличних редакторів (Excel, LibreOffice Calc)
- **Text** (роздільник Tab) — для текстових редакторів
- **HTML** — повна кольорова таблиця, ідентична тій що відображається в діалозі

Ім'я файлу **генерується автоматично** на основі вибраних компонентів:
- Тільки Source: `IC1_STM32H743IIT6.csv`
- Source + Target: `IC1_STM32H743IIT6_to_IC2_W9825G6KH-6.csv`

Діалог запам'ятовує останню використану директорію протягом сесії.

## Вимоги

- Autodesk EAGLE 7.x або новіший, або Fusion 360 Electronics
- Запускати тільки з **редактора схем** (не з редактора плати)
