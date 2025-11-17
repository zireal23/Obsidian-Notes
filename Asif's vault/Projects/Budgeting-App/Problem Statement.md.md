Budgeting App: Problem Statement & High-Level Design

A simple, sleek, and cute budgeting app that treats every purchase as a rich data object — with full metadata — and supports both composite items and linked purchases for powerful, flexible tracking.

Problem Statement

Most budgeting apps force users into rigid categories (e.g., "Shopping", "Electronics") and treat spending as flat transactions. They lack the ability to:

- Track detailed attributes like store, payment method, card used, or online/offline status.
    
- Group items into composite purchases (e.g., "Work Setup: Laptop + Case + Mouse") that behave like single items.
    
- Link independent purchases across time (e.g., "Kitchen Renovation" project) without merging them.
    

Spreadsheets can handle this, but they’re not mobile-friendly, structured, or joyful to use.

There is a need for a lightweight, personal finance journal that:

- Is simple and cute — not cluttered like a financial dashboard.
    
- Supports rich item attributes and deep filtering.
    
- Allows users to group items into composites or link purchases across time.
    
- Enables custom analytics with charts on any attribute combination.
    
- Works offline-first, with data export for backup and trust.
    

This app should feel like a tool that understands how real people buy things — not just how much they spend, but why, where, and with what.

Core Concepts

Item  
A single purchased product with detailed metadata.

``` json
type Item = {  
	id: string;  
	name: string;  
	price: number;  
	date: Date;  
	store: string;  
	isOnline: boolean;  
	paymentMethod: 'cash' | 'card';  
	cardUsed?: string;  
	category: string;  
	notes?: string;  
};
```


Composite Item  
A group of items merged into a single purchase. Behaves like an Item in filtering and analytics.

```json
type CompositeItem = {  
	id: string;  
	name: string;  
	items: Item[];  
	date: Date;  
	totalPrice: number;  
	paymentMethod: 'cash' | 'card';  
	cardUsed?: string;  
};
```

Linked Purchase (Link Group)  
A non-destructive way to connect existing purchases (individual or composite) based on shared context (e.g., project, event).

```json
type LinkGroup = {  
	id: string;  
	name: string;  
	description?: string;  
	purchaseIds: string[];  
	createdAt: Date;  
	color?: string;  
	icon?: string;  
};
```
Key Features

- Add Item with full metadata (store, card, online/offline, etc.)
    
- Create Composite — group items into a single purchase
    
- Link Purchases — connect items across time (e.g., for projects or events)
    
- Rich Search & Filter
    
    - Filter by date, price, store, card, payment method
        
    - Sort by date, price, number of items
        
    - Filter by composite or linked group
        
- Analytics Dashboard
    
    - Charts: bar, pie, line — customizable by any attribute
        
    - Example: “Show total spend by card for online purchases at Amazon in Q3”
        
- Cute, Minimal UI
    
    - Soft colors, rounded corners, subtle animations
        
    - Emojis and color-coded tags for personalization
        
    - No clutter — only essential actions visible
        
- Offline-First & Data Export
    
    - Local storage (e.g., SQLite)
        
    - Export all data as CSV/JSON
        

App Structure (File-Based Routing)

app/  
├── index.tsx  
├── items/  
│ ├── index.tsx  
│ └── [id].tsx  
├── composite/  
│ ├── index.tsx  
│ └── create.tsx  
├── links/  
│ ├── index.tsx  
│ └── create.tsx  
├── analytics/  
│ ├── index.tsx  
│ └── chart.tsx  
├── search.tsx  
└── settings.tsx

Future Enhancements

- Auto-suggest links: “You bought ‘Mouse’ after ‘Laptop’ — link them?”
    
- Monthly summary cards with trends and cute visuals
    
- Dark mode with warm neutrals
    
- Quick-add via home screen shortcut
    
- Tagging system for custom filters (e.g., #gift, #urgent)
    

Design Philosophy

“Simple, sleek, and cute” — but powerful under the hood.  
Not a financial dashboard.  
A personal spending journal that feels joyful to use.