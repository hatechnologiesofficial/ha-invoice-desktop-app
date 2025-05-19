# Electron Preload API Documentation

This README provides an overview of the APIs exposed by the Electron preload script for the **HA Invoice App**.

---

## 🌐 Global Interfaces

### `window.HaInvoiceApp`

This object exposes update event listeners from the main process:

#### Methods:

* `onUpdateAvailable(callback)`

  * Listens for `update_available` event.
  * **Usage**: `window.HaInvoiceApp.onUpdateAvailable((event) => { ... });`

* `onUpdateDownloaded(callback)`

  * Listens for `update_downloaded` event.
  * **Usage**: `window.HaInvoiceApp.onUpdateDownloaded((event) => { ... });`

---

### `window.HaApi`

This object exposes various application-level APIs that communicate with the main process via `ipcRenderer.invoke`.

#### 🔖 General

* `getVersion()`

  * Returns the current app version.

---

### 📁 Business Info

```js
window.HaApi["business-info"]
```

* `change(item)` – Create or update business info.
* `get(item)` – Retrieve business info.

---

### 🗂️ Categories

```js
window.HaApi.categories
```

* `create(item)` – Add a new category.
* `list(item)` – List all categories.
* `count(item)` – Count total categories.
* `update(id, item)` – Update a specific category.

---

### 🛍️ Products

```js
window.HaApi.products
```

* `create(item)` – Add a new product.
* `list(item)` – List all products.
* `count(item)` – Count total products.
* `delete(item)` – Delete a product.
* `update(id, item)` – Update a specific product.

---

### 🏷️ Brands

```js
window.HaApi.brands
```

* `create(item)` – Add a new brand.
* `list(item)` – List all brands.
* `count(item)` – Count total brands.
* `update(id, item)` – Update a specific brand.

---

### 👥 Customers

```js
window.HaApi.customers
```

* `create(item)` – Add a new customer.
* `list(item)` – List all customers.
* `count(item)` – Count total customers.
* `update(id, item)` – Update a specific customer.

---

### 📬 Addresses

```js
window.HaApi.addresses
```

* `create(item)` – Add a new address.
* `list(item)` – List all addresses.
* `count(item)` – Count total addresses.
* `delete(item)` – Delete a specific address.
* `update(id, item)` – Update a specific address.

---

### 📦 Inventories

```js
window.HaApi.inventories
```

* `create(item)` – Add new inventory batch.
* `list(item)` – List all inventory batches.
* `count(item)` – Count total inventories.

---

### 🧾 Invoices

```js
window.HaApi.invoices
```

* `create(item)`

  * Creates an invoice.
  * Automatically decreases inventory quantities for each item in `item.items`.

* `cancel(invoiceId)` – Cancel an invoice.

* `makePaid(invoiceId)` – Mark invoice as paid.

* `makeRefunded(invoiceId)` – Mark invoice as refunded.

* `list(item)` – List all invoices.

* `count(item)` – Count total invoices.

---

## 🔐 Security

These APIs are exposed securely using `contextBridge` and `ipcRenderer`, preventing direct access to Node.js from the renderer process.

---

## 📄 License

MIT License – (c) Ham Mim / HA Invoice App
