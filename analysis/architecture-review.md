# Архитектурный обзор Telegram iOS

## Слои приложения
- **UI** — отображение ChatViewController и списка сообщений
- **Presentation** — преобразование доменной модели в UI, обработка действий
- **Domain** — Message, Chat state, Peer
- **Data** — Postbox, кеширование, реактивные подписки
- **Network** — MTProto, синхронизация и отправка сообщений

## Поток данных
1. Сервер → Network Layer (MTProto)
2. Network Layer → Data Layer (Postbox)
3. Data Layer → Domain Layer
4. Domain Layer → Presentation / UI
5. UI обновляется

## Узкие места
- производительность рендеринга сообщений в больших чатах
- избыточные обновления UI через реактивный pipeline
- потенциальные задержки при частых обновлениях статуса сообщений
