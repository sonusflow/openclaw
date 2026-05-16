# Extracted OpenClaw Agents from kalarepa-iMac

Extracted 2026-03-08 from kalarepa-iMac (10.20.10.201).

## Agents

### sonus-flow (SonusFlow)

- **Purpose**: Voice AI assistant for SonusFlow company (AI/tech services)
- **Default model**: moonshot/kimi-k2.5
- **Language**: Polish (voice-first, TTS-optimized)
- **boot.md**: Polish system prompt for phone conversations about SonusFlow services
- **SOUL.md**: Full knowledge base covering SonusFlow, SonusFlow sp. z o.o., and Sonus Art

### sonus-art (Sonus Art)

- **Purpose**: Voice AI assistant for Sonus Art handpan shop
- **Default model**: anthropic/claude-opus-4-6
- **Language**: Polish (voice-first, TTS-optimized)
- **boot.md**: Polish system prompt for phone conversations about handpan sales
- **SOUL.md**: Full knowledge base covering handpan inventory, FAQ, and routing

## openclaw.json Agent Config

Add these to the `agents.list` array in openclaw.json:

```json
{
  "id": "sonus-flow",
  "name": "SonusFlow",
  "workspace": "<OPENCLAW_DIR>/workspace-sonus-flow",
  "agentDir": "<OPENCLAW_DIR>/agents/sonus-flow/agent",
  "model": "moonshot/kimi-k2.5"
},
{
  "id": "sonus-art",
  "name": "Sonus Art",
  "workspace": "<OPENCLAW_DIR>/workspace-sonus-art",
  "agentDir": "<OPENCLAW_DIR>/agents/sonus-art/agent",
  "model": "anthropic/claude-opus-4-6"
}
```

## Shared Auth Profiles

Both agents share the same credentials:

- **Anthropic**: sk-ant-oat01-Mla3... (in auth-profiles.json)
- **Moonshot**: sk-JKuMa59sFey2... (Kimi K2.5 API)
- **OpenAI (Speaches)**: "not-needed" (local Speaches STT/TTS)

## Mattermost Integration

The kalarepa OpenClaw instance connects to msg.sonusflow.io with bot token `masdb8y6bpf6tdz166w9g9gxby`.
Group allowlist: `td5ptduamtdgjec68mejbq1cyo`.

## Botwinek Status

- **botwinek-5090** (10.100.0.120): macOS VM on sf-ai (5090 host). SSH password rejected (exit code 5). Could not verify OpenClaw presence.
- **botwinka** (10.100.0.202): Mac mini. SSH connection timed out — host appears offline.

## File Structure

```
extracted-agents/
  sonus-flow/
    agent/
      boot.md              # System prompt (Polish, voice-first)
      models.json           # Moonshot/Kimi K2.5 provider config
      auth-profiles.json    # API keys (Anthropic, Moonshot, OpenAI)
    workspace/
      IDENTITY.md           # Name: Sonus, emoji: mic
      SOUL.md               # Full knowledge base + behavior rules
  sonus-art/
    agent/
      boot.md              # System prompt (Polish, voice-first)
      models.json           # Moonshot/Kimi K2.5 provider config
      auth-profiles.json    # API keys (same as sonus-flow)
    workspace/
      IDENTITY.md           # Name: Sonus Art, emoji: musical note
      SOUL.md               # Handpan knowledge + behavior rules
```
