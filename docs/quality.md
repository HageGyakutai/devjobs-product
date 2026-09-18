# Качество и проверка работоспособности

## Release-кандидат backend

Перед публикацией продуктового описания release-ветка прошла полный набор проверок:

| Проверка | Результат |
|---|---|
| Pytest | **505 passed** |
| Ruff | успешно |
| MyPy | успешно |
| Runtime OpenAPI schema check | успешно |
| Import boundaries check | успешно |
| Thin routers check | успешно |
| Datetime policy check | успешно |
| Git diff check | успешно |
| GitHub Actions CI | успешно |

## Demo smoke-сценарий

В локальной Docker-среде были подняты PostgreSQL, Redis, API и worker. После применения миграций создан демонстрационный профиль и набор вакансий.

Проверены основные screen-level endpoints:

- dashboard;
- market fit;
- vacancies.

Каждый endpoint вернул успешный ответ.

## Что это означает

Проверки не заменяют production-наблюдаемость, нагрузочное тестирование и security audit. Они подтверждают, что текущий backend MVP согласован по контрактам, проходит статический анализ, автоматические тесты и базовый сквозной demo-сценарий.
