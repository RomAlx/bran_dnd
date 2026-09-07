# Бран «Трактирщик» Каплесбор

Mobile-first лендинг и шпаргалка к сессии D&D (Vue 3 + Vite).

**Сайт:** https://romalx.github.io/bran_dnd/

## Локально

```bash
npm install
npm run dev
```

Сборка:

```bash
npm run build
npm run preview
```

## GitHub Pages

Пуш в `main` собирает сайт и публикует его через [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml). Отдельной ветки `gh-pages` нет.

Один раз в репозитории:

1. **Settings → Pages**
2. Source: **GitHub Actions**

Не выбирай «Deploy from a branch». После первого зелёного workflow сайт будет на https://romalx.github.io/bran_dnd/
