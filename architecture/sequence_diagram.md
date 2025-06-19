# RUI Sequence Diagram

## Remote User Interface Sequence Diagram for Region clustering
![image](https://github.com/user-attachments/assets/eb02cc6d-2194-42e2-b37e-1e95e3a1b421)


---

### Key Features

* **Clustering Threshold**: Clustering mode is enabled when `cellDrawZoomRate = 0.00005`.
* **Grid System**: The screen is divided into a 10×10 grid to group aircraft by region.
* **Performance Optimization**: Instead of rendering each aircraft individually, circular indicators are drawn per region to improve rendering performance.

---

### Two-Step Processing Workflow

**Loop 1: Data Collection & Grid Calculation**

* Iterate through all aircraft data in the `HashTable`.
* Convert each aircraft’s latitude and longitude to screen coordinates using `LatLon2XY`.
* Determine which cell of the 10×10 grid the screen coordinates fall into.
* Increment the aircraft count for that cell.

**Loop 2: Visualization Rendering**

* Iterate through all cells of the 10×10 grid.
* For cells containing aircraft, render a circular indicator.
* Use OpenGL to draw a semi-transparent white circle and overlay the aircraft count as text.

---

### Performance Impact

* **Before**: Hundreds of individual aircraft sprites were rendered. Too many aircraft are displayed, making it difficult for the user to select the desired one.
* **After**: At most 100 simplified circular indicators (10×10 grid cells).
* **Result**: Reduced rendering load, enhanced visual clarity, and improved user experience.

