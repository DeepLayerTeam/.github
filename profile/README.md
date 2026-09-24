# DeepLayer

**Minecraft-разработка, инфраструктура и инструменты для собственной экосистемы NeverMine.**

DeepLayer — команда, сосредоточенная исключительно на **Minecraft**.

Мы развиваем собственный Minecraft-проект **NeverMine**, а также техническую экосистему вокруг него: лаунчер, runtime, клиентскую защиту, серверные интеграции, аутентификацию, управление устройствами, совместимость с различными loaders и инфраструктуру релизов.

## NeverMine

**NeverMine** — основной Minecraft-проект DeepLayer.

Вокруг него развивается собственная техническая инфраструктура, которая охватывает путь от авторизации пользователя и доставки клиентской сборки до запуска Minecraft и проверки доступа на серверной стороне.

NeverMine используется как практическая среда для развития и проверки компонентов экосистемы Never в реальных Minecraft-сценариях.

## Экосистема Never

| Проект | Назначение | Статус |
| --- | --- | --- |
| [**NeverLauncher**](https://github.com/DeepLayerTeam/NeverLauncher) | Self-hosted Minecraft LauncherOps-платформа: клиент, backend, Auth Federation, Device Trust, Minecraft Compatibility, ServerBridge, release pipeline и управление доставкой | Активная разработка |
| [**NeverRuntime**](https://github.com/DeepLayerTeam/NeverRuntime) | Runtime-компонент для подготовки окружения и запуска Minecraft-клиента | Развивается |
| [**NeverGuard**](https://github.com/DeepLayerTeam/NeverGuard) | Клиентский security boundary, authenticated IPC, integrity evidence и защита процесса запуска Minecraft | Развивается |
| [**NeverExtensions**](https://github.com/DeepLayerTeam/NeverExtensions) | Дополнительные Minecraft-интеграции и расширения экосистемы Never | В разработке |

## Основные направления

### Minecraft LauncherOps

NeverLauncher объединяет управление:

- Minecraft-сборками;
- профилями запуска;
- версиями и loaders;
- каналами обновлений;
- клиентскими файлами;
- авторизацией;
- релизами;
- запуском игры;
- серверными интеграциями.

Платформа ориентирована на self-hosted эксплуатацию и использование в собственной Minecraft-инфраструктуре.

### Minecraft Compatibility

Одно из ключевых направлений — реальная совместимость с Minecraft-клиентом и распространёнными loaders.

Разрабатываются и проверяются сценарии для:

- Vanilla;
- Fabric;
- Quilt;
- Forge;
- NeoForge.

Совместимость должна подтверждаться реальными build/test/E2E-сценариями, а не только наличием декларативной поддержки.

### Authentication

Экосистема включает собственный auth-контур и интеграцию с Minecraft authentication flow.

Развиваются:

- локальная авторизация;
- внешние auth providers;
- OIDC;
- Microsoft integration;
- passkeys и MFA;
- управление сессиями;
- Minecraft-compatible auth flow;
- единая пользовательская identity.

### Device Trust

Device Trust связывает пользовательскую сессию с доверенным устройством.

Система включает:

- device keys;
- OS secure storage;
- hardware-bound identities;
- управление устройствами;
- permanent revocation;
- challenge-response;
- binding epoch;
- risk-based enforcement.

Device trust применяется не только к панели или API, но и к Minecraft-сессиям и серверному входу.

### NeverGuard

NeverGuard — отдельный компонент защиты Minecraft-клиента и процесса запуска.

Основные направления:

- authenticated IPC;
- integrity evidence;
- process policy;
- server-verifiable guard evidence;
- Windows, Linux и macOS;
- интеграция с NeverRuntime и NeverLauncher.

Архитектура не строится вокруг агрессивных hooks.

Локальные проверки и platform integrity signals не выдаются за полноценную hardware remote attestation там, где соответствующего vendor evidence нет.

### ServerBridge

ServerBridge связывает backend NeverLauncher с Minecraft-серверами и proxy-средой.

Поддерживаемые и развиваемые направления:

- Bukkit;
- Spigot;
- Paper;
- Purpur;
- Folia;
- Velocity;
- Waterfall;
- BungeeCord;
- Fabric;
- Forge;
- NeoForge.

ServerBridge используется для server-side проверки:

- пользовательской сессии;
- trusted device;
- trust state;
- project/profile/channel;
- one-time join tickets;
- integrity evidence.

### Minecraft Server Infrastructure

DeepLayer также развивает архитектуру вокруг эксплуатации собственного Minecraft-проекта NeverMine:

- серверные интеграции;
- proxy topology;
- backend services;
- доступ игроков;
- обновления;
- deployment;
- observability;
- эксплуатационную автоматизацию.

## Release Engineering

Для критичных Minecraft-компонентов используются автоматизированные проверки:

- CI;
- unit/integration tests;
- E2E;
- compatibility matrices;
- migration verification;
- release certification;
- cross-platform builds;
- production packaging.

Релиз считается готовым только после прохождения соответствующих проверок.

## Инженерные принципы

- **Minecraft first.** Все основные разработки DeepLayer Team связаны с Minecraft и NeverMine.
- **Self-hosted.** Оператор сохраняет контроль над инфраструктурой, данными и политиками доступа.
- **Fail closed.** Ошибка trust/security-проверки не должна превращаться в автоматическое разрешение доступа.
- **Реальная совместимость.** Поддержка платформы или loader должна подтверждаться работающим сценарием.
- **Проверяемая безопасность.** Заявленные гарантии должны соответствовать реально собираемому evidence.
- **Кроссплатформенность.** Windows, Linux и macOS являются целевыми платформами там, где это применимо.
- **Автоматизация.** Сборка, тестирование, миграции и релизы должны быть воспроизводимыми.
- **Поддерживаемость.** Upgrade path, документация, observability и миграции являются частью production-системы.

## Технологии

В Minecraft-проектах DeepLayer Team используются:

`Go` · `Rust` · `TypeScript` · `React` · `Tauri` · `PostgreSQL` · `Redis` · `OpenAPI` · `Docker` · `GitHub Actions`

Также используются Minecraft-specific технологии и интеграции:

`Minecraft Protocol` · `Bukkit/Paper API` · `Velocity` · `Fabric` · `Forge` · `NeoForge`

## Репозитории

- [NeverLauncher](https://github.com/DeepLayerTeam/NeverLauncher)
- [NeverRuntime](https://github.com/DeepLayerTeam/NeverRuntime)
- [NeverGuard](https://github.com/DeepLayerTeam/NeverGuard)
- [NeverExtensions](https://github.com/DeepLayerTeam/NeverExtensions)

## Участие

Issues и pull requests принимаются в соответствующих репозиториях.

Перед отправкой изменений рекомендуется ознакомиться с документацией проекта, его текущими ограничениями и CI-требованиями.

## Лицензирование

Условия использования определяются лицензией каждого конкретного репозитория.

Перед использованием или распространением кода проверяйте файл `LICENSE` соответствующего проекта.
