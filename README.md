# LLM-chatbot-telegram

A Node.js-powered Telegram bot furnishing access to diverse AI language models via OpenRouter.ai integration, complete with administrative functions and usage monitoring.

## Capabilities

- Support for multiple AI models (e.g., Claude, GPT-4, GPT-3.5, Mistral)
- User access control system (whitelist)
- Dialogue management
- Usage monitoring and analytics
- Administrator privileges
- Request throttling
- Error management

## Preconditions

- Docker and Docker Compose
- Telegram Bot Token
- OpenRouter API Key
- Administrator Telegram Identifiers

For local development excluding Docker:

- Node.js v18 or newer
- MongoDB v6 or newer

## Docker-Based Deployment

1. Clone the source code repository and switch to the project folder:

```bash
https://github.com/Dev-Sphere111/LLM-chatbot-telegram/
cd LLM-chatbot-telegram
```

2. Establish a `.env` file with your specific configuration (refer to the Environment Variables section further down).

3. Construct and initiate the containers:

```bash
docker-compose up -d
```

4. Observe the logs:

```bash
docker-compose logs -f
```

5. Halt the containers:

```bash
docker-compose down
```

To reconstruct the application following modifications:

```bash
docker-compose up -d --build
```

## Local Setup

1. Duplicate the repository:

```bash
https://github.com/Dev-Sphere111/LLM-chatbot-telegram/
cd LLM-chatbot-telegram
```

2. Install project dependencies:

```bash
npm install
```

3. Create a `.env` file containing the necessary settings:

```bash
# Bot Settings
TELEGRAM_BOT_TOKEN=your_telegram_bot_token
OPENROUTER_API_KEY=your_openrouter_api_key
NODE_ENV=development

# Database Connection
MONGODB_URI=mongodb://localhost:27017/llm-chat-bot

# Security Parameters
JWT_SECRET=your_jwt_secret
JWT_EXPIRY=24h
ENCRYPTION_KEY=your_encryption_key

# Administrator Setup
ADMIN_TELEGRAM_IDS=123456,789012

# OpenRouter Settings
DEFAULT_MODEL=claude-2
MAX_TOKENS=2000
TEMPERATURE=0.7

# Request Throttling
RATE_LIMIT_WINDOW=15m
RATE_LIMIT_MAX_REQUESTS=100

# Logging Configuration
LOG_LEVEL=info
LOG_FILE_PATH=logs/app.log
```

4. Compile the project:

```bash
npm run build
```

## Development Phase

Launch the development server:

```bash
npm run dev
```

Execute tests:

```bash
npm test
```

Analyze code with linter:

```bash
npm run lint
```

Reformat code:

```bash
npm run format
```

## Project Layout

```
src/
  ├── config/
  │   ├── env.config.ts
  │   ├── logger.config.ts
  │   ├── db.config.ts
  │   └── openrouter.config.ts
  │
  ├── models/
  │   ├── user.model.ts
  │   ├── conversation.model.ts
  │   └── usage.model.ts
  │
  ├── controllers/
  │   ├── bot.controller.ts
  │   ├── admin.controller.ts
  │   └── usage.controller.ts
  │
  ├── services/
  │   ├── bot.service.ts
  │   ├── user.service.ts
  │   └── model.service.ts
  │
  ├── middleware/
  │   ├── auth.middleware.ts
  │   ├── rate-limit.middleware.ts
  │   └── error.middleware.ts
  │
  ├── types/
  │   └── errors.ts
  │
  └── utils/
      ├── validation.ts
      └── formatting.ts
```

## Accessible Commands

- `/newchat` - Initiate a new dialogue
- `/clearchat` - Erase dialogue history
- `/changemodel` - Modify the active AI model
- `/usage` - Display personal usage metrics
- `/help` - Show a list of usable commands

## Administrator Commands

- `/whitelist <user_id>` - Authorize a user
- `/unwhitelist <user_id>` - Revoke user authorization
- `/stats` - Exhibit global usage data
- `/models` - Oversee available AI models

## How to Contribute

1. Fork the project repository
2. Establish your feature branch (`git checkout -b feature/novel-enhancement`)
3. Commit your alterations (`git commit -m 'Introduce a novel enhancement'`)
4. Push to your branch (`git push origin feature/novel-enhancement`)
5. Initiate a Pull Request

## Licensing

This project is distributed under the ISC License.

## Credits

- [node-telegram-bot-api](https://github.com/yagop/node-telegram-bot-api)
- [OpenRouter](https://openrouter.ai/)
- [Mongoose](https://mongoosejs.com/)
- [Express](https://expressjs.com/)
