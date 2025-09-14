Here’s a **Developer’s Checklist** tailored for your space trading simulator so you (or future‑you) can make changes confidently without breaking the game’s logic or UI.  
Think of it as your “flight manual” for safe modifications 🚀  

---

## 🛠 Space Trading Simulator – Developer’s Checklist

### 1. **Data Management**
- **Keep goods data external**  
  Store `COMMON_GOODS` and `TRADE_GOODS` in CSV or JSON files. Load them at runtime so you can tweak prices, DMs, and quantities without touching the core logic.
- **Maintain consistent field names**  
  Always use the same property names (`name`, `base`, `qty`, `dm1`, `dm2`) so functions don’t break.
- **Validate new entries**  
  Check that dice notation (`"10D"`, `"2D"`) is valid and that DMs follow the `XX+N` format.

---

### 2. **Game Logic**
- **Centralise constants**  
  Keep `PRICE_FACTOR`, broker DMs/commissions, and trade code lists in one config section.
- **Clamp values**  
  Ensure price rolls are always clamped to the min/max (currently 2–16).
- **Test modifiers**  
  When adding new trade codes or brokers, verify that DMs apply correctly and commission is calculated in the manifest.

---

### 3. **UI Structure**
- **Separate concerns**  
  Keep HTML structure clean and minimal; let JavaScript handle dynamic rendering.
- **Use semantic IDs/classes**  
  IDs like `availableList`, `manifestBody` make it easy to find and update elements.
- **Responsive design**  
  Test on narrow screens; adjust CSS grid/flex layouts if adding new UI elements.

---

### 4. **Extending Features**
When adding new mechanics:
- **Selling goods** → Mirror the purchase logic but use `saleDMs` and a different factor table.
- **Cargo capacity** → Track a `maxTons` variable and prevent over‑selection.
- **Multiple worlds** → Store `market` as an array of markets keyed by system name.
- **Save/Load** → Use `localStorage` to persist manifest and settings between sessions.

---

### 5. **Testing & Debugging**
- **Add a debug mode**  
  Show dice rolls, applied DMs, and factor multipliers in the UI for balancing.
- **Test edge cases**  
  - No trade codes selected  
  - All trade codes selected  
  - No broker vs. highest broker  
  - Goods with 0 available tons
- **Check calculations**  
  Verify totals match manual calculations, especially with commission applied.

---

### 6. **Version Control**
- **Commit often**  
  Use Git (or similar) to track changes. Commit after each working feature.
- **Tag stable builds**  
  Mark versions you know are working so you can roll back if needed.
- **Document changes**  
  Keep a short changelog of what was added, removed, or fixed.

---

### 7. **Performance**
- **Avoid unnecessary re‑renders**  
  Only update DOM elements that change.
- **Optimise loops**  
  If the goods list grows large, consider virtualised rendering.
- **Minimise inline styles**  
  Keep styling in CSS for easier theme changes.

---

💡 **Pro tip:** When you upload the script to me in the future, include:
1. The **full current version** (so I see all your latest tweaks).
2. A **clear list of changes** you want, in priority order.
3. Any **new rules or mechanics** you’ve added since we last worked on it.

---
