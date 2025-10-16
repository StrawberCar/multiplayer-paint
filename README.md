# 🎨 Multiplayer Paint

A real-time collaborative painting web application built with Supabase for the backend and designed to be hosted on GitHub Pages.

## Features

- **Real-time Collaboration**: See other users drawing in real-time
- **Live Cursors**: Watch where other artists are drawing with colored cursors and usernames
- **Active Users Display**: See who's currently painting with you
- **Customizable Tools**: Choose your color and brush size
- **Canvas Persistence**: All drawings are saved to the database
- **Responsive Design**: Works on desktop and mobile devices
- **Touch Support**: Draw with your finger on mobile devices

## How It Works

The application uses:
- **Supabase Database**: Stores all painting strokes and canvas data
- **Supabase Realtime**: Provides instant updates when other users draw
- **PostgreSQL**: Backend database with Row Level Security enabled for public access
- **Vanilla JavaScript**: No framework dependencies, just pure JS

## Database Schema

The app uses three main tables:

1. **canvases**: Stores canvas metadata (size, name)
2. **strokes**: Stores individual drawing strokes with points, color, and size
3. **active_users**: Tracks currently active users and their cursor positions

## Deployment to GitHub Pages

### Step 1: Create a GitHub Repository

1. Go to GitHub and create a new repository
2. Name it something like `multiplayer-paint`
3. Make it public (required for GitHub Pages)

### Step 2: Upload Files

1. Upload the `index.html` file to your repository
2. Commit the changes

### Step 3: Enable GitHub Pages

1. Go to your repository's Settings
2. Navigate to "Pages" in the left sidebar
3. Under "Source", select "Deploy from a branch"
4. Select the `main` branch and `/ (root)` folder
5. Click "Save"

### Step 4: Access Your Site

Your site will be available at: `https://[your-username].github.io/[repository-name]/`

For example: `https://yourusername.github.io/multiplayer-paint/`

## Configuration

The application is already configured to use your Supabase project:
- **Project URL**: https://hhfvoadudcikgpygexvf.supabase.co
- **Database**: Already set up with all necessary tables and policies

The Supabase configuration is embedded in the HTML file, so no additional configuration is needed!

## Usage

1. Open the website in your browser
2. Enter your name
3. Choose a color and brush size
4. Start drawing!
5. Share the link with friends to draw together in real-time

## Features Explained

### Real-time Drawing
When you draw, your strokes are immediately sent to the Supabase database. Other users subscribed to the same canvas receive these updates instantly via Supabase Realtime and render them on their canvas.

### Live Cursors
As users move their cursor over the canvas, their position is updated in the `active_users` table every time they move. Other users see these cursors with the user's name and color.

### Presence System
The app automatically tracks when users are active by updating their `last_seen` timestamp. Inactive users (no activity for 15 seconds) are automatically removed from the active users list.

### Clear Canvas
The "Clear Canvas" button removes all strokes from the database and clears the canvas for all users. Use with caution!

## Technical Details

- **No Authentication Required**: The app uses anonymous access with Row Level Security policies that allow public read/write
- **Efficient Storage**: Strokes are stored as JSONB arrays of points, allowing for efficient storage and retrieval
- **Real-time Subscriptions**: Uses Supabase's PostgreSQL change data capture for instant updates
- **Automatic Cleanup**: Inactive users are automatically removed to keep the active users list clean

## Browser Support

- Chrome/Edge (recommended)
- Firefox
- Safari
- Mobile browsers (iOS Safari, Chrome Mobile)

## Future Improvements

Potential features to add:
- Multiple canvas rooms
- Undo/redo functionality
- Export canvas as image
- More drawing tools (eraser, shapes, text)
- Color palettes
- Layer support
- User authentication for saving personal drawings

## Troubleshooting

### Canvas not loading
- Check browser console for errors
- Ensure Supabase project is active and accessible

### Drawings not syncing
- Verify internet connection
- Check if Supabase Realtime is enabled on your project
- Check browser console for connection errors

### Performance issues
- Large number of strokes may slow down rendering
- Use the "Clear Canvas" button to reset
- Consider implementing stroke batching for better performance

## License

This project is open source and available for anyone to use and modify!

---

Built with ❤️ using Supabase and vanilla JavaScript