# AI-project_FAOSTAT-Macro-Indicators
Interactive dashboard for FAOSTAT Macro Indicators and Capital Stock — AFF economy (Agriculture, forestry &amp; fishing), investment and country profiles

**FAO** (*Food and Agriculture Organization* — Продовольственная и сельскохозяйственная организация ООН) <br> 
**FAOSTAT** (*FAO Statistics* — статистика ФАО).<br>

<div id="header" align="center">
<img src="https://cdn1.tenchat.ru/static/vbc-gostinder/2025-05-19/f3d592c4-6f18-4095-8b73-f6d89e8c3f58.png?width=1004&height=525&fmt=webp" title="Cursor" width="133" height="70"/>&nbsp;
</div>
<br>




Сфокусированный HTML-дашборд по двум доменам FAOSTAT:

- **Macro Indicators / MK** (*Macro Indicators* — макроиндикаторы) — **GDP** (*Gross Domestic Product* — ВВП, валовой внутренний продукт), добавленная стоимость, рост и доли секторов
- **Capital Stock / CS** (*Capital Stock* — запас капитала) — инвестиции AFF (**GFCF**, *Gross Fixed Capital Formation* — валовое накопление основного капитала), чистый запас капитала (**NCS**, *Net Capital Stock*), **AOI** (*Agriculture Orientation Index* — индекс ориентации сельского хозяйства) и **AIR** (*Agriculture Investment Ratio* — интенсивность инвестиций: GFCF AFF / VA AFF)

Сюжет — **Сельское хозяйство, лес и рыба (AFF - Agriculture, forestry & fishing)** на фоне всей экономики, а не полный браузер FAOSTAT.

