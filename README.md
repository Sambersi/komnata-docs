# Документация komnata — учебный проект

Практическая работа «Docs as Code: документация в репозитории».

| Папка или файл | Что это |
|---|---|
| `docs/` | Исходные страницы документации в Markdown |
| `mkdocs.yml` | Конфигурация генератора MkDocs: название, меню, тема |
| `product/` | Источник истины о продукте: вывод `--help` и конфигурация по умолчанию |
| `CHANGELOG.md` | Журнал изменений продукта |
| `styles/`, `.vale.ini` | Правила линтера прозы Vale |
| `.github/workflows/docs.yml` | Конвейер: сборка, проверки, публикация |
| `.github/pull_request_template.md` | Шаблон описания пул-реквеста |
| `compare/` | Папка для задания 5 |
| `REPORT.md` | Ваш отчёт по работе |

## Сборка на своём компьютере (необязательно)

```bash
python -m venv .venv
# Windows: .venv\Scripts\activate    macOS, Linux: source .venv/bin/activate
pip install -r requirements.txt
mkdocs serve          # сайт откроется по адресу http://127.0.0.1:8000
```


## Результат лабораторной

- [Опубликованный сайт](https://sambersi.github.io/komnata-docs/).
- [Подробный отчёт по каждому шагу](REPORT.md).
- [Порядок показа и ответы на защите](DEFENSE.md).
- [Самопроверка и ограничение взаимного ревью](SELF_REVIEW.md).

## Локальная проверка перед отправкой

Установите зависимости из requirements.txt и Vale 3.24.0, затем выполните:

```bash
git config core.hooksPath .githooks
```

По умолчанию hook использует команды python и vale из PATH.
Если они находятся в другом месте, задайте пути локально, без коммита:

```bash
git config docs.python /path/to/venv/bin/python
git config docs.vale /path/to/vale
```

В Windows указывайте полный путь в кавычках, предпочтительно с прямыми слешами.
Перед git push проверяются Vale и строгая сборка MkDocs.
Hook можно обойти, и он не включается автоматически при клонировании, поэтому серверный CI остаётся обязательной общей проверкой.
