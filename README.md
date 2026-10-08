# Shopee Datasets and Data Quality Guides by Easy Data

Explore historical Shopee product listings, understand the fields, and build a careful first analysis. Maintained by [Easy Data](https://easydata.io.vn/), the dataset publisher.

**Start here:** [View the Shopee sample and documentation](https://easydata.io.vn/data-sample/free-shopee-dataset/?utm_source=github&utm_medium=referral&utm_campaign=shopee_dataset&utm_content=readme_sample).

## Choose a dataset

| Collection | Recorded coverage | Download and documentation |
| --- | --- | --- |
| Thailand starter sample | January 31, 2025; 540 unique shop/item pairs; 151 shops; 23 fields; THB | [Easy Data sample page](https://easydata.io.vn/data-sample/free-shopee-dataset/) · [Kaggle CSV and Data Card](https://www.kaggle.com/datasets/johnphamed/shopee-thailand-diaper-listings-january-2025) |
| Six-market diaper collection | November 18, 2025 crawl date; 24,896 rows; 19,686 unique domain/shop/product keys; six Excel workbooks | [Kaggle workbooks and Data Card](https://www.kaggle.com/datasets/johnphamed/shopee-diaper-listings-six-markets-november-2025) · [Original Drive folder](https://drive.google.com/drive/folders/1-ynfBFXTlHJ6S4Hq52QEjfs0xSjga-N-) |
| Thailand nine-category collection | May 31, 2025; 19,072 unique shop/item pairs; 5,943 shops; 23 fields; THB | [Kaggle workbooks and Data Card](https://www.kaggle.com/datasets/johnphamed/shopee-thailand-nine-categories-may-2025) · [Original Drive folder](https://drive.google.com/drive/folders/1HK5PrWfq2gg1ZWggAcocLTbPqqCUqRyq) |
| Singapore collection views | August 18, 2025; 2,996 identifiable observations; 2,727 distinct shop/product pairs; 968 shops; SGD | [Kaggle workbooks and Data Card](https://www.kaggle.com/datasets/johnphamed/shopee-singapore-listing-samples-august-2025) · [Original Drive folder](https://drive.google.com/drive/folders/14f9Uj9D5uG7gEw2r6YEnUYGz7EC1HueD) |
| Thailand March nine-category collection | March 31, 2025; 4,299 unique shop/item pairs; 1,400 shops; 23 fields; THB | [Kaggle workbooks and Data Card](https://www.kaggle.com/datasets/johnphamed/shopee-thailand-nine-categories-march-2025) · [Original Drive folder](https://drive.google.com/drive/folders/1uo06N2asg6gJn1xrgfyQmDr4qOXpRPwT) |

Files are hosted at the linked sources. This repository provides a guide to choosing and using them. These are separate collections with different schemas and sampling coverage. The May collection covers mobile/tablets, pet food, carbonated drinks/tonics, bath/shower, face masks, sunscreen, shampoo/conditioner, diapers and milk formula. Do not assume the collections form a comparable time series.

## March and May Thailand samples

The [March 2025 collection](https://www.kaggle.com/datasets/johnphamed/shopee-thailand-nine-categories-march-2025) contains 4,299 listings across the same nine category labels, compared with 19,072 in May. There are 2,966 shared shopId/itemId pairs and 1,333 March pairs absent from the May sample. Sampling differs: absence does not prove delisting, and row-count changes do not measure market growth. Compare only matched listings after checking variants and pack sizes.

March quality notes: normalize mixed Excel/text date values; 772 brands are blank; 1,163 reference prices are zero, including every Milk Formula row; five rows have sold greater than historySold. The Data Card explains how to preserve raw values and handle these checks.

## Singapore store, keyword and category samples

The August collection preserves three original workbooks: Category (998 identifiable observations), Keyword (999) and Store (999). Read the [Singapore Data Card](https://www.kaggle.com/datasets/johnphamed/shopee-singapore-listing-samples-august-2025) for overlap counts, exact fields and a practical analysis sequence.

**Quality note:** the Keyword workbook also contains 11,862 incomplete rows without listing identifiers; these are excluded from the 2,996 observation count. Do not forward-fill their identifiers. Store data includes 312 reference prices recorded as -1 and 39 rows with parse times earlier than crawl times. Preserve originals, filter missing keys, and retain query/category/store context when handling repeated listings.

## Related Australian retail samples

[Australian Retail Product Samples, February 2026](https://www.kaggle.com/datasets/johnphamed/australian-retail-product-samples-february-2026) contains 178 records: Amazon Australia (72), Chemist Warehouse (20), Coles (55) and Woolworths (31). These are separate retail sources, not Shopee data.

Use the four workbooks to practice schema mapping and manually reviewed product matching. Fields vary from 16 to 31 columns. Amazon records are dated February 5, 2026; the others February 1. The files have no explicit currency column or store/postcode context, so verify those before price comparisons. Read the Data Card for retailer-specific field meanings and limits.

## Six-market coverage

| Market | Currency | Rows | Unique listing keys | Shops |
| --- | --- | ---: | ---: | ---: |
| Indonesia | IDR | 8,851 | 7,233 | 1,938 |
| Malaysia | MYR | 2,328 | 1,520 | 481 |
| Philippines | PHP | 4,265 | 3,644 | 722 |
| Singapore | SGD | 1,373 | 1,076 | 338 |
| Thailand | THB | 2,176 | 1,257 | 285 |
| Vietnam | VND | 5,903 | 4,956 | 1,017 |

Counts were checked in the supplied workbooks. A listing key combines domain, shop_id and product_id. Repeated keys remain in the source, so rows are not unique products. Each workbook contains a Multi-Modal Comparison sheet. Indonesia has 46 columns; the other markets have 47, including discount.

The recorded crawl date is November 18, 2025 and the recorded parse date is December 11, 2025. Upload dates do not indicate fresh collection. Time zones are not specified.

## Getting started

1. Choose the small Thailand CSV for an introductory Excel or Power BI exercise. Choose the six-market workbooks for duplicate-key checks and image/text annotation comparisons, or the August Singapore files for comparing collection views.
2. Keep identifiers as text. The starter CSV and March/May Thailand workbooks use shopId and itemId; the November and August Singapore workbooks use domain, shop_id and product_id.
3. Check missing values and repeated keys before aggregating. Inspect source_url filters and conflicting rows before deciding which observation to retain.
4. Keep currencies separate. Normalize pack quantities and variants before comparing unit prices.
5. Preserve the original brand field alongside the image-based and text-based annotations. Review disagreements manually. Model confidence is not measured accuracy.
6. Split classification datasets by listing key to prevent repeated listings appearing in both training and evaluation sets.

For a step-by-step introductory walkthrough, see the [Shopee Thailand data quality notebook](https://www.kaggle.com/code/johnphamed/shopee-thailand-dataset-data-quality-guide).

## Useful first outputs

- A table of row counts, unique listing keys and missing identifiers by market.
- Missing-value rates for the fields used in a dashboard.
- A review queue for image/text brand disagreements.
- Price distributions within one currency, with variant and pack-size limitations stated.

## Interpretation limits

These historical samples do not establish current prices, complete category coverage, market share or growth. Source URLs in the six-market files include price filters and sales sorting. Country row counts are not a measure of country demand.

Source sales counters, including monthly_sold and sold, are not audited transactions. A field name does not prove a complete calendar-month reporting window. Multiplying a counter by a listing price does not establish verified revenue.

Model-generated categories, brands and explanations can be wrong. Matching image and text labels do not make them ground truth. Review the relevant Data Card before using the data in a report.

## Need a dataset for your project?

Visit [Easy Data for marketplace data enquiries](https://easydata.io.vn/?utm_source=github&utm_medium=referral&utm_campaign=shopee_dataset&utm_content=readme_enquiry). Describe the marketplace, countries, categories, required fields and collection frequency so the scope can be discussed.

## Attribution and corrections

Cite Easy Data and the specific dataset release you used. Reuse licensing is not specified for these datasets; public access does not establish unrestricted reuse rights. This project is not endorsed by Shopee.

Open a repository issue for documentation corrections and include the relevant field or example without private customer information.
