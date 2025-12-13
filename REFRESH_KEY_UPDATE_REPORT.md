# Refresh Key Update Report

**Date:** 2025-12-13
**Task:** Update all pre-aggregation refresh_key.every values to 365 days

## Summary

- **Total Files Modified:** 9
- **Total Pre-aggregations Updated:** 10
- **Status:** ✅ Complete - All changes successful

## Files Modified

### 1. customers.yml
- **Pre-aggregation:** `customer_ltv`
- **Old Value:** `every: 6 hours`
- **New Value:** `every: 365 days`
- **Status:** ✅ Updated

### 2. inventory_levels.yml
- **Pre-aggregation:** `inventory_snapshot`
- **Old Value:** `every: 30 minutes`
- **New Value:** `every: 365 days`
- **Status:** ✅ Updated

### 3. order_discount_applications.yml
- **Pre-aggregation:** `discounts_by_product`
- **Old Value:** `every: 1 hour`
- **New Value:** `every: 365 days`
- **Status:** ✅ Updated

### 4. order_fulfillments.yml
- **Pre-aggregation:** `fulfillments_daily`
- **Old Value:** `every: 1 hour`
- **New Value:** `every: 365 days`
- **Status:** ✅ Updated

### 5. order_line_items.yml
- **Pre-aggregation 1:** `product_daily`
- **Old Value:** `every: 1 hour`
- **New Value:** `every: 365 days`
- **Status:** ✅ Updated

- **Pre-aggregation 2:** `orders_rollup`
- **Old Value:** `every: 1 hour`
- **New Value:** `every: 365 days`
- **Status:** ✅ Updated

### 6. order_refunds.yml
- **Pre-aggregation:** `refunds_daily`
- **Old Value:** `every: 1 hour`
- **New Value:** `every: 365 days`
- **Status:** ✅ Updated

### 7. orders.yml
- **Pre-aggregation:** `orders_daily`
- **Old Value:** `every: 1 hour`
- **New Value:** `every: 365 days`
- **Status:** ✅ Updated

### 8. product_variants.yml
- **Pre-aggregation:** `variant_summary`
- **Old Value:** `every: 2 hours`
- **New Value:** `every: 365 days`
- **Status:** ✅ Updated

### 9. products.yml
- **Pre-aggregation:** `product_summary`
- **Old Value:** `every: 2 hours`
- **New Value:** `every: 365 days`
- **Status:** ✅ Updated

## Original Refresh Intervals Distribution

- **30 minutes:** 1 pre-aggregation (inventory_snapshot)
- **1 hour:** 6 pre-aggregations (order_discount_applications, order_fulfillments, order_line_items x2, order_refunds, orders)
- **2 hours:** 2 pre-aggregations (product_variants, products)
- **6 hours:** 1 pre-aggregation (customers)

## Post-Update Status

All 10 pre-aggregations now use:
```yaml
refresh_key:
  every: 365 days
```

## Impact

With automatic refresh disabled (set to 365 days), pre-aggregations will:
- No longer refresh automatically
- Require manual refresh via Cube API or CLI
- Reduce server load from automatic refresh operations
- Maintain existing pre-aggregated data until manually refreshed

## Verification

All edits completed successfully with exact indentation and formatting preserved. No issues encountered during the update process.

## Next Steps

1. Deploy updated YAML files to Cube server
2. Restart Cube service to load new configuration
3. Set up manual refresh schedule if needed
4. Monitor pre-aggregation data freshness
