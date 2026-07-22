# Анализ визитов Webvisor

Методология продуктового анализа лендинга по данным Webvisor: карта страницы, воронка, гипотезы отвала, рекомендации и внедрение улучшений в код.

## Состав репозитория

```
/
├── README.md
└── webvisor-conversion-analysis/
    ├── SKILL.md
    ├── analysis.md
    ├── hypothesis-format.md
    ├── report-template.md          ← обязательная структура hypotheses.md
    └── implementation.md
```

## Входы и выходы

| Вход | Описание |
|------|----------|
| `site_url` | URL лендинга (DOM-аудит на этапе 0) |
| `data_dir` | Папка с JSON-файлами визитов |
| `site_dir` | Код лендинга и инструкции (README, STUDENTS.md и т.д.) |
| `output_dir` | Куда сохранить результат |

| Выход | Этап |
|-------|------|
| `landing-map.json` | 1 |
| `work/visits/<visitId>.json` | 2 |
| `hypotheses.md` | 3 |
| `site-constraints.md` | 4 |
| `recommendations.md` | 5 |
| изменённые файлы в `site_dir` | 6 |
| `constraints-check.md` | 7 |

## Как запустить в Cursor

```
Проведи анализ и внедри улучшения по @webvisor-conversion-analysis/SKILL.md

site_url: https://example.com/
data_dir: @data/visits-2026-07-21
site_dir: .
output_dir: output
```
