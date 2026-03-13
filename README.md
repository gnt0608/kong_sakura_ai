# kong_sakura_ai

Minimal Kong AI Proxy setup for connecting to Sakura AI Engine through its OpenAI-compatible Chat Completions endpoint.

## Files

- `docker-compose.yml`: starts Kong Gateway in DB-less mode
- `kong.yaml`: declarative config with the `ai-proxy` plugin
- `.env.example`: sample environment variables

## Usage

1. Copy `.env.example` to `.env`
2. Set `KONG_LICENSE_DATA`
3. Set `SAKURA_AI_AUTH_HEADER` to the full header value, for example `Bearer <your-token>`
4. Run `docker compose up -d`
5. Send requests to `http://localhost:8000/sakura-ai/chat`

Specify the Sakura model name in the request body.

```bash
curl -X POST http://localhost:8000/sakura-ai/chat \
  -H "Content-Type: application/json" \
  -d '{
    "model": "your-sakura-model",
    "messages": [
      { "role": "system", "content": "You are a helpful assistant." },
      { "role": "user", "content": "Hello" }
    ]
  }'
```
