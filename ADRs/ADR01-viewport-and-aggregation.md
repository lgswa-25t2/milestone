# ADR 1 : Viewport-Based Aircraft Rendering with Aggregation Strategy

The original system triggered a timer event every 500ms to re-render the display.  
During each event, all tracked aircraft were rendered, resulting in high computational load, especially when the number of tracked aircraft increased.

## Decision
We will optimize the rendering process by applying a viewport-based filtering mechanism and an aggregation strategy.  

Specifically:
1. Only aircraft within the current viewport will be rendered.
2. When zoomed out, instead of rendering all aircraft, we will display aggregated distribution data using circles with a count of aircraft inside each.
3. When zoomed in, rendering will revert to individual aircraft within the viewport.

## Rationale
According to the results of [Experiment 1: Performance Test based on the Number of Aircraft](../experiments/exp01-aircraft-number.md), 

Rendering all aircraft every 500ms caused performance degradation due to increased computation as aircraft count grew. By rendering only visible aircraft and aggregating when zoomed out, we reduce the rendering load significantly.  
Alternatives such as throttling the timer or simplifying aircraft visuals were considered but rejected due to limited effectiveness.  
The chosen approach balances both performance and user usability.

## Status
[Proposed | **Accepted** | Deprecated | Superseded]

## Consequences
Positive:  
- Reduced CPU usage and improved frame rate  
- Enhanced user experience, especially at wider zoom levels

Negative:
- Slight increase in implementation complexity due to aggregation logic