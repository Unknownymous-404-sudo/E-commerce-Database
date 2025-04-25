# E-commerce Database Schema

This SQL file defines the schema for an e-commerce database. The database is designed to manage products, their attributes, variations, and related entities such as brands, categories, and images.

## Database Structure

### 1. Database
- **Name**: `E-commerce`
- The database is created if it does not already exist.

### 2. Tables

#### Brand Table
- **Table Name**: `brand`
- **Columns**:
  - `id`: Primary key, auto-incremented.
  - `name`: Unique name of the brand.

#### Product Category Table
- **Table Name**: `product_category`
- **Columns**:
  - `id`: Primary key, auto-incremented.
  - `category_id`: Identifier for the product category.

#### Color Table
- **Table Name**: `color`
- **Columns**:
  - `id`: Primary key, auto-incremented.
  - `name`: Name of the color.

#### Size Category Table
- **Table Name**: `size_category`
- **Columns**:
  - `id`: Primary key, auto-incremented.
  - `size_option`: Name of the size category.

#### Attribute Category Table
- **Table Name**: `attribute_category`
- **Columns**:
  - `id`: Primary key, auto-incremented.
  - `name`: Name of the attribute category.

#### Attribute Type Table
- **Table Name**: `attribute_type`
- **Columns**:
  - `id`: Primary key, auto-incremented.
  - `name`: Name of the attribute type.
  - `category_id`: Foreign key referencing `attribute_category(id)`.

#### Product Table
- **Table Name**: `product`
- **Columns**:
  - `id`: Primary key, auto-incremented.
  - `name`: Name of the product.
  - `brand_id`: Foreign key referencing `brand(id)`.
  - `category_id`: Foreign key referencing `product_category(id)`.
  - `base_price`: Base price of the product.

#### Product Image Table
- **Table Name**: `product_image`
- **Columns**:
  - `id`: Primary key, auto-incremented.
  - `product_id`: Foreign key referencing `product(id)`.
  - `image_uri`: URI of the product image.

#### Size Option Table
- **Table Name**: `size_option`
- **Columns**:
  - `id`: Primary key, auto-incremented.
  - `size_category_id`: Foreign key referencing `size_category(id)`.
  - `value`: Value of the size option.

#### Product Variation Table
- **Table Name**: `product_variation`
- **Columns**:
  - `id`: Primary key, auto-incremented.
  - `product_id`: Foreign key referencing `product(id)`.
  - `size_id`: Foreign key referencing `size_option(id)`.
  - `color_id`: Foreign key referencing `color(id)`.

#### Product Item Table
- **Table Name**: `product_item`
- **Columns**:
  - `id`: Primary key, auto-incremented.
  - `variation_id`: Foreign key referencing `product_variation(id)`.
  - `sku`: Unique stock-keeping unit.
  - `price`: Price of the product item.

#### Product Attribute Table
- **Table Name**: `product_attribute`
- **Columns**:
  - `id`: Primary key, auto-incremented.
  - `product_id`: Foreign key referencing `product(id)`.
  - `type_id`: Foreign key referencing `attribute_type(id)`.
  - `value`: Value of the attribute.

## Usage
1. Run the SQL file in your MySQL database to create the schema.
2. Use the tables to store and manage data for an e-commerce application.

## Notes
- Foreign key constraints ensure data integrity between related tables.
- The schema is designed to be extensible for additional features like promotions, orders, and user management.

## License
This schema is provided as-is for educational or development purposes.