# Aquarium Build Journal (RU/EN)

## RU: Подробный путь от пустого экрана к живому 3D-аквариуму

### 1) Старт и валидация ТЗ
- Взяли исходное задание из `AQUARIUM_TASK_SPECIFICATION.md` и проверили, какие требования обязательны: интерактив, камера, несколько рыб, живая процедурная анимация, ограничение границами аквариума.
- Сравнили раннюю реализацию с ТЗ и нашли расхождения.

### 2) Первый рабочий рендер
- Собрали сцену аквариума и окружения.
- Подключили управление камерой (орбита + зум).
- Включили непрерывный цикл анимации.

### 3) Переход к полностью автономной версии
- По требованию убрали внешние зависимости.
- Сделали standalone-файл на чистом Canvas 2D + собственной 3D-математике.
- Добавили процедурную проекцию, depth-сортировку и базовый пайплайн рендера.

### 4) Рыбы: геометрия, кинематика, поведение
- Добавили несколько уникальных рыб (цвет/размер/пропорции).
- Реализовали движение с физиологичным “волновым” телом и хвостом.
- Ввели steering-поведение:
  - wander;
  - center pull;
  - boundary avoidance;
  - separation / alignment / cohesion.
- Доработали повороты и banking, чтобы рыба смотрела по вектору скорости.

### 5) “Рыбки плывут хвостом назад” - исправлено
- Перевернули анатомическую привязку:
  - хвост на заднюю часть;
  - голова и глаза на переднюю;
  - грудные плавники ближе к передней трети.

### 6) Переход от плоских тел к объемным
- Заменили плоский силуэт на сегментированное объемное тело.
- Разделили поверхность на верх/бока/низ с разной светотенью.
- Добавили контурные и спекулярные акценты для “живой” формы.

### 7) Исправление ориентации верхнего плавника
- Исправили геометрию спинного плавника, чтобы он выходил наружу из объема тела, а не “проваливался” внутрь.

### 8) Исправление хвоста
- Перестроили хвост так, чтобы он примыкал к телу вершиной (углом), а не целой гранью.
- Сохранили динамику взмаха.

### 9) Оптимизация производительности и объема кода
- Создали `interactive-3d-aquarium-standalone-optimized.html`.
- Сократили код и уменьшили аллокации в кадре.
- Исправили баг “прозрачных тел” (проблема с переиспользованием буфера при отложенной отрисовке).

### 10) Жесткие физические ограничения
- Добавили safety radius на каждую рыбу.
- Гарантировали непересечение границ аквариума для тела, хвоста и плавников.
- Добавили пост-итерационную коррекцию пересечений между рыбами (resolve overlaps).

### 11) Биологический ритм
- Сделали индивидуальные частоты:
  - крупные рыбы двигают хвостом и плавниками реже;
  - мелкие - чаще.
- Убрали синхронность через персональные фазы для каждой рыбы.

### 12) Документация и публикация
- Добавили подробные двуязычные комментарии в optimized-файл.
- Создали двуязычный `README.md`.
- Инициализировали Git, опубликовали публичный репозиторий, затем зачистили состав файлов на GitHub до нужного минимума.

### 13) Небольшая дружеская правда жизни
- Ты как “мешок с костями” оказался surprisingly точным QA-инструментом: каждый микродефект замечался быстрее, чем успевал остыть мой синус в хвостовом шейдинге.
- Поэтому итог и получился настолько вылизанным.

---

## EN: Full journey from blank screen to volumetric 3D fish

### 1) Kickoff and spec validation
- Parsed `AQUARIUM_TASK_SPECIFICATION.md` and extracted mandatory requirements: interaction, camera controls, multiple fish, procedural animation, strict aquarium bounds.
- Compared the early implementation against the spec and identified gaps.

### 2) First functional render
- Built aquarium scene and environment.
- Added orbit camera controls (drag + wheel zoom).
- Enabled continuous animation loop.

### 3) Migration to fully standalone mode
- Removed external dependencies as requested.
- Implemented a standalone file using pure Canvas 2D and custom 3D math.
- Added projection pipeline, depth sorting, and render scheduling.

### 4) Fish geometry, kinematics, and behavior
- Created multiple fish variants (color/size/proportions).
- Implemented body/tail undulation driven by procedural math.
- Added steering behavior:
  - wander;
  - center pull;
  - boundary avoidance;
  - separation / alignment / cohesion.
- Improved orientation and banking so fish face their velocity vector naturally.

### 5) “Fish are swimming tail-first” - fixed
- Corrected anatomical placement:
  - tail to rear;
  - head and eyes to front;
  - pectoral fins shifted toward front section.

### 6) Flat bodies -> volumetric fish
- Replaced flat silhouette with segmented volumetric body.
- Split rendering into top/sides/bottom with differentiated shading.
- Added contour/specular accents for better 3D perception.

### 7) Dorsal fin orientation fix
- Corrected dorsal fin construction so it protrudes outward from the body volume instead of folding inward.

### 8) Tail attachment fix
- Rebuilt tail to connect with a vertex (angle) to the body, not with a full edge.
- Preserved dynamic flapping.

### 9) Performance and code-size optimization
- Created `interactive-3d-aquarium-standalone-optimized.html`.
- Reduced code size and per-frame allocations.
- Fixed “transparent fish body” artifact (deferred rendering buffer reuse issue).

### 10) Hard spatial constraints
- Added per-fish safety radius.
- Guaranteed that body/fins/tail stay inside aquarium boundaries.
- Added iterative anti-overlap correction between fish.

### 11) Biological rhythm realism
- Added individualized cadence:
  - larger fish flap tails/fins less often;
  - smaller fish flap more often.
- Removed synchronization by introducing per-fish phase offsets.

### 12) Documentation and publishing
- Added detailed bilingual comments in optimized source.
- Created bilingual `README.md`.
- Initialized Git, published repository, then cleaned GitHub file set to the required minimal set.

### 13) Friendly final note
- You jokingly called yourself a “bag of bones,” but your feedback precision was elite QA level.
- That iterative feedback loop is exactly why the final aquarium feels polished and alive.

---

## Final Output Reference

Primary production file:
- `interactive-3d-aquarium-standalone-optimized.html`
