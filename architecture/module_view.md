# Remote User Interface Module View 


# 1. 아래 그림에서 수정된 모듈만 Coloring하고, 그 아래에 class level로 그린 상세 그림 추가
# 2. 아래 설명 중에 현재 구현과 틀린 부분 있는지 봐주세요.

## Remote User Interface Module View 
![image](https://github.com/user-attachments/assets/cce8d1b4-f761-474b-9b79-91092e8658b4)

![image](https://github.com/user-attachments/assets/6fe565a7-0803-4265-95b8-a6d0b6b05373)


**Key Highlight - Region Clustering Feature:**

🎯 **Region clustering functionality when zooming out** implemented in the **DisplayGUI module**:

1. **Zoom Level Detection**: Check zoom level with `xf >= cellDrawZoomRate` condition
2. **Grid System**: Divide screen into 10x10 cells
3. **Aircraft Counting**: Calculate number of aircraft in each cell
4. **Circle Rendering**: Display circular indicators using `DrawCircleWithNumber()` function
5. **Performance Optimization**: Show aggregated information instead of individual aircraft

**Key Module Relationships:**
- **DisplayGUI**: Contains overall rendering logic and clustering algorithm
- **HashTable**: High-speed search/management of all aircraft data
- **ntds2d**: OpenGL-based graphics rendering (circles, text, etc.)
- **Aircraft**: Individual aircraft position and status information
- **LatLonConv**: Converts geographic coordinates to screen coordinates

**System Architecture Description:**

This ADS-B Display System implements a sophisticated **region-based clustering feature** that enhances both user experience and system performance. When users zoom out beyond a certain threshold (`cellDrawZoomRate`), the system automatically switches from displaying individual aircraft icons to showing regional clusters.

**Core Features:**
- **Adaptive Display**: Automatically switches between detailed aircraft view and clustered view based on zoom level
- **Grid-based Clustering**: Uses a 10x10 grid system to group aircraft by screen regions
- **Visual Feedback**: Displays white circles with aircraft counts for each populated region
- **Performance Optimization**: Reduces rendering overhead when dealing with high aircraft density

**Technical Implementation:**
The clustering functionality is primarily implemented in the `DrawObjects()` method of the DisplayGUI module, which:
1. Monitors the zoom factor (`xf`) against the clustering threshold
2. Calculates cell positions for each aircraft on screen
3. Aggregates aircraft counts per cell
4. Renders circular indicators with count numbers instead of individual aircraft sprites

This design pattern effectively addresses the challenge of displaying dense aircraft traffic while maintaining system responsiveness and visual clarity.

  
