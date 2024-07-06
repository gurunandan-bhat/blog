+++
title = 'Describing Products With Variations'
date = 2024-07-05T22:41:49+05:30
draft = false
+++

I have been looking for clean ways to create a schema to describe products that come with different variations. The most common variations are color and size. Additionally some inventories might have products that vary with materials and sometimes sold with different accessories. Products sold in different variations come with two problems - the first is the choice of a database schema that describes such products, and second - designing the UI for such product pages. An overall design (database and UI) is one where these two components feed off each other.

The key entity to simplify the schema is the SKU (Stock Keeping Unit) each of which is identified by a unique combination of variables like size and color for example. A product has multiple SKUs and prices and stock quantity are attached to each SKU. Here is a simple schema to describe products and SKUs.
