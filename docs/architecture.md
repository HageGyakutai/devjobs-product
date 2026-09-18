# Архитектура backend

## Принцип

DevJobs построен как слоистый backend. HTTP-роуты отвечают за транспорт и валидацию, а продуктовые правила живут вне роутеров.

```text
API router
  → dependency injection
    → use case
      → service / domain logic
        → repository / external adapter
          → PostgreSQL, Redis, HH API, AI provider
```

## Основные границы

| Слой | Ответственность |
|---|---|
| API / routers | HTTP, Pydantic-валидация, статусы и ответы |
| Dependencies | Сбор зависимостей и инфраструктурных компонентов |
| Use cases | Сценарии продукта: резюме, вакансии, аналитика, экранные данные |
| Services / domain | Расчёты, matching, правила формирования рекомендаций |
| Repositories | Изолированный доступ к PostgreSQL |
| Workers | Долгие операции: сбор вакансий и анализ рынка |
| External adapters | HH OAuth/API и AI-провайдеры |

## Продуктовая модель

Главный агрегат — профиль кандидата. Он строится из резюме и подтверждается пользователем. Вакансии образуют рыночный профиль. На пересечении профиля кандидата и рынка формируется Career Market Fit.

```text
Candidate Profile + Market Profile
              ↓
       Career Market Fit
              ↓
Strengths · Skill gaps · Vacancy matches · Roadmap
```

## Асинхронный сценарий

Анализ рынка не блокирует HTTP-запрос. API создаёт запуск анализа со статусом, worker собирает и обрабатывает вакансии, а frontend получает прогресс и итоговый компактный snapshot.

Это позволяет отделить пользовательский интерфейс от длительных внешних операций и корректно обрабатывать ошибки и повторные запуски.

## Frontend-ready API

Для будущего интерфейса backend предоставляет не только низкоуровневые сущности, но и готовые DTO на уровне экранов: dashboard, market fit, список вакансий, roadmap, integrations и settings. Такой контракт уменьшает связность frontend с внутренней доменной моделью.
