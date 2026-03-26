# LLM Integration for Node.js

> Production-ready reference implementations for connecting Node.js applications to language model APIs with resilience, cost tracking, and observability baked in.

## 🎯 What This Folder Contains

**Ready-to-drop-in modules** for production Express/Fastify services that handle:
- ✅ Full LLM integration lifecycle
- ✅ Error boundaries and graceful degradation
- ✅ Cost instrumentation and observability
- ✅ Provider-agnostic abstractions where applicable

## 🔧 Coverage: Full Integration Lifecycle

### API Integration
- 🔌 **Streaming responses** — handle streaming model output efficiently
- 📦 **Structured output parsing** — extract JSON/typed data from model responses
- 🔄 **Retry logic with exponential backoff** — resilience against transient failures
- ⏸️ **Graceful degradation** — fallback behavior when endpoints unavailable

### Resource Management
- 💰 **Token budget management** — track and limit token consumption per request/feature
- 📊 **Cost instrumentation** — lightweight middleware for cost tracking
- 🎯 **Feature-level aggregation** — see costs broken down by business feature
- 📈 **Observability-ready format** — integrate directly with your monitoring stack

### Resilience
- 🛡️ **Proper error boundaries** — model timeout never takes down the calling service
- ⏱️ **Timeout handling** — explicit controls for request timeouts
- 📍 **Provider abstractions** — swap providers without rewriting integration code

## 💻 Implementation Features

- **Production-ready code** — minimal modification needed for your service
- **Modular design** — pick what you need, leave the rest
- **Async patterns** — proper error handling for concurrent requests
- **Offline testing** — integration tests use recorded API responses
  - ✅ Suite runs offline without API keys
  - ✅ Deterministic — no flaky network tests
  - ✅ Cost-free — no API charges during CI

## 🛠️ Primary SDK

- **Anthropic SDK** — first-class support
- **Other providers** — notes on provider-agnostic patterns