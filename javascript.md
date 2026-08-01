```mermaid
flowchart TD
    A(("Page Load / Init")) --> B["Build board grid & set initial game state"]
    B --> C["Attach event listeners"]
    C --> D(("Start Button Click"))
    D --> E["Hide modal & start render + timer intervals"]
    E --> F["Render cycle executes every 400ms"]
    F --> G["Clear snake fill classes"]
    G --> H["Mark food cell"]
    H --> I["Compute next head position"]
    I --> J{"Wall collision?"}
    J -->|Yes| K["Stop intervals & show game over modal"]
    J -->|No| L{"Food consumed?"}
    L -->|Yes| M["Generate new food, update score/high score, grow snake"]
    L -->|No| N["Advance snake by adding head & removing tail"]
    M --> O["Draw snake on board"]
    N --> O
    O --> F
    C --> P(("Keydown Event"))
    P --> Q{"Arrow key pressed?"}
    Q -->|Up| R["direction = up"]
    Q -->|Right| S["direction = right"]
    Q -->|Left| T["direction = left"]
    Q -->|Down| U["direction = down"]
    C --> V(("Restart Button Click"))
    V --> W["Reset score, time, direction, snake, food, UI & restart render loop"]
    