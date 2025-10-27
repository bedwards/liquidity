# liquidity

Utilities for managing Shopify Liquid themes.

- [Liquid reference](https://shopify.dev/docs/api/liquid)
- [Shopify Liquid cheat sheet](https://www.shopify.com/partners/shopify-cheat-sheet)
- [Shopify Ajax API reference](https://shopify.dev/docs/api/ajax/reference)
- [Accelerated checkout](https://shopify.dev/docs/storefronts/themes/pricing-payments/accelerated-checkout) 

---

Copy example .env.

```
cp .env.example .env
```

Edit .env

```
SHOPIFY_CLI_THEME_TOKEN=admin.shopify.com → apps → theme access → create password → check email  

SHOPIFY_FLAG_STORE=example.myshopify.com

SHOPIFY_FLAG_STORE_PASSWORD=admin.shopify.com → sales channels → online store → preferences → password

SHOPIFY_FLAG_THEME_ID=liquidity
```

Export environment variables.

```
set -a; source .env; set +a
```

Initialize theme (this repo has initial theme with edits.)

```
shopify theme init liquidity-theme
cd liquidity-theme
```

## Add products and create a collection

admin.shopify.com → products → add product  
set `type` to "evidence"

admin.shopify.com → products → collections → add collection  
smart collection type
conditions → type is equal to evidence  

## Edit liquid templates

templates/index.json calls in sections/hello-world.liquid, so editing that will render on the home page.

```
<script>
  const e = {{ collections.evidence.products[0] | json }};
  const k = Object.keys(e)
  console.log(JSON.stringify(k, null, 2));
</script>

<div>
  {% for product in collections.evidence.products %}
    <div>
      {{ product.title }}
    </div>
  {% endfor %}
</div>
```

Push to shopify.

```
shopify theme push
```

See edits rendered in the context of your dev store (open chrome dev tools.)

## Console (REPL)

Not super useful in my opinion.

[https://www.youtube.com/watch?v=oAwiznpqmzQ](https://www.youtube.com/watch?v=oAwiznpqmzQ)

```
shopify theme console
```
