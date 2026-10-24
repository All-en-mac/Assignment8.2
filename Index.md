HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Auto-Responsive Image Gallery</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <header class="gallery-header">
        <h1>Nature & Architecture Gallery</h1>
        <p>An auto-responsive photo collection built with CSS Grid (`auto-fit` & `minmax`).</p>
    </header>

    <!-- Step 3 & 5: Gallery Grid Container -->
    <main class="gallery-container">

        <!-- Step 1 & 2: Gallery Item 1 -->
        <div class="gallery-item">
            <img src="https://images.unsplash.com/photo-1470071459604-3b5ec3a7fe05?auto=format&fit=crop&w=600&q=80" alt="Misty Pine Forest">
            <div class="overlay"><span>Misty Pine Forest</span></div>
        </div>

        <!-- Gallery Item 2 -->
        <div class="gallery-item">
            <img src="https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=600&q=80" alt="Yosemite Valley Stream">
            <div class="overlay"><span>Yosemite Stream</span></div>
        </div>

        <!-- Gallery Item 3 -->
        <div class="gallery-item">
            <img src="https://images.unsplash.com/photo-1426604966848-d7adac902bff?auto=format&fit=crop&w=600&q=80" alt="Snowy Mountain Peaks">
            <div class="overlay"><span>Snowy Peaks</span></div>
        </div>

        <!-- Gallery Item 4 -->
        <div class="gallery-item">
            <img src="https://images.unsplash.com/photo-1469474968028-56623f02e42e?auto=format&fit=crop&w=600&q=80" alt="Hiking Trail Adventure">
            <div class="overlay"><span>Alpine Trail</span></div>
        </div>

        <!-- Gallery Item 5 -->
        <div class="gallery-item">
            <img src="https://images.unsplash.com/photo-1511884642898-4c92249e20b6?auto=format&fit=crop&w=600&q=80" alt="Nordic Fjords">
            <div class="overlay"><span>Nordic Fjords</span></div>
        </div>

        <!-- Gallery Item 6 -->
        <div class="gallery-item">
            <img src="https://images.unsplash.com/photo-1501785888041-af3ef285b470?auto=format&fit=crop&w=600&q=80" alt="Sunset Lake Reflection">
            <div class="overlay"><span>Sunset Lake</span></div>
        </div>

        <!-- Gallery Item 7 -->
        <div class="gallery-item">
            <img src="https://images.unsplash.com/photo-1447752875215-b2761acb3c5d?auto=format&fit=crop&w=600&q=80" alt="Sunlit Forest Canopy">
            <div class="overlay"><span>Sunlit Canopy</span></div>
        </div>

        <!-- Gallery Item 8 -->
        <div class="gallery-item">
            <img src="https://images.unsplash.com/photo-1519681393784-d120267933ba?auto=format&fit=crop&w=600&q=80" alt="Starry Night Mountain Sky">
            <div class="overlay"><span>Starry Night</span></div>
        </div>

    </main>

</body>
</html>

CSS
/* Universal Resets */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

body {
    background-color: #0f172a;
    color: #f8fafc;
    padding: 3rem 5%;
}

.gallery-header {
    text-align: center;
    margin-bottom: 3rem;
}

.gallery-header h1 {
    font-size: 2.5rem;
    font-weight: 800;
    margin-bottom: 0.5rem;
    color: #ffffff;
}

.gallery-header p {
    color: #94a3b8;
    font-size: 1.05rem;
}

/* ==========================================================
   3 & 5. Auto-Responsive Grid Container (`auto-fit` & `gap`)
   ========================================================== */
.gallery-container {
    display: grid; /* Activate CSS Grid */
    
    /* 
      Magic Responsive Rule:
      - repeat(auto-fit, ...): Automatically fits as many columns as possible into the row.
      - minmax(260px, 1fr): Each column is at least 260px wide, but can stretch (1fr) 
        to fill remaining space when windows expand.
    */
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    
    /* 5. Consistent spacing between rows and columns */
    gap: 1.5rem;
    
    max-width: 1400px;
    margin: 0 auto;
}

/* ==========================================================
   2 & 4. Gallery Item & Image Styling (`object-fit`)
   ========================================================== */
.gallery-item {
    position: relative;
    border-radius: 12px;
    overflow: hidden;
    background-color: #1e293b;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
    aspect-ratio: 4 / 3; /* Ensures uniform card proportions */
    cursor: pointer;
}

.gallery-item img {
    width: 100%;                  /* 4. Full container width */
    height: 100%;                 /* Full container height */
    object-fit: cover;            /* 4. Crops image cleanly without distortion */
    display: block;
    transition: transform 0.4s ease;
}

/* Hover Effects */
.gallery-item:hover img {
    transform: scale(1.08);       /* Zoom effect on hover */
}

/* Caption Overlay */
.overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(to top, rgba(15, 23, 42, 0.85) 0%, rgba(15, 23, 42, 0) 60%);
    display: flex;
    align-items: flex-end;
    padding: 1.25rem;
    opacity: 0;
    transition: opacity 0.3s ease;
}

.gallery-item:hover .overlay {
    opacity: 1;
}

.overlay span {
    color: #ffffff;
    font-weight: 600;
    font-size: 1rem;
    letter-spacing: 0.025em;
}