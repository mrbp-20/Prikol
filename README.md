# Interactive 3D Aquarium (Standalone, No Dependencies)

RU | EN

## RU: Описание проекта

Это автономный интерактивный 3D-аквариум, реализованный в одном HTML-файле без внешних библиотек и CDN.  
Сцена рендерится через `Canvas 2D` и собственную математику 3D-проекции.

### Основные возможности

- Полностью standalone: никаких зависимостей, сборщиков и пакетов.
- Орбит-камера: вращение мышью, зум колесом.
- Процедурные рыбы с объемным телом, плавниками и хвостом.
- Живое поведение рыб:
  - блуждание и плавное руление;
  - избегание стенок аквариума;
  - анти-пересечения между рыбами;
  - индивидуальный ритм движений (без синхрона);
  - крупные рыбы двигают хвостом/плавниками реже, чем мелкие.
- Подводные эффекты: каустики, псевдо-рефракция, пузырьки, растения.

### Структура файлов

- `interactive-3d-aquarium-standalone-optimized.html` — оптимизированная standalone-версия (рекомендуется).
- `AQUARIUM_TASK_SPECIFICATION.md` — исходное ТЗ в формате Markdown.
- `AQUARIUM_BUILD_JOURNAL_RU_EN.md` — подробный двуязычный журнал разработки.

### История проекта

- [ТЗ, по которому строился аквариум](./AQUARIUM_TASK_SPECIFICATION.md)
- [Подробный журнал сборки (RU/EN)](./AQUARIUM_BUILD_JOURNAL_RU_EN.md)

### Быстрый запуск (Windows / PowerShell)

Откройте файл напрямую в браузере:

- `interactive-3d-aquarium-standalone-optimized.html`

Или поднимите локальный сервер (рекомендуется):

```powershell
python -m http.server 8080
```

Затем откройте:

- [http://localhost:8080/interactive-3d-aquarium-standalone-optimized.html](http://localhost:8080/interactive-3d-aquarium-standalone-optimized.html)

### Публикация на веб-сервере

Достаточно скопировать `interactive-3d-aquarium-standalone-optimized.html` на любой статический хостинг:

- GitHub Pages
- Netlify
- Vercel
- Nginx/Apache static host

### Безопасность

- Нет `eval`, `Function` и динамической загрузки скриптов.
- Нет обработки пользовательского ввода в HTML/JS-код.
- Нет внешних API-запросов и передачи данных.
- Нет cookies/localStorage для логики приложения.

---

## EN: Project Description

This is a fully standalone interactive 3D aquarium implemented in a single HTML file with no external libraries and no CDN.  
Rendering is done with `Canvas 2D` and custom 3D projection math.

### Key Features

- Fully standalone: no dependencies, bundlers, or packages.
- Orbit camera: mouse drag to rotate, mouse wheel to zoom.
- Procedural fish with volumetric body, fins, and tail.
- Lifelike fish behavior:
  - wandering and smooth steering;
  - aquarium boundary avoidance;
  - anti-overlap fish solver;
  - individual movement rhythm (not synchronized);
  - larger fish move tails/fins less frequently than smaller fish.
- Underwater effects: caustics, pseudo-refraction, bubbles, plants.

### File Structure

- `interactive-3d-aquarium-standalone-optimized.html` — optimized standalone version (recommended).
- `AQUARIUM_TASK_SPECIFICATION.md` — original task specification in Markdown.
- `AQUARIUM_BUILD_JOURNAL_RU_EN.md` — detailed bilingual build journal.

### Project History

- [Task specification used to build the aquarium](./AQUARIUM_TASK_SPECIFICATION.md)
- [Detailed build journal (RU/EN)](./AQUARIUM_BUILD_JOURNAL_RU_EN.md)

### Quick Start (Windows / PowerShell)

Open directly in browser:

- `interactive-3d-aquarium-standalone-optimized.html`

Or run a local static server (recommended):

```powershell
python -m http.server 8080
```

Then open:

- [http://localhost:8080/interactive-3d-aquarium-standalone-optimized.html](http://localhost:8080/interactive-3d-aquarium-standalone-optimized.html)

### Deployment

Upload `interactive-3d-aquarium-standalone-optimized.html` to any static hosting:

- GitHub Pages
- Netlify
- Vercel
- Nginx/Apache static host

### Security Notes

- No `eval`, no `Function`, no dynamic script injection.
- No untrusted input parsing/execution.
- No external API requests.
- No cookies/localStorage required for core logic.

---

## License

Open-source friendly.  
If you publish a fork, keep attribution in source comments and README.

## Author

Nikolai (Codex AI), 2026
