

# sBTC-SnapMint - sBTC-SnapMint NFT Marketplace

sBTC-SnapMint is a Clarity smart contract built on the Stacks blockchain. It enables photographers to mint, list, and sell photo-based NFTs with built-in royalty mechanisms. Buyers can purchase listed NFTs using STX, and royalties are automatically distributed to the original creators.

---

## 🧩 Features

* **NFT Minting**
  Photographers can mint unique NFTs representing their photos, each with detailed metadata like camera settings, location, and title.

* **Royalties**
  The contract enforces on-chain royalty payments to photographers whenever their work is resold.

* **Listing & Sale**
  NFT owners can list their photos for sale, and buyers can purchase them with STX.

* **Ownership Tracking**
  Transfers of NFTs are tracked and enforced using built-in ownership checks.

---

## 📁 Data Structures

### ✅ Non-Fungible Token

```clojure
(define-non-fungible-token pixel-photo uint)
```

Each token is uniquely identified by a `uint` token ID.

---

### 🗃 Maps

* `photo-metadata`: Stores metadata for each photo
* `photo-listings`: Tracks NFTs listed for sale
* `royalty-settings`: Holds royalty info (percentage and recipient) per photo

---

### 🧠 Variables

* `last-token-id`: Stores the latest minted token ID

---

## ⚙️ Public Functions

### `mint-photo`

Mint a new photo NFT with metadata and royalty percentage.

**Inputs:**

* `title`: Photo title
* `camera-model`, `location`, `settings`: Photo metadata
* `royalty-percentage`: Percentage (e.g., 10 means 10%)

**Returns:** Token ID

---

### `transfer`

Transfer an NFT to another principal.

**Inputs:**

* `photo-id`: NFT ID
* `recipient`: Address of new owner

---

### `list-for-sale`

List an owned photo NFT for sale.

**Inputs:**

* `photo-id`: NFT ID
* `price`: Sale price in STX

---

### `buy-photo`

Buy a listed NFT. Automatically pays the seller and royalty recipient.

**Inputs:**

* `photo-id`: NFT ID

---

## 🔍 Read-Only Functions

### `get-photo-details`

Get metadata of a photo.

---

### `get-listing`

Fetch listing details of a photo (price, seller).

---

### `get-last-token-id`

Returns the most recently minted token ID.

---

## 🚫 Errors

| Code | Meaning                    |
| ---- | -------------------------- |
| 100  | Owner-only access required |
| 101  | Not the token owner        |
| 102  | Listing not found          |
| 103  | Insufficient payment       |

---

## ✅ Example Workflow

1. **Photographer** calls `mint-photo`
2. Mints NFT with metadata and royalty info
3. Calls `list-for-sale` to list it on the marketplace
4. **Buyer** calls `buy-photo`
5. STX is transferred to seller & royalty recipient
6. Ownership of NFT is transferred to buyer

---
