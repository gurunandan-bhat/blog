+++
title = 'Describing Products With Variations'
date = 2024-07-05T22:41:49+05:30
draft = false
+++

I have been looking for clean ways to create a schema to describe products that come with different variations. The most common variations are color and size. Additionally some inventories might have products that vary with materials and sometimes sold with different accessories. Products sold in different variations come with two problems - the first is the choice of a database schema that describes such products, and second - designing the UI for such product pages. An overall design (database and UI) is one where these two components feed off each other.

The key entity to simplify the schema is the SKU (Stock Keeping Unit) each of which is identified by a unique combination of variables like size and color for example. A product has multiple SKUs and, each SKU has a price and stock quantity attached. Here is a simple schema to describe products and SKUs.

{{< highlight sql "linenos=tables,style=solarized-light" >}}

CREATE TABLE `product` (
`iProdID` int unsigned NOT NULL AUTO_INCREMENT,
`vProdName` varchar(128) NOT NULL,
PRIMARY KEY (`iProdID`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci

CREATE TABLE `sku` (
`iSKUID` int unsigned NOT NULL AUTO_INCREMENT,
`iProdID` int unsigned NOT NULL,
`fPrice` decimal(16,2) NOT NULL,
`iStock` int unsigned NOT NULL DEFAULT '0',
PRIMARY KEY (`iSKUID`),
UNIQUE KEY `unique_sku_product` (`iSKUID`,`iProdID`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci
{{< /highlight >}}
