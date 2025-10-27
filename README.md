# liquidity

Utilities for managing Shopify Liquid themes.

admin.shopify.com > Apps > Theme Access > Create password (check email)

```
set -a; source .env; set +a
export $(cat .env | xargs)

shopify theme init liquidity-theme
cd liquidity-theme
```

## Console (REPL)

```
shopify theme console
```



```

shopify theme list
```