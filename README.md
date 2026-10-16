# Seedream 5.0 Pro Prompts — 8 Tested Recipes With Outputs

<!-- conv-kit:v1 -->

<p align="center">
  <img src="assets/badges/price.svg" alt="observed unit price"> <img src="assets/badges/billing.svg" alt="billing model"> <img src="assets/badges/compat.svg" alt="OpenAI-compatible endpoint">
</p>

<p align="center">
  <img src="assets/01-product-hero-perfume.jpg" width="820" alt="Sample render via the APIMart image API">
</p>

> **from $0.014625 per image** (1K-layer $0.014625 · 1K $0.02925 · 2K-layer $0.02925) — 一个 OpenAI 兼容端点 `https://api.apimart.ai/v1`，无需包月套餐。*(数据观测于 2026-10-12)*

**[Get an API key](https://go.apimart.ai/k-e27ca4)** · **[Live pricing](https://go.apimart.ai/k-577905)** · **[Model page](https://go.apimart.ai/k-921179)** · [⚡ 60-second quickstart](#quickstart)

**为什么团队通过 APIMart 调用 Seedream 5.0 Pro（`seedream-5-0-pro`）**

- **一个 Key，整个目录。**同一个 `https://api.apimart.ai/v1` base URL 和 `Authorization` 请求头即可访问 Seedream 5.0 Pro（`seedream-5-0-pro`）以及图像、视频、语言等 300+ 模型——只需切换 `model` 字段，客户端无需改动。
- **$1 起充，按量付费。**没有订阅、也没有需要预先估算用量的预付费套餐：最低充值 $1，调用多少扣多少。
- **费用随响应一并返回。**每个完成的任务都会报告实际计费金额（`cost` / `credits_cost`）；状态为 `failed` 的任务会自动退款。
- **原生异步设计。**提交任务、拿到 `task_id`、轮询 `GET /v1/tasks/{id}`——批处理和重试都是普通的队列工作，不需要定制集成。

<!-- /conv-kit:v1 -->

**中文环境也叫:** 即梦图片

Eight **Seedream 5.0 Pro prompts** listed with an example render, the ratio, and what the call costs on this route. Copy a recipe, keep the structure, swap the subject.

- Model: `seedream-5-0-pro`
- Recipes: **8** (machine-readable in [`data/prompts.json`](data/prompts.json), table in [`PROMPTS.md`](PROMPTS.md))
- Effective price used below: **$0.0146 per image** — estimated cost of the whole set: **$0.117**

## What separates a usable recipe from a wasted call

Three rules held up across every render in this set:

1. **Name the material, not the adjective.** "Frosted glass", "matte ceramic", "layered paper" steer rendering far more
   than "beautiful" or "high quality".
2. **Set the light explicitly.** "Single softbox from the left", "golden hour backlight", "focus-stacked studio light"
   remove the guesswork the model would otherwise do for you.
3. **Pin the framing.** Ratio plus lens language (`85mm`, `24mm`, `macro`, overhead flat lay) decides whether the output
   drops into a layout unchanged.

## Prompt structure cheat-sheet

| Slot | What to write | Example |
| --- | --- | --- |
| Subject | one concrete object or person, with material | *frosted glass perfume bottle* |
| Light | direction + quality | *single softbox from the left* |
| Framing | ratio + lens or distance | *3:4, medium format look* |
| Setting | surface, backdrop, environment | *wet black stone slab* |
| Finish | render or film character | *commercial product photography* |

## The gallery

Each row is one recipe: example render, category, ratio, cost on this route and the exact prompt.

| Output | Recipe | Ratio | Cost | Prompt |
| --- | --- | --- | --- | --- |
| <img src="assets/01-product-hero-perfume.jpg" width="220" alt="Sample render via the APIMart image API"> | Product / e-commerce | 1:1 | $0.0146 | `Studio hero shot of a frosted glass perfume bottle on a wet black stone slab, single softbox from the left, faint mist, deep charcoal background, crisp label text, commercial product photography` |
| <img src="assets/02-food-overhead-ramen.jpg" width="220" alt="Sample render via the APIMart image API"> | Food photography | 4:3 | $0.0146 | `Overhead flat lay of a spicy miso ramen bowl with soft boiled egg, nori and scallions, dark ceramic table, chopsticks resting on the rim, natural window light, editorial food photography` |
| <img src="assets/03-cinematic-street-rain.jpg" width="220" alt="Sample render via the APIMart image API"> | Cinematic still | 16:9 | $0.0146 | `Rain soaked Kyoto alley at night, paper lantern reflections on wet stone, a lone figure with a transparent umbrella walking away, cinematic 35mm still, shallow depth of field, film grain` |
| <img src="assets/04-architectural-dusk.jpg" width="220" alt="Sample render via the APIMart image API"> | Architecture | 16:9 | $0.0146 | `Minimalist concrete villa on a cliff at dusk, warm interior light, infinity pool reflecting a violet sky, architectural photography, 24mm perspective, ultra sharp` |
| <img src="assets/05-fashion-editorial-studio.jpg" width="220" alt="Sample render via the APIMart image API"> | Fashion portrait | 3:4 | $0.0146 | `Editorial fashion portrait of a model in an oversized ivory wool coat, seamless light grey studio backdrop, crisp high key lighting, medium format detail, calm expression` |
| <img src="assets/06-illustration-layered-paper.jpg" width="220" alt="Sample render via the APIMart image API"> | Illustration | 1:1 | $0.0146 | `Layered paper cut illustration of a mountain lake at sunrise, five depth layers, soft pastel palette, subtle drop shadows, art print composition, clean vector edges` |
| <img src="assets/07-infographic-dashboard.jpg" width="220" alt="Sample render via the APIMart image API"> | Design / UI | 16:9 | $0.0146 | `Flat vector dashboard panel showing three gauge dials and abstract latency curves, muted blue and sand palette, generous white space, crisp geometric cards, no placeholder text` |
| <img src="assets/08-macro-botanical-detail.jpg" width="220" alt="Sample render via the APIMart image API"> | Macro nature | 3:2 | $0.0146 | `Macro photograph of a dew covered dandelion seed head against deep black background, focus stacked detail, iridescent droplets, studio lighting` |

## Run a recipe yourself

```bash
export APIMART_API_KEY=...
python examples/run_recipes.py --dry-run                 # list the recipes, no network
python examples/run_recipes.py --limit 2                 # generate two of them
```

```bash
curl --request POST --url https://api.apimart.ai/v1/images/generations \
  --header "Authorization: Bearer $APIMART_API_KEY" --header 'Content-Type: application/json' \
  -d '{"model":"seedream-5-0-pro","prompt":"<paste a prompt>","size":"1:1","resolution":"1K"}'
```

Result links expire 72 hours after completion, so store the outputs; the completed task carries `cost` for reconciliation.

## FAQ

**Are these prompts free to reuse?**

Yes — the prompt text in this repository is MIT licensed. The generated images and any third-party marks they contain remain your responsibility, and you should check the model vendor's terms before publishing commercial work.

**Why do the recipes use different aspect ratios?**

Because ratio is a layout decision, not a style one: 1:1 for catalogue and icons, 16:9 for hero and video thumbnails, 3:4 or 2:3 for portraits and print. Pinning it up front avoids cropping later.

**How much does one recipe cost to run?**

**from $0.014625 per image** (1K-layer $0.014625 · 1K $0.02925 · 2K-layer $0.02925). Every completed task reports the exact amount in its `cost` field; a failed task is refunded.

**Can I use a recipe as a template for another subject?**

That is the point. Keep the structure (subject + light + framing + setting + finish) and replace the subject; changing everything at once makes it impossible to tell which phrase moved the output.

<!-- related-repos:auto -->
## Related repositories

- **Same model, this language** — the other half of this pair: [seedream-5-0-pro-api-cn](https://github.com/a2hnks5fo-t/seedream-5-0-pro-api-cn)
- **Same model, other languages** — 9 more language builds: Deutsch `seedream-5-0-pro-api-de` · Español [seedream-5-0-pro-api-es](https://github.com/pblexl325ktue/seedream-5-0-pro-api-es) · Français [seedream-5-0-pro-api-fr](https://github.com/jef7is8ris/seedream-5-0-pro-api-fr) · Relay/gateway `seedream-5-0-pro-api-gateway` · Bahasa [seedream-5-0-pro-api-id](https://github.com/ayekoa913g/seedream-5-0-pro-api-id) · 日本語 [seedream-5-0-pro-api-ja](https://github.com/d2td7nw6r/seedream-5-0-pro-api-ja) · 한국어 [seedream-5-0-pro-api-ko](https://github.com/d2td7nw6r/seedream-5-0-pro-api-ko) · Português [seedream-5-0-pro-api-pt](https://github.com/znscxwmvl8m7m/seedream-5-0-pro-api-pt) · Русский [seedream-5-0-pro-api-ru](https://github.com/rqox1kopnhnd7c/seedream-5-0-pro-api-ru)
- **More models in this language** — [midjourney-api-cn](https://github.com/apimartycl6k972t/midjourney-api-cn) · [gemini-2-5-flash-image-preview-api-cn](https://github.com/hm-5j/gemini-2-5-flash-image-preview-api-cn) · [nano-banana-api-cn](https://github.com/mpflv/nano-banana-api-cn) · [gemini-3-1-flash-image-preview-api-cn](https://github.com/utp00/gemini-3-1-flash-image-preview-api-cn) · [nano-banana-2-api-cn](https://github.com/i3hxnu6/nano-banana-2-api-cn) · [gemini-3-pro-image-preview-api-cn](https://github.com/vd0tv42d/gemini-3-pro-image-preview-api-cn)
- **Topic hubs** — every build of this model, all languages: [seedream-5-0-pro](https://github.com/topics/seedream-5-0-pro) · [seedream-5-0-pro-api](https://github.com/topics/seedream-5-0-pro-api)

This repository is one build in a cross-linked set of API guides for the same model family; each language build links back to the others.
<!-- /related-repos:auto -->

## Attributed links (how this repository is measured)

| Purpose | Attributed link | Target |
| --- | --- | --- |
| Model page | <https://go.apimart.ai/k-921179> | `apimart.ai/zh/model/seedream-5-0-pro` |
| Live pricing | <https://go.apimart.ai/k-577905> | `apimart.ai/zh/pricing` |
| Get an API key | <https://go.apimart.ai/k-e27ca4> | `apimart.ai/zh/keys` |

Outbound APIMart links are minted through the promo link API; hand-made tracking parameters are rejected by
`tools/check_links.py` in CI.

## Disclosure

Seedream 5.0 Pro is a third-party model served through APIMart. This repository publishes prompts, example renders and
cost logic; it does not claim official status for any vendor, and model names and documentation belong to their owners.

## Repository map

```text
README.md              gallery, prompt structure and FAQ
PROMPTS.md             every recipe in one table
data/prompts.json      machine-readable recipes with per-unit cost
examples/run_recipes.py  batch runner (dry-run safe for CI)
tools/check_links.py   attribution guard
assets/                example renders via the APIMart image API (JPEG)
```

## License

MIT — see [LICENSE](LICENSE).
