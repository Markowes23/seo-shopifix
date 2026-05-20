# Skill: On-Page SEO Engine

## Instructions
When a product is passed from the sourcer, run it through this optimization pipeline:

1. **Keyword Mapping:** Research primary and semantic LSI (Latent Semantic Indexing) keywords for the item.
2. **The 3-Part Description Rule:**
   - *The Hook:* An emotional, benefit-driven opening line.
   - *The Specs:* Bullet points mapping features to physical real-world benefits.
   - *The FAQ:* 3 specific questions users type into Google regarding this product type.
3. **Meta Fields Generation:** Ensure character counts map to search engine display limits.

## Input Schema
```json
{
  "product_data": {
    "raw_title": "string",
    "key_features": ["string"],
    "niche": "string",
    "proposed_retail_price": number
  },
  "seo_focus": "string (e.g., 'long-tail keywords', 'user intent', 'pain points')"
}
```

## Execution Pipeline

### Phase 1: Keyword Research
- Identify primary keyword (40-60 monthly searches)
- Extract 5-7 LSI keywords (semantic variations)
- Analyze search intent: Informational vs. Commercial vs. Transactional
- Build keyword map with placement zones (title, description, meta)

### Phase 2: Content Generation

#### The Hook (Opening Line)
- Lead with **benefit**, not feature
- Include emotional trigger (transformation, relief, confidence)
- Keep under 25 words
- Example: "Finally eliminate kitchen clutter with this space-saving gadget"

#### The Specs (Bullet Points)
- Map each feature to real-world benefit
- Use power words: "prevents", "reduces", "eliminates", "saves"
- Include measurements or specifics
- 5-7 bullets maximum
- Example:
  - ✅ Compact design saves 60% counter space
  - ✅ Non-slip base prevents sliding during use
  - ✅ Dishwasher-safe for easy cleaning

#### The FAQ Section
- Write 3 questions users actually Google
- Answer directly and briefly (50-75 words max per answer)
- Include secondary keywords naturally
- Examples:
  - "Is [product] worth the price?"
  - "How long does [product] last?"
  - "Can I use [product] with [related item]?"

### Phase 3: Meta Fields
- **Title Tag:** 50-60 characters, primary keyword first
- **Meta Description:** 150-160 characters, benefit-driven, include CTA

## Execution Template
Store the output as an absolute JSON object:
```json
{
  "title": "[Optimized Keyword-Rich Title]",
  "handle": "url-slug-with-hyphens",
  "body_html": "<p><strong>The Hook:</strong> [Opening benefit line]</p><h2>Key Benefits</h2><ul><li>[Benefit 1]</li><li>[Benefit 2]</li></ul><h2>Frequently Asked Questions</h2><h3>[Question 1]</h3><p>[Answer 1]</p>",
  "metafields": {
    "title_tag": "[Under 60 chars]",
    "description_tag": "[Under 160 chars with CTA]",
    "primary_keyword": "string",
    "lsi_keywords": ["keyword1", "keyword2"]
  },
  "optimization_score": 0-100,
  "ready_for_publish": boolean
}
```

## Quality Checklist
- [ ] No supplier description copy-paste detected
- [ ] Primary keyword in title and first 100 words
- [ ] 3+ LSI keywords naturally distributed
- [ ] FAQ section includes actual Google queries
- [ ] Meta title under 60 chars
- [ ] Meta description under 160 chars with CTA
- [ ] Optimization score >= 80
- [ ] Human-readable, not spammy tone

## SEO Best Practices
- Always prefer "you" language over brand-centric
- Use active voice
- Include 1-2 long-tail keyword variations
- Add numbers/specifics where possible
- Internal linking opportunities identified
- No keyword stuffing (keyword density < 2.5%)
