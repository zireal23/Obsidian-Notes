## 🧱 Low-Level Design (LLD) Overview

The app follows a **layered architecture**:

```json
UI Layer (Components) 
	↓ 
Business Logic & State (Hooks, Services) 
	↓ 
Data Layer (Storage, Database) 
	↓ 
Utilities (Types, Helpers)
```

Each layer is isolated, testable, and reusable.

---

## 📂 Folder Structure (with LLD Context)



---

## 🔌 Data Layer (Low-Level Details)
	app/
├── lib/               → Shared logic, types, and utilities
│   ├── types.ts       → TypeScript interfaces (Item, CompositeItem, LinkGroup)
│   ├── database.ts    → SQLite setup and CRUD operations
│   ├── storage.ts     → High-level service layer (e.g., addItem, createComposite)
│   └── utils/         → Helper functions (formatDate, sumPrices, etc.)
│
├── components/        → Reusable UI components
│   ├── ItemCard.tsx   → Displays an item or composite
│   ├── AddButton.tsx  → Cute floating button
│   └── ChartView.tsx  → Wrapper for charts
│
├── items/             → Screens for individual items
│   ├── index.tsx      → List of all items
│   └── add.tsx        → Form to add a new item
│
├── composite/         → Composite item management
│   ├── index.tsx      → List of composites
│   └── create.tsx     → Select items → group into composite
│
├── links/             → Linking purchases
│   ├── index.tsx      → List of link groups
│   └── create.tsx     → Create a group and add purchases
│
├── analytics/         → Data visualization
│   ├── index.tsx      → Dashboard
│   └── chart.tsx      → Customizable chart builder
│
├── search.tsx         → Rich search with filters (date, price, store, card, etc.)
├── settings.tsx       → Export data, dark mode, app info
└── _layout.tsx        → Root layout (theme, fonts, providers)


## 1. **Database: `expo-sqlite`**

- Local, persistent, offline-first.
    
- Stores all items, composites, and link groups.
    
- Schema:
    

	```SQL
	-- Individual items
CREATE TABLE items (
  id TEXT PRIMARY KEY,
  name TEXT,
  price REAL,
  date TEXT,
  store TEXT,
  isOnline INTEGER,
  paymentMethod TEXT,
  cardUsed TEXT,
  category TEXT,
  notes TEXT
);

-- Composite items
CREATE TABLE composite_items (
  id TEXT PRIMARY KEY,
  name TEXT,
  items TEXT, -- JSON array of item IDs
  date TEXT,
  totalPrice REAL,
  paymentMethod TEXT,
  cardUsed TEXT
);

-- Linked purchase groups
CREATE TABLE link_groups (
  id TEXT PRIMARY KEY,
  name TEXT,
  description TEXT,
  purchaseIds TEXT, -- JSON array of item/composite IDs
  createdAt TEXT,
  color TEXT,
  icon TEXT
);

	```



> Use `JSON.stringify` and `JSON.parse` to store arrays.

## 2. **`lib/database.ts`**

- Handles raw SQL queries.
    
- Exposes functions like:
    
    - `getAllItems()`
        
    - `getItemById(id)`
        
    - `insertItem(item)`
        
    - `updateItem(id, item)`
        
    - `deleteItem(id)`
        

## 3. **`lib/storage.ts` (Service Layer)**

- Higher-level logic that uses `database.ts`.
    
- Example: `createComposite(items: Item[])` → calculates total, sets date, saves to DB.
    
- Ensures business rules are enforced (e.g., composite must have at least 2 items).
    
- Handles relationships (e.g., when deleting an item, remove it from composites/links).
    

---

## 🧩 Business Logic & State

## 1. **Custom Hooks (in `lib/hooks/`)**

- `useItems()`: Fetches and caches items from DB.
    
- `useComposites()`: Gets all composite items.
    
- `useLinkGroups()`: Loads link groups.
    
- Uses React Query or simple `useState + useEffect` for now.
    

## 2. **State Management**

- No need for Redux. Use:
    
    - React Context (e.g., `AppContext` for theme, user prefs).
        
    - Local state (`useState`) for form inputs.
        
    - Custom hooks for shared logic.
        

---

## 🖼️ UI Layer (Components)

## 1. **Reusable Components**

- `ItemCard`: Displays an item or composite with name, price, store, date.
    
- `Tag`: Small label for cardUsed, category, or link group color.
    
- `SearchBar`: With dropdowns for filters (date range, card, store).
    
- `ChartView`: Wrapper around `victory-native` — accepts data and type (bar, pie).
    

## 2. **Navigation**

- `expo-router` uses file-based routing.
    
- Each screen is a `.tsx` file under `app/`.
    
- Use `Link` and `router.push()` for navigation.
    

---

## 🔄 Key Workflows (LLD in Action)

## 1. **Add Item**

1. User fills form in `items/add.tsx`.
    
2. On save → `storage.ts` → `database.ts` inserts into `items` table.
    
3. Redirect to home.
    

## 2. **Create Composite**

1. User selects multiple items in `composite/create.tsx`.
    
2. App calculates `totalPrice`, picks latest `date`.
    
3. `storage.createComposite()` saves to `composite_items` table.
    
4. Composite appears in analytics like a regular purchase.
    

## 3. **Link Purchases**

1. User creates a link group in `links/create.tsx`.
    
2. Selects any items or composites.
    
3. `storage.createLinkGroup()` saves to `link_groups` with JSON list of IDs.
    
4. Later, filter analytics by this group.
    

## 4. **Analytics**

1. User selects filters (e.g., cardUsed = "HDFC", date = last month).
    
2. `useFilteredPurchases(filters)` queries DB for items + composites.
    
3. Renders chart using `victory-native`.
    

---

## 🧪 Testing & Extensibility

- **Unit Tests**: Test `utils/formatDate`, `storage.createComposite`.
    
- **Future-Proof**:
    
    - Add `tags` field later without schema change (store as JSON).
        
    - Export to CSV: query all data → `Papaparse` to generate CSV.
        
    - Sync: later add cloud backup (e.g., Firebase) — isolated in `lib/sync.ts`.
        

---

## ✅ Summary

|Layer|Responsibility|Tools|
|---|---|---|
|**UI**|Screens, forms, charts|React Native, Expo|
|**Business Logic**|Rules, flows, state|Custom hooks, Context|
|**Data**|Storage, queries|`expo-sqlite`, `lib/storage.ts`|
|**Types & Utils**|Type safety, helpers|TypeScript, `lib/utils/`|

You now have a **clear, scalable LLD** that supports:

- Individual items
    
- Composite items
    
- Linked purchases
    
- Rich filtering and analytics
    
- Cute, responsive UI