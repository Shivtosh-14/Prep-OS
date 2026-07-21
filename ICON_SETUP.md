# Study Assistant Icon Setup

## 📁 How to Add Your Custom Icon

### Option 1: Replace the existing SVG file
1. **Replace the file**: `study-assistant-icon.svg` with your own icon
2. **Keep the same filename**: `study-assistant-icon.svg`
3. **Recommended size**: 24x24 pixels (or any square aspect ratio)
4. **Supported formats**: SVG, PNG, JPG, GIF, WebP

### Option 2: Use a different filename
1. **Update the HTML**: Change the `src` attribute in `prototype.html` line 389:
   ```html
   <img src="your-icon-name.svg" alt="Study Assistant Icon" class="chat-icon" id="studyAssistantIcon">
   ```

## 🎨 Icon Requirements

### Size & Resolution
- **Fixed display size**: 24x24 pixels (automatically scaled)
- **Aspect ratio**: Square (1:1) recommended
- **Resolution**: Any resolution supported (automatically scaled to fit)
- **Object-fit**: `contain` ensures the entire icon is visible

### Styling
- **Background**: Transparent recommended
- **Colors**: Will be displayed as-is
- **Border radius**: 4px applied automatically
- **Hover effect**: Slight opacity reduction on hover

## 🔧 Technical Details

### CSS Properties Applied
```css
.chat-icon {
    width: 24px;
    height: 24px;
    object-fit: contain;        /* Scales to fit within bounds */
    flex-shrink: 0;            /* Prevents shrinking */
    border-radius: 4px;        /* Rounded corners */
    transition: opacity 0.2s ease;
}
```

### Fallback System
- **If icon fails to load**: Shows a 📚 emoji in a circular background
- **Automatic detection**: JavaScript handles load errors
- **Graceful degradation**: No broken image icons

### Responsive Design
- **Flex layout**: Icon stays aligned with title
- **Gap spacing**: 10px between icon and text
- **Container**: Flexbox ensures proper alignment

## 🚀 Quick Start

1. **Drop your icon file** into the project folder
2. **Name it** `study-assistant-icon.svg` (or update the HTML)
3. **Refresh the page** - your icon will appear!
4. **If it doesn't work**: Check browser console for errors

## 📝 Notes

- The icon is only visible in `prototype.html`
- Other course pages don't have this icon (as requested)
- The icon appears in the Study Assistant header
- Clicking the header still toggles the chat interface
