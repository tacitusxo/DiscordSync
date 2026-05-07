# DiscordSync

<div align="center">
  <img src="assets/discord.png" width="80" />
  <p>A desktop app that monitors Discord channels and forwards messages to webhooks.</p>
</div>

## Overview

DiscordSync is an Electron app that listens to Discord channels via a self-bot token and automatically forwards incoming messages to specified webhooks. Keyword filtering lets you forward only messages that match your conditions.

## Requirements

- License key
- Discord user token

## Installation

```bash
git clone https://github.com/tacitusxo/discordsync.git
cd discordsync
npm install
```

## Configuration

On first launch, a `DiscordSync/` folder is automatically created in your home directory.

### config.json

```json
{
  "key": "your-license-key",
  "token": "your-discord-user-token"
}
```

### tasks.csv

Define forwarding tasks in CSV format.

| Column | Description |
|--------|-------------|
| `monitor_channel` | Discord channel ID to monitor |
| `webhook_url` | Destination webhook URL |
| `webhook_mention` | Mention to prepend to forwarded messages (optional) |
| `webhook_user_name` | Webhook sender name (defaults to original username) |
| `webhook_avatar_url` | Webhook avatar URL (defaults to original avatar) |
| `webhook_reference_enabled` | Append a link to the original message (`true` / `false`) |
| `positive_keywords_type` | Match mode for positive keywords (`all` / `or`) |
| `positive_keywords` | Keywords required for forwarding, separated by `+` |
| `negative_keywords_type` | Match mode for negative keywords (`all` / `or`) |
| `negative_keywords` | Keywords that suppress forwarding, separated by `+` |

**Match modes:**
- `all` — all specified keywords must be present
- `or` — at least one of the specified keywords must be present

**Example:**

```csv
monitor_channel,webhook_url,webhook_mention,webhook_user_name,webhook_avatar_url,webhook_reference_enabled,positive_keywords_type,positive_keywords,negative_keywords_type,negative_keywords
123456789012345678,https://discord.com/api/webhooks/xxx/yyy,@here,Bot,https://example.com/avatar.png,true,or,sale+discount,or,
```

## Development

```bash
npm start
```

## Build

```bash
npm run package
```

Build artifacts are output to `release/build/`.

## License

MIT
