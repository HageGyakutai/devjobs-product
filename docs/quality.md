# Качество и подтверждение работоспособности

## Подтверждённый baseline

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
| CI release-ветки | успешно |
| Docker demo smoke | успешно |

## Demo smoke-сценарий

В локальной Docker-среде были подняты PostgreSQL, Redis, API и worker. После применения миграций создан демонстрационный профиль и набор из пяти вакансий.

Подтверждены успешные ответы screen-level API:

- Dashboard;
- Market Fit;
- Vacancies.

## Что следует из проверок

Проверки подтверждают, что backend MVP согласован по контрактам, проходит статический анализ, автоматические тесты и базовый сквозной demo-сценарий.

Они не заменяют нагрузочное тестирование, production-наблюдаемость и независимый security audit — эти направления не заявляются завершёнными в текущем MVP.
