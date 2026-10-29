1. HTML Code (index.html)
HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aperture & Co. | Photo Gallery</title>
    <link rel="stylesheet" href="style.css">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600&family=Playfair+Display:wght@600&display=swap" rel="stylesheet">
</head>
<body>

    <!-- Header Section -->
    <header class="site-header">
        <h1>Aperture & Co.</h1>
        <p>A curated collection of modern architectural and landscape photography.</p>
    </header>

    <!-- Main Grid Layout -->
    <main class="gallery-container">
        
        <!-- Card 1 (Standard) -->
        <article class="gallery-item">
            <img src="https://images.unsplash.com/photo-1513694203232-719a280e022f?auto=format&fit=crop&w=800&q=80" alt="Minimalist Interior">
            <div class="overlay">
                <h3>Minimalist Spaces</h3>
                <p>Architecture • Tokyo</p>
            </div>
        </article>

        <!-- Card 2 (Featured - Explicit Grid Span) -->
        <article class="gallery-item wide">
            <img src="https://images.unsplash.com/photo-1470071459604-3b5ec3a7fe05?auto=format&fit=crop&w=1200&q=80" alt="Foggy Pine Forest">
            <div class="overlay">
                <h3>Misty Horizons</h3>
                <p>Landscape • Pacific Northwest</p>
            </div>
        </article>

        <!-- Card 3 (Standard) -->
        <article class="gallery-item">
            <img src="https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=800&q=80" alt="Tropical Coastline">
            <div class="overlay">
                <h3>Coastal Serenity</h3>
                <p>Seascape • Amalfi Coast</p>
            </div>
        </article>

        <!-- Card 4 (Standard) -->
        <article class="gallery-item">
            <img src="https://images.unsplash.com/photo-1519681393784-d120267933ba?auto=format&fit=crop&w=800&q=80" alt="Starry Night Sky">
            <div class="overlay">
                <h3>Stargazer</h3>
                <p>Night • Swiss Alps</p>
            </div>
        </article>

        <!-- Card 5 (Featured - Explicit Grid Span) -->
        <article class="gallery-item tall">
            <img src="https://images.unsplash.com/photo-1486406146926-c627a92ad1ab?auto=format&fit=crop&w=800&q=80" alt="Modern Skyscraper">
            <div class="overlay">
                <h3>Vertical Geometry</h3>
                <p>Urban • Chicago</p>
            </div>
        </article>

        <!-- Card 6 (Standard) -->
        <article class="gallery-item">
            <img src="https://images.unsplash.com/photo-1447752875215-b2761acb3c5d?auto=format&fit=crop&w=800&q=80" alt="Autumn Forest Path">
            <div class="overlay">
                <h3>Autumn Tones</h3>
                <p>Nature • Vermont</p>
            </div>
        </article>

        <!-- Card 7 (Standard) -->
        <article class="gallery-item">
            <img src="https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=800&q=80" alt="Yosemite Valley">
            <div class="overlay">
                <h3>Granite Monoliths</h3>
                <p>Adventure • Yosemite</p>
            </div>
        </article>

    </main>

    <!-- Footer Section -->
    <footer class="site-footer">
        <p>&copy; 2026 Aperture & Co. All rights reserved. Built with CSS Grid.</p>
    </footer>

</body>
</html>
2. CSS Code (style.css)
CSS
/* --- Global Styles & Reset --- */
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: 'Inter', sans-serif;
    background-color: #0f172a;
    color: #f8fafc;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
}

/* --- Header Section --- */
.site-header {
    text-align: center;
    padding: 50px 20px 30px 20px;
}

.site-header h1 {
    font-family: 'Playfair Display', serif;
    font-size: 2.8rem;
    letter-spacing: 1px;
    margin-bottom: 10px;
    color: #ffffff;
}

.site-header p {
    color: #94a3b8;
    font-size: 1rem;
    font-weight: 300;
}

/* --- Main Grid Layout --- */
.gallery-container {
    display: grid;
    /* Using repeat(), minmax(), and fr units for responsive columns with consistent gaps */
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    grid-auto-rows: 280px;
    gap: 24px;
    max-width: 1400px;
    width: 92%;
    margin: 0 auto 60px auto;
}

/* --- Gallery Card Component --- */
.gallery-item {
    position: relative;
    border-radius: 12px;
    overflow: hidden; /* Prevents image overflow */
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.3);
    background-color: #1e293b;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    min-width: 0; /* Prevents grid blowout from flex/grid items */
}

.gallery-item:hover {
    transform: translateY(-5px);
    box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.4);
}

/* --- Preventing Image Overflow --- */
.gallery-item img {
    width: 100%;
    height: 100%;
    object-fit: cover; /* Ensures image covers area cleanly without distortion or overflow */
    display: block;
    transition: transform 0.5s ease;
}

.gallery-item:hover img {
    transform: scale(1.05);
}

/* --- Overlay & Text Styling (Overflow prevention) --- */
.overlay {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    padding: 25px 20px 20px 20px;
    background: linear-gradient(to top, rgba(15, 23, 42, 0.9) 0%, rgba(15, 23, 42, 0) 100%);
    opacity: 0;
    transition: opacity 0.3s ease;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
}

.gallery-item:hover .overlay {
    opacity: 1;
}

.overlay h3 {
    font-size: 1.15rem;
    font-weight: 600;
    color: #ffffff;
    margin-bottom: 4px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis; /* Prevents long text from overflowing */
}

.overlay p {
    font-size: 0.85rem;
    color: #cbd5e1;
}

/* --- 3. Explicit Grid Placement (Spans) --- */
.gallery-item.wide {
    grid-column: span 2;
}

.gallery-item.tall {
    grid-row: span 2;
}

/* --- Footer Section --- */
.site-footer {
    text-align: center;
    padding: 30px;
    background-color: #0b0f19;
    color: #64748b;
    font-size: 0.9rem;
    margin-top: auto;
    border-top: 1px solid #1e293b;
}

/* --- Responsive Adjustments for Smaller Screens --- */
@media (max-width: 768px) {
    /* Reset explicit spans on mobile so cards stack smoothly in single columns */
    .gallery-item.wide,
    .gallery-item.tall {
        grid-column: span 1;
        grid-row: span 1;
    }
    
    .gallery-container {
        grid-auto-rows: 240px;
        gap: 16px;
    }
}
Assignment Checklist & Verification:
Header & Footer: Included professional header title/tagline and bottom footer.

Main Grid Layout: Controlled with display: grid on .gallery-container.

Multiple Cards/Images: Loaded with 7 high-quality responsive photography cards.

Consistent Gaps: Maintained using gap: 24px;.

Responsive Columns: Handled automatically using repeat(auto-fit, minmax(280px, 1fr)).

repeat(), minmax(), & fr Units: Fully integrated in the grid track definition.

Explicit Grid Placement: Demonstrated using .wide (grid-column: span 2) and .tall (grid-row: span 2).

Overflow Prevention: Implemented via object-fit: cover, overflow: hidden, min-width: 0, and text-overflow: ellipsis.