# DRIP Store — E-commerce Storefront

The customer-facing storefront for **DRIP**, an online fashion store. Shoppers can browse
and search the catalogue, keep a wishlist, manage a cart, and check out with **M-Pesa**. An
admin page handles the catalogue and orders. It is built with plain HTML, CSS and
JavaScript on top of the [DRIP REST API](https://github.com/ray100-art/DRIP---ECOMMERCE-BACKEND).

## Pages

| Page | What it does |
|---|---|
| `index.html` | Landing page |
| `Shop.html`, `Products.html` | Browse the catalogue by category and brand |
| `Product.html` | Product detail with price, sale price, rating and stock |
| `Search.html` | Search across products |
| `Wishlist.html` | Saved items |
| `Checkout.html` | Cart, shipping, totals and M-Pesa STK Push payment |
| `Orders.html` | A customer's order history |
| `Profile.html` | Account details |
| `admin.html` | Manage products and order status |

## How it works

- **API client.** Pages call the backend at `http://localhost:8080/api` for products,
  authentication and orders.
- **Authentication.** The JWT returned at login is kept in `sessionStorage`. `auth.js`
  reads it to update the navbar, and checkout and order pages send it as a Bearer token.

- **Cart.** Kept in `localStorage` (`drip-cart`), so it survives page reloads.
- **Payments.** Checkout sends the customer's phone number and the amount to the backend,
  which triggers an M-Pesa STK Push prompt on the phone.

## Tech stack

HTML5, CSS3, vanilla JavaScript (ES6+), browser `localStorage`, and the Fetch API. Two
small Python scripts, `download_images.py` and `download-images.py`, fetch the product
imagery into `images/`.

## Running locally

1. Start the [backend](https://github.com/ray100-art/DRIP---ECOMMERCE-BACKEND) on port 8080.
2. Serve this folder with any static server, for example:
   ```bash
   python -m http.server 5500
   ```
   or VS Code's Live Server.
3. Open http://localhost:5500.

`test.http` contains ready-made API requests (register, login, and so on) for the VS Code
REST Client extension.

## License

[Apache 2.0](LICENSE)
