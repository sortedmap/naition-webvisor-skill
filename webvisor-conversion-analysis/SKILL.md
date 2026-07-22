---
name: webvisor-conversion-analysis
description: >-
  Analyzes landing page Webvisor visit JSON for conversion drop-off hypotheses,
  produces full hypotheses.md report, proposes and implements landing fixes in
  site_dir respecting project instructions. Use with site_url, data_dir, and site_dir.
---

# Webvisor Conversion Analysis

Продуктовый анализ визитов лендинга по JSON Webvisor, отчёт и внедрение улучшений в код.

## Перед началом

1. Входы: `site_url`, `data_dir`, `site_dir`, `output_dir` (optional).
2. **`analysis.md`** — этапы 0–4.
3. **`hypothesis-format.md`** — гипотезы per-visit.
4. **`report-template.md`** — обязательная структура `hypotheses.md`.
5. **`implementation.md`** — этапы 4.5–7.

## Порядок работы

| Этап | Артефакт |
|------|----------|
| 0 — DOM + structural audit → карта | `landing-map.json` |
| 1 — воронка | hypotheses.md |
| 2 — группы + converted-профиль | hypotheses.md |
| 3 — все визиты, primary + secondary | `work/visits/*.json` |
| 4 — полный отчёт, рекомендации 2 слоя | `hypotheses.md` |
| 4.5 — discovery в site_dir | `site-constraints.md` |
| 5 — рекомендации + gate | `recommendations.md` |
| 6 — правки site_dir (сверху вниз) | изменённые файлы |
| 7 — проверка + workflow | `constraints-check.md` |

## Критические правила

### Анализ (0–4)

- **Этап 0:** DOM-аудит + `structuralAudit`; `observed` не пуст; без Y-сетки.
- **Converted:** разобрать каждый конвертированный визит.
- **Доминирующий кластер (>70%):** несколько рычагов, не только секция конверсии; secondary где есть накопление.
- **Этап 4:** `hypotheses.md` по **`report-template.md`**; рекомендации **два слоя** (топ-3 кластера + structural audit).
- Label — продуктовый язык; milestone-id только в `funnelStage`.
- Сверка N; все визиты в приложении.

### Внедрение (4.5–7)

- Без `site-constraints.md` правки запрещены.
- Ограничения — только из markdown в `{site_dir}`.
- **Внедрить:** approved из топ-3 **и** минимум один structural; порядок **сверху страницы вниз**.
- **Запрещено:** править только секцию конверсии, пропустив structural и малые кластеры.
- После правок: интерактив из карты работает; workflow из site_dir зафиксирован в `constraints-check.md`.

## Конверсия

Из `inputNodes` и submit в `formEvents` → `landing-map.conversionGoal`.

Подробности — `analysis.md`; шаблон — `report-template.md`; внедрение — `implementation.md`.
