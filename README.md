# MCP Twitter X

MCP Twitter X is a small Model Context Protocol server for posting to X/Twitter
with the `twitter-api-v2` client. It exposes an SSE transport so an MCP client can
connect to the server and call the included tools.

## Tools

| Tool | Purpose |
| --- | --- |
| `addTwoNumbers` | Example tool that adds 2 numbers. |
| `createPost` | Posts a status update through configured X/Twitter API credentials. |

## Setup

Install the server dependencies:

```bash
cd server
npm install
```

Create `server/.env` with your X/Twitter app credentials:

```dotenv
TWITTER_API_KEY=replace-me
TWITTER_API_SECRET=replace-me
TWITTER_ACCESS_TOKEN=replace-me
TWITTER_ACCESS_TOKEN_SECRET=replace-me
```

Start the MCP server:

```bash
npm start
```

The server listens on `http://localhost:3001`, with:

- SSE endpoint: `http://localhost:3001/sse`
- Message endpoint: `http://localhost:3001/messages`

## Client Notes

Point any MCP client that supports SSE transports at the `/sse` endpoint. Keep
the `.env` file local, do not paste credentials into prompts, and review every
`createPost` call before allowing the server to publish.

## OpenClaw Companion

If an OpenClaw workflow needs account-scoped public X/Twitter context before it
calls this MCP server, TweetClaw can provide a separate reviewed source step:

```bash
openclaw plugins install npm:@xquik/tweetclaw
```

Use that step for bounded searches, tweet or reply lookup, follower exports,
media context, monitor evidence, webhook events, and giveaway draw inputs. Keep
posting through this MCP server's configured X/Twitter API credentials unless
you deliberately move a workflow to another approved publishing tool.