Интерактивный дашборд --> [FAOSTAT-Macro-Indicators](https://elenatratsevskaya.github.io/AI-project_FAOSTAT-Macro-Indicators/FAOSTAT_Macro_Indicators.html) <br><br>

## Источник

Данные из официальных нормализованных выгрузок FAOSTAT:

| Домен | Типичный файл FAOSTAT |
|--------|----------------------|
| Macro Indicators (макроиндикаторы) | `Macro-Statistics_Key_Indicators_E_All_Data_(Normalized).csv` |
| Capital Stock (запас капитала) | `Investment_CapitalStock_E_All_Data_(Normalized).csv` |

 --> [Источник данных](https://www.fao.org/faostat/en/) <br><br>

Денежные ряды — в **постоянных долларах США 2015** (*real USD* / *Value US$, 2015 prices* — постоянные доллары США в ценах 2015). Этот базовый год — как опубликованы серии MK/CS в используемой выгрузке, а не своя переоценка.

**Не путать** **USD 2015** (*United States dollar* — доллар США, постоянные цены 2015) как единицу измерения с фильтром **vs 2015** (дельта: выбранный год минус 2015).

### Годы в данных и фильтре

В данных:

- Macro Indicators (`yearsMk`) — до **2024**
- Capital Stock (`yearsCs`) — до **2023**
- Общий слайдер берёт пересечение (`yearsJoint`) → максимум **2023** (диапазон фильтра **1995–2023**)

**2022** выбран стартовым, потому что по Capital за 2023 много *forecast*-флагов (прогнозных оценок).

## Структура дашборда

Одностраничное приложение: [`dashboard/FAOSTAT_Macro_Indicators.html`](dashboard/FAOSTAT_Macro_Indicators.html)

| Лист | Фокус |
|-------|--------|
| **Overview** (обзор) | Объёмы экономики и капитал — карта, **KPI** (*Key Performance Indicators* — ключевые показатели), топы, структура и тренды |
| **Macro** (макро) | Рост и структура AFF (*Agriculture, Forestry and Fishing* — сельское хозяйство, лес и рыба) |
| **Capital** (капитал) | Инвестиции и капитал AFF: **GFCF** (*Gross Fixed Capital Formation* — валовое накопление основного капитала), **NCS** (*Net Capital Stock* — чистый запас капитала), **AOI** (*Agriculture Orientation Index* — индекс ориентации сельского хозяйства), **AIR** (*Agriculture Investment Ratio* — интенсивность инвестиций) |
| **Country** (страна) | Профиль одной страны vs *peer* (группа сравнения) и мир (ранг, тренд, радар) |
| **Glossary** (глоссарий) | Термины и методология (**EN** / **RU** — английский / русский) |

Общие фильтры (где применимо): год, режим территории (страны / *geo-regions* — георегионы), *peer*-группа (группа сравнения), показатель карты, режим **Δ** (дельта: **YoY**, *Year over Year* — к предыдущему году, или vs 2015).

### География (упрощённо)

- **Страны** — основной режим карты и рейтингов  
- **Geo-regions** (*geographic regions* — георегионы) — Africa, Americas, Asia, Europe, Oceania  
- **Peer** (группа сравнения) — All / **LDC** (*Least Developed Countries* — наименее развитые страны) / **SIDS** (*Small Island Developing States* — малые островные развивающиеся государства) / **EU-27** (*European Union* — Европейский союз, 27 стран) (и связанные срезы в сборке)  
- **World** (мир) — мировой агрегат FAOSTAT для сравнительных графиков  

## Индикаторы (сфокусированный набор)

Типичные представления:

- **GDP** (*Gross Domestic Product* — ВВП) и GDP на душу населения (USD 2015 — постоянные доллары США 2015)
- **VA AFF** (*Value Added* — валовая добавленная стоимость AFF), доля AFF в GDP, рост AFF (**% 2015** — рост в постоянных ценах 2015)
- Доля **Manufacturing** (обрабатывающая промышленность) — контекст структуры
- **GFCF AFF** (*Gross Fixed Capital Formation* — валовое накопление основного капитала в AFF), **Net Capital Stock AFF** / **NCS** (*Net Capital Stock* — чистый запас капитала AFF)
- **AOI** (*Agriculture Orientation Index* — индекс ориентации сельского хозяйства; ориентир ≈ 1)
- **AIR** (*Agriculture Investment Ratio* — интенсивность инвестиций: GFCF AFF / VA AFF, %)
- **GFCF AFF / GFCF** (%) — доля аграрных инвестиций в общем валовом накоплении основного капитала

Остальное из тех же **CSV** (*Comma-Separated Values* — таблицы с разделителями-запятыми) в **UI** (*User Interface* — интерфейс) не выводится.

## Как собирается дашборд

```
FAOSTAT CSV (MK + CS)
        │
        ▼
build_overview_data.py   ← фильтр items/elements, годы ≥ 1995 (пересечение MK∩CS)
        │
        ▼
dashboard/data/overview-data.js   (+ overview.json)
        │
        ▼
FAOSTAT_Macro_Indicators.html
  Chart.js · Leaflet · TopoJSON
```

1. Положите нормализованные папки CSV MK (*Macro Indicators* — макроиндикаторы) и CS (*Capital Stock* — запас капитала) рядом с корнем проекта (пути ожидает `build_overview_data.py`).
2. Пересоберите срезы:

```bash
python dashboard/build_overview_data.py
```

3. Откройте `dashboard/FAOSTAT_Macro_Indicators.html` в браузере (или отдайте папку `dashboard/` локальным сервером).

Браузер не загружает сырые таблицы FAOSTAT. Он читает заранее нарезанный **JSON** (*JavaScript Object Notation* — текстовый формат данных) / JS для карт, трендов и таблиц.

## Упрощения относительно полного FAOSTAT

Дашборд — **узкая витрина**, а не зеркало всей базы.

1. **Одна ценовая линейка** — только постоянные USD 2015 (*United States dollar* — доллар США в ценах 2015; без локальной валюты и без *current USD* / текущих долларов как основной).
2. **Узкий набор индикаторов** — только AFF (*Agriculture, Forestry and Fishing* — сельское хозяйство, лес и рыба) и ключевые macro/investment метрики (макро / инвестиции).
3. **Простая география** — страны, пять *geo-regions* (георегионы), несколько *peer*-групп (группы сравнения), World (мир) — не все агрегаты FAOSTAT.
4. **Предсборка данных** — компактные срезы вместо фильтрации полных CSV в браузере.
5. **Без UI флагов качества** (*User Interface* — интерфейс) — флаги CS (*Capital Stock*) есть в исходниках, но лист Quality (качество) не показывается.
6. **Побочные эффекты UI** — Δ (дельта) только как **YoY** (*Year over Year* — к предыдущему году) или vs 2015; один показатель карты задаёт цвет/сортировку карты, топа и таблицы; Peer = All на части графиков близок к World.

## Стек

- Статический **HTML** (*HyperText Markup Language* — язык разметки страниц) / **CSS** (*Cascading Style Sheets* — таблицы стилей) / **JavaScript** (язык сценариев браузера)
- [Chart.js](https://www.chartjs.org/) — графики
- [Leaflet](https://leafletjs.com/) + **TopoJSON** (*Topology JSON* — топологический формат геоданных) — карта
- Python + pandas — сборка данных (`build_overview_data.py`)

## Лицензия / атрибуция

Определения и значения индикаторов принадлежат **FAO** (*Food and Agriculture Organization* — Продовольственная и сельскохозяйственная организация ООН) / **FAOSTAT** (*FAO Statistics* — статистика ФАО). При переиспользовании цифр указывайте FAOSTAT. Этот репозиторий — слой визуализации над выбранной выгрузкой.


<img width="1601" height="900" alt="41" src="https://github.com/user-attachments/assets/7f9c3081-4383-4e02-b8b6-e66bf3892750" />

<img width="1597" height="902" alt="42" src="https://github.com/user-attachments/assets/9f4d35bd-885d-42b6-a417-1dc1944be478" />

<img width="1600" height="898" alt="44" src="https://github.com/user-attachments/assets/61865756-3605-4a83-98c1-cacb1b67e219" />

<img width="1601" height="901" alt="45" src="https://github.com/user-attachments/assets/9859154e-7954-43ef-8326-3108083b8cba" />

<img width="1594" height="901" alt="46" src="https://github.com/user-attachments/assets/430261f8-22be-4e43-8300-717ad9b3e229" />

<img width="1597" height="901" alt="47" src="https://github.com/user-attachments/assets/f2bbc438-81fa-409f-8134-c84ce0523992" />

<img width="1599" height="902" alt="48" src="https://github.com/user-attachments/assets/f10100cf-dc7d-4045-9759-fc914b5a2a92" />

<img width="1599" height="902" alt="49" src="https://github.com/user-attachments/assets/fad120b7-3c26-449c-b73b-89a4de5b1b9c" />

<img width="1600" height="900" alt="50" src="https://github.com/user-attachments/assets/2e2fba3b-b42d-4341-8412-88a5c2372323" />

---

*Не является официальным ПО FAO (ФАО).*
