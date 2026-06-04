# Contributing to Master Analyst Agent

Thank you for your interest in contributing.

## Development Setup

```bash
git clone https://github.com/fb4vprmxyd-web/master-analyst-agent.git
cd master-analyst-agent
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
cp .env.example .env  # Add your API keys
```

## Architecture

Each agent is an independent subprocess that outputs JSON to `shared_outputs/`. The master agent orchestrates execution, aggregates signals via weighted voting, and generates reports.

## Pull Request Guidelines

- Keep PRs focused — one feature or fix per PR
- Test your changes with `python run_demo.py --check`
- Ensure agent outputs remain valid JSON

## License

By contributing, you agree that your contributions will be licensed under the [MIT License](LICENSE).
