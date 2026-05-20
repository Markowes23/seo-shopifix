# Skill: Trend Sourcing and Data Normalization

## Workflow
1. Use `google_search` to look up recent trending products within the specified niche (e.g., "trending TikTok kitchen gadgets 2026").
2. Analyze top competitor stores to extract their pricing models and layout styles using `url_context`.
3. Use `code_execution` to run a Python script that calculates a viable dropshipping margin (Targeting a minimum 3x markup over cost).

## Input Schema
```json
{
  "niche": "string (e.g., 'home organization', 'fitness accessories')",
  "search_trend": "string (e.g., 'trending on TikTok', 'viral Pinterest')",
  "target_price_range": {
    "min": number,
    "max": number
  },
  "minimum_margin_multiplier": 3
}
```

## Execution Pipeline

### Phase 1: Trend Research
- Query: Search for top 10 trending products in niche
- Filter by:
  - Recent trend velocity (last 30-90 days)
  - Supplier availability (AliExpress, Zendrop, Alibaba)
  - Retail competitive landscape
  - Margin viability (cost under $15 for 3x markup potential)

### Phase 2: Competitor Analysis
- Identify 3-5 top Shopify stores selling similar products
- Extract:
  - Product pricing (retail vs. cost estimates)
  - Page layout structure
  - Marketing angles (pain point, lifestyle, benefit-driven)
  - Customer review sentiment (quality, shipping time, value)
  - Ad copy patterns

### Phase 3: Supplier Data Collection
```python
# Python execution script to normalize supplier data
import json

supplier_data = {
    "raw_title": "AliExpress Product Title",
    "supplier_url": "https://aliexpress.com/...",
    "supplier_cost_price": 8.50,
    "estimated_shipping": 2.00,
    "total_landed_cost": 10.50,
    "proposed_retail_price": 34.99,  # 3.33x markup
    "gross_margin_percent": 70,
    "key_features": [
        "Compact design",
        "Non-slip base",
        "Easy to clean"
    ],
    "competitor_retail_avg": 32.99,
    "viability_score": 0-100  # Based on margin, trend velocity, reviews
}

# Validate: landed_cost * 3 <= proposed_retail_price
assert supplier_data["total_landed_cost"] * 3 <= supplier_data["proposed_retail_price"]
```

## Output Standard
Generate a clean data structure for the product:

```json
{
  "sourcing_metadata": {
    "trend_source": "string (TikTok, Pinterest, Google Trends)",
    "trend_velocity_score": 0-100,
    "niche_category": "string"
  },
  "supplier_data": {
    "raw_title": "Original supplier product name",
    "supplier": "string (AliExpress, Zendrop, etc.)",
    "supplier_url": "https://...",
    "sku": "string"
  },
  "pricing": {
    "cost_price": number,
    "shipping_cost": number,
    "total_landed_cost": number,
    "proposed_retail_price": number,
    "gross_margin_percent": number,
    "markup_multiplier": number
  },
  "product_details": {
    "key_features": [
      "string",
      "string"
    ],
    "estimated_weight": "string (grams)",
    "estimated_dimensions": "string (cm)",
    "materials": ["string"],
    "colors_available": ["string"]
  },
  "competitive_analysis": {
    "competitor_avg_price": number,
    "competitor_count": number,
    "market_saturation": "low|medium|high"
  },
  "viability_assessment": {
    "margin_viable": boolean,
    "trend_score": 0-100,
    "competition_score": 0-100,
    "overall_viability_score": 0-100,
    "recommendation": "PROCEED|CONSIDER|SKIP"
  }
}
```

## Margin Calculation Rules
- **Minimum Multiplier:** 3x (cost price to retail price)
- **Target Multiplier:** 3.5x - 4x (optimal balance: profit margin vs. competitive pricing)
- **Landed Cost:** Cost Price + Shipping + 5% contingency buffer
- **Gross Margin %:** (Retail Price - Landed Cost) / Retail Price * 100

## Quality Checklist
- [ ] Product found on multiple supplier platforms
- [ ] Customer reviews avg rating >= 4.0/5.0
- [ ] Shipping time <= 21 days (standard)
- [ ] Landed cost calculation verified
- [ ] Margin multiplier >= 3.0
- [ ] No obvious copyright/trademark violations
- [ ] Product images clear (not stolen/low quality)
- [ ] Niche has Google search volume >= 1,000/month

## Data Cleaning Rules
- Remove all supplier marketing jargon from raw_title
- Strip HTML/special characters
- Normalize color names (not "Blck" → "Black")
- Convert all measurements to metric (cm, grams)
- Remove duplicate/redundant features

## Output Format
All data normalized to JSON, ready for handoff to **seo-optimizer** skill.
