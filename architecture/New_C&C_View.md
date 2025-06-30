## C&C View Diagram
![image](https://github.com/user-attachments/assets/f716576f-f1a5-4c4b-9bd8-f2a8d25fb9d0)


## Element Catalog
### Processing Components
| Element                                           | Type                 | Responsibility                                                                                                    | Interfaces                                                                             |
| ------------------------------------------------- | -------------------- | ----------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| **DrawObjectsCore** </br>(DrawObjects)               | Processing Component | - Core rendering controller</br> - Zoom-based rendering strategy</br> - Aggregation with cell array</br> - Filters aircraft list | - Provided: Optimized rendering paths<br/> - Required: Hash table, OpenGL, Coord conversion |
| **CellClickProcessor** </br>(CheckCellClickAndZoom)  | Processing Component | - Click-to-zoom for aggregated cells</br> - Enhances aggregated view interaction                                       | - Provided: Cell zoom control<br/> - Required: Coord mapping, Zoom control                  |


### Rendering Components
| Element                                           | Type                | Responsibility                                                          | Interfaces                                                                    |
| ------------------------------------------------- | ------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| **IndividualRenderer** </br>(DrawAirplaneImage)        | Rendering Component | - Renders individual aircraft sprites </br> - Handles rotation and scaling    | - Provided: Detailed rendering<br/> - Required: OpenGL sprites, Texture management |
| **AggregationRenderer** </br>(DrawCircleWithNumber)  | Rendering Component | - Aggregated view circles with counts </br>- High-performance rendering path | - Provided: Circle with count<br/> - Required: OpenGL primitives, Text rendering   |
| **TextRenderer** </br>(Draw2DText)                     | Rendering Component | - Renders aircraft IDs</br> - Handles font scaling and positioning           | - Provided: Text rendering<br/> - Required: OpenGL text API, Font resources        |

### Transform Component
| Element                        | Type                | Responsibility                                                                                  | Interfaces                                                                          |
| ------------------------------ | ------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| **CoordConverter** </br>(LatLon2XY) | Transform Component | - Converts geographic coordinates to screen coordinates</br> - Supports grid mapping for aggregation | - Provided: Coordinate transformation<br/> - Required: Map parameters, Screen dimensions |

### External Component
| Element                             | Type               | Responsibility                                                      | Interfaces                                                               |
| ----------------------------------- | ------------------ | ------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| **OpenGLIF** </br>(OpenGL API)           | Graphics Component | - Hardware-accelerated drawing</br> - Optimization target for draw calls | - Provided: Graphics primitives<br/> - Required: GPU driver, Graphics context |
