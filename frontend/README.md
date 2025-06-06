# File Tree Timeline Visualizer - Frontend

Interactive Three.js sunburst visualization for exploring file system changes over time.

## Features

- **3D Sunburst Visualization**: Radial tree representation with time as depth
- **Interactive Timeline**: Scrub through scan history with smooth animations
- **Mouse Interaction**: Hover for detailed file/folder information
- **Camera Controls**: Orbit, zoom, and pan with smooth damping
- **Color Coding**: Visual distinction between file types
- **Real-time Info**: Live statistics and scan metadata
- **Responsive Design**: Adapts to different screen sizes

## Usage

### Local Development

1. **Serve the files** using any local server:
   ```bash
   # Using Python 3
   python -m http.server 8000
   
   # Using Node.js (if you have it)
   npx serve .
   
   # Using Live Server (VS Code extension)
   # Right-click index.html and select "Open with Live Server"
   ```

2. **Place data file**: Ensure `file_tree_data.json` is in the same directory as `index.html`

3. **Open browser**: Navigate to `http://localhost:8000`

### Data Requirements

The frontend expects JSON data in this format:
```json
{
  "metadata": {
    "generated_at": "2024-01-01T12:00:00",
    "total_scans": 5
  },
  "timeline": [
    {
      "scan_id": 0,
      "timestamp": "2024-01-01T11:30:00",
      "total_files": 150,
      "total_size": 2048576,
      "tree_data": {
        "name": "root",
        "type": "folder",
        "size": 2048576,
        "color": "#34495e",
        "children": [...]
      }
    }
  ]
}
```

## Interface Components

### Control Panel
- **Timeline Slider**: Navigate between different scans
- **Play/Pause**: Automatic timeline progression
- **Reset**: Return to first scan
- **Current Scan**: Shows position in timeline

### Info Panel
- **Timestamp**: When the scan was performed
- **Total Files**: Number of files in current scan
- **Total Size**: Combined size of all files
- **Scan Duration**: Time taken to complete scan

### Hover Panel
- **File Details**: Name, size, MIME type, hash
- **Folder Details**: Name, size, file count
- **Real-time Updates**: Follows mouse movement

### Legend
- **Color Guide**: File type identification
- **Visual Reference**: Quick type recognition

## Visualization Details

### Sunburst Structure
- **Center**: Root directory
- **Rings**: Nested folders and files
- **Segments**: Individual files/folders sized by content
- **Depth**: Timeline progression (Z-axis)

### Color Coding
- **JavaScript**: Yellow (`#f7df1e`)
- **Python**: Blue (`#3776ab`)
- **HTML**: Orange (`#e34c26`)
- **CSS**: Blue (`#1572b6`)
- **Folders**: Dark blue-gray (`#34495e`)
- **Other Files**: Light gray (`#bdc3c7`)

### Interactions
- **Mouse Hover**: Highlight and show details
- **Orbit Controls**: Click and drag to rotate
- **Zoom**: Mouse wheel or pinch
- **Auto-rotation**: Gentle continuous movement

## Performance

### Optimization Features
- **Efficient Rendering**: Three.js WebGL acceleration
- **Level of Detail**: Adaptive geometry complexity
- **Memory Management**: Cleanup of unused objects
- **Smooth Animations**: 60 FPS targeting

### Browser Requirements
- **Modern Browser**: Chrome 60+, Firefox 55+, Safari 11+
- **WebGL Support**: Required for 3D rendering
- **ES6 Support**: Modern JavaScript features
- **Local Storage**: For preferences (future feature)

## Customization

### Styling
All visual elements can be customized via CSS:
- Panel backgrounds and blur effects
- Color schemes and gradients
- Animation timings and easing
- Typography and spacing

### Behavior
JavaScript configuration options:
- Auto-rotation speed
- Timeline playback speed
- Camera movement sensitivity
- Hover response timing

## Troubleshooting

### Common Issues

**"Failed to load data"**
- Ensure `file_tree_data.json` exists
- Check browser console for network errors
- Verify JSON format validity

**"No timeline data available"**
- Confirm data file has `timeline` array
- Check that array is not empty
- Verify scan data structure

**Visualization not showing**
- Check WebGL support in browser
- Ensure proper file serving (not file:// protocol)
- Clear browser cache and reload

**Poor performance**
- Reduce data complexity
- Close other browser tabs
- Check graphics driver updates