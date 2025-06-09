# Experiment 4: API Key Requirement and Limitation Test for Map Providers

## Results and recommendations

To be written upon completion of the experiment.

## Objective

The objective of this experiment is to verify whether the currently used or candidate map providers require an API key, and to evaluate the impact of API key policies on system deployment and scalability.
This will help determine whether the current architecture depends on API-key-restricted services and identify alternative options if necessary.

## Status

[***Planned*** | In progress | Suspended | Canceled | Concluded]

## Expected outcomes

* A comparison table of map providers and their API key requirements
* Identification of usage limits, pricing, and throttling policies
* Feasibility analysis for API-key-free deployment
* List of viable alternative providers or self-hosted options

## Resources required

* **Software**: Current system using embedded map services
* **Network**: Internet access to external map APIs
* **Test providers**:

  * OpenStreetMap (default)
  * Mapbox
  * Google Maps
  * HERE Maps
  * Leaflet with various tile sources
* **Personnel**: 2 people × 4 hours

  * (1 for provider research and testing, 1 for documentation and evaluation)

## Experiment description

### 1. Provider Research and Environment Setup

* Identify all map providers currently integrated or under consideration
* Review documentation for each provider regarding API key requirements, usage quotas, and billing

### 2. Test Scenarios

For each provider:

* Attempt map loading without an API key
* Attempt map loading with a valid API key (if available)
* Measure:

  * Load success/failure
  * Initial loading time
  * Any request throttling or warnings
  * Map tile availability and completeness
* Check policy on commercial vs. non-commercial use

### 3. Data Analysis

* Create a matrix comparing:

  * API key required (Yes/No)
  * Free usage limit (tiles per day/month)
  * Rate limits
  * Behavior when quota exceeded
  * API key security implications
* Assess suitability for current project constraints (e.g., offline use, embedded deployment)

### 4. Conclusion and Review

* Summarize risk level per provider
* Identify preferred providers for API-key-free usage
* Recommend fallback strategies (e.g., self-hosting OpenStreetMap tiles)
* Document legal or licensing considerations

## Duration

Start Date: June 12, 2025
End Date: June 13, 2025
