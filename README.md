### Sync - Renters Flow

```mermaid
flowchart TD
    A[Start] --> B[Input: Obtain pmcid and siteid]

    B --> C[Iterate for each siteId]

    C --> D[Call Prospect Management<br/>ProspectSearch API]

    D --> E[Fetch Renter / Prospect Details]

    E --> F[Resolve Codes<br/>Using GetPickLists API]
    F --> F1[Map Prospect Status Codes]
    F --> F2[Map Lead Source Codes]

    E --> G[Retrieve Preference Data<br/>from ProspectSearch Response]

    G --> H[Identify Preferred Units]
    H --> H1[Use FloorplanGroupID]
    H1 --> H2[Match with Floorplans]
    H2 --> H3[Derive preferredUnitIds]

    E --> I[Fetch Lead Events]
    I --> I1[Read Activities Section]
    I1 --> I2[Extract Lead Events]

    I2 --> J[Process Next siteId]
    J --> C

    C -->|All Sites Processed| K[End]

