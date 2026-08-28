## Установка навыка

Навык можно установить прямо из публичного GitHub-репозитория — клонировать его не нужно. Нужны Node.js и `npx`.

### Codex и Claude Code

```bash
npx skills add B216-lab/agentic --skill geopanel-agent --global --agent codex --agent claude-code
```

Команда загрузит навык `geopanel-agent` и установит его глобально для Codex и Claude Code. Чтобы выбрать другие поддерживаемые агенты или установить навык только для текущего проекта, запустите команду без `--global` и при необходимости измените параметры `--agent`. Список доступных навыков репозитория можно посмотреть без установки:

```bash
npx skills add B216-lab/agentic --list
```

После установки перезапустите агент. Чтобы обновить навык, повторите команду установки.

### Настройка доступа к GeoPanel

1. Создайте API-токен в разделе **Доступ к рабочей области** и сохраните его в отдельный файл:

   ```bash
   mkdir -p ~/.config/geopanel
   chmod 700 ~/.config/geopanel
   read -rsp "Токен GeoPanel: " geopanel_token
   printf '%s' "$geopanel_token" > ~/.config/geopanel/token
   unset geopanel_token
   chmod 600 ~/.config/geopanel/token
   ```

2. Перед запуском агента задайте адрес GeoPanel и путь к токену:

   ```bash
   export GEOPANEL_BASE_URL=https://geopanel.example.com
   export GEOPANEL_TOKEN_FILE="$HOME/.config/geopanel/token"
   ```

Пример запроса агенту: `Используй geopanel-agent, изучи мои наборы данных и создай дашборд.`
