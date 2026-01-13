# MRBS — Machine-Readable Brand System

<p align="center">
  <strong>Making brand identity accessible to AI agents.</strong>
</p>

<p align="center">
  <a href="https://github.com/MRBSystem/MRBS-Specification">Specification</a> •
  <a href="https://github.com/MRBSystem/MRBS-Specification/blob/main/docs/getting-started.md">Getting Started</a> •
  <a href="https://github.com/MRBSystem/MRBS-Specification/blob/main/example">Example</a> •
  <a href="https://github.com/MRBSystem/MRBS-Specification/discussions">Discussions</a>
</p>

---

## The Problem

Traditional brand guidelines were designed for human designers — PDF brandbooks, PowerPoint style guides, scattered documentation. When you ask an AI agent to create brand-compliant content, it can't effectively use these materials:

- **PDFs** → Unstructured, unparseable
- **Color swatches** → Values extractable, context lost
- **"Use plenty of white space"** → Subjective, not testable
- **Logo usage rules** → Prose descriptions, no validation

**Result:** AI-generated content that looks generic, ignores brand rules, requires extensive revision.

## The Solution

**MRBS** is an open specification that transforms brand identity into structured, semantic, machine-readable formats that AI agents can query, interpret, and validate against.

```
brand-system/
├── brand.manifest.json       ← AI reads this first
├── visual/
│   ├── colors.tokens.json    ← Colors with usage rules
│   └── typography.tokens.json
├── identity/
│   └── voice-tone.yaml       ← Writing guidelines by context
├── rules/
│   └── constraints.yaml      ← Testable do's and don'ts
└── templates/
    └── presentation/manifest.json
```

### Before MRBS
```
"Our primary blue (#0066CC) should be used for headlines 
and call-to-action buttons. Avoid using it for body text."
```

### After MRBS
```json
{
  "primary": {
    "$value": "#0066CC",
    "usage": {
      "recommended": ["headlines", "cta_buttons"],
      "prohibited": ["body_text"]
    },
    "min_contrast_ratio": 4.5
  }
}
```

---

## Key Principles

| Principle | Description |
|-----------|-------------|
| **Semantic over Visual** | Describe meaning and intent, not just appearance |
| **Rules as Code** | Transform prose guidelines into testable constraints |
| **Context-Aware** | Different rules for different contexts (formal, casual, etc.) |
| **Platform-Agnostic** | Works with Claude, ChatGPT, Gemini, or any AI system |
| **Human + Machine** | Readable by both humans and AI agents |

---

## Repositories

| Repository | Description |
|------------|-------------|
| [**MRBS-Specification**](https://github.com/MRBSystem/MRBS-Specification) | Core specification, schemas, and reference implementation |

---

## Quick Example

**Color tokens with semantic metadata:**
```json
{
  "color": {
    "brand": {
      "primary": {
        "$value": "#0066CC",
        "semantic_role": "brand_identity",
        "usage": {
          "recommended": ["headings", "buttons", "links"],
          "prohibited": ["body_text", "large_backgrounds"]
        },
        "pair_with": ["white", "neutral-100"],
        "accessibility": {
          "wcag_level": "AA",
          "min_contrast_ratio": 4.5
        }
      }
    }
  }
}
```

**Voice guidelines as structured rules:**
```yaml
voice:
  core_attributes:
    - "Professional but approachable"
    - "Confident without arrogance"

tone_by_context:
  formal:
    use_for: ["legal", "investor_communications"]
    rules:
      contractions: false
      
  conversational:
    use_for: ["blog", "social_media"]
    rules:
      contractions: true
```

---

## Integration

MRBS works with any AI platform:

- **Claude** — System prompts, Projects, MCP servers
- **ChatGPT** — Custom GPTs with knowledge base
- **API integrations** — REST endpoints for enterprise
- **Design tools** — Export to Figma Variables, Style Dictionary

---

## Benefits

| Metric | Traditional | With MRBS |
|--------|-------------|-----------|
| Presentation creation | 4-8 hours | 15-30 minutes |
| Brand compliance | 60-70% | 95%+ |
| Revision cycles | 2-4 rounds | 0-1 rounds |
| Designer bottleneck | High | Eliminated |

---

## Get Started

1. **Read the spec:** [MRBS-Specification](https://github.com/MRBSystem/MRBS-Specification)
2. **Explore the example:** [Reference implementation](https://github.com/MRBSystem/MRBS-Specification/tree/main/example)
3. **Follow the guide:** [Getting Started](https://github.com/MRBSystem/MRBS-Specification/blob/main/docs/getting-started.md)
4. **Migrate your brand:** [Migration Guide](https://github.com/MRBSystem/MRBS-Specification/blob/main/docs/migration-guide.md)

---

## Contributing

MRBS is an open specification. We welcome:

- 🐛 Issue reports and suggestions
- 📝 Documentation improvements
- 🔧 Validators and converters
- 🌍 Translations
- 💡 Implementation examples

See [CONTRIBUTING.md](https://github.com/MRBSystem/MRBS-Specification/blob/main/CONTRIBUTING.md) for guidelines.

---

## License

[Apache 2.0](https://github.com/MRBSystem/MRBS-Specification/blob/main/LICENSE) — Use freely, build commercially, contribute back.

---

<p align="center">
  <sub>MRBS builds on the work of the <a href="https://www.w3.org/community/design-tokens/">W3C Design Tokens Community Group</a>, <a href="https://amzn.github.io/style-dictionary/">Style Dictionary</a>, and <a href="https://modelcontextprotocol.io">Model Context Protocol</a>.</sub>
</p>
