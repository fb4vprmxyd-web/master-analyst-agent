# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability, please report it responsibly via [GitHub's private vulnerability reporting](https://github.com/fb4vprmxyd-web/master-analyst-agent/security/advisories/new).

## Security Considerations

- **API Keys**: All secrets stored in `.env` (never committed — listed in `.gitignore`)
- **LLM API Keys**: Anthropic and OpenAI keys provide access to paid APIs — treat as passwords
- **Alpha Vantage**: 4 separate keys used for parallel data fetching — rotate if compromised
- **Financial Data**: Analysis outputs in `shared_outputs/` may contain market-sensitive recommendations
