# Design Decisions

- **Single-page delivery:** The application is a self-contained `index.html` using CDN dependencies.
- **Libraries:** chess.js validates game rules, chessboard.js renders positions, jQuery supports chessboard.js, and Alpine.js generates repeated clocks, boards, and layout controls.
- **Dual-board view:** Both boards show one synchronized game. Board A uses white orientation and Board B uses black orientation.
- **Layouts:** Opposed mode rotates Board B by 180 degrees. Sideways mode rotates Board A by 90 degrees and Board B by 270 degrees, using short visual transitions.
- **Piece interaction:** Tapping a piece highlights legal destinations only on the board being used, keeping the opposing board free of selection and move-target markers. Pointer Events provide consistent mouse and touch dragging, including correctly rotated floating pieces.
- **Pawn promotion:** A legal promotion pauses move completion and opens an enlarged vertical icon-only picker for queen, rook, bishop, or knight. The whole picker uses the board's piece resource, rotates into the active player's viewing direction, and appears below the promotion square from that player's perspective.
- **Move history:** The origin and destination squares of the latest move receive a synchronized light-yellow tint on both boards.
- **Viewport layout:** Boards are edge-to-edge, equally sized, centered, and dynamically constrained by both viewport width and available height. Page scrolling is disabled.
- **Controls:** The title opens a dropdown containing game restart and a Black/White position swap. Swapping updates board orientations, clock positions, and captured-piece placement together. Clock settings and board layout controls remain compact around a full-width, centered timer panel, while a persistent top-right button toggles browser fullscreen mode.
- **Clock behavior:** Common and custom time controls support increments, pause, reset, and automatic turn switching after the first move. A flag stops both clocks permanently until reset or restart, but play may continue.
- **Clock visuals:** Each clock box doubles as its remaining-time bar. Inactive fills are light blue, the active fill is green, and flagged clocks use red.
- **Board alignment:** chessboard.js's default border is removed and its internally rounded board size is centered to keep rotated boards aligned.
- **Check feedback:** The checked king receives a pulsing red radial bloom on both synchronized boards. Checkmate marks the winning king with a compact green queen badge and the losing king with a red loss badge.
- **Captured pieces:** Each board has a narrow outer-side tray with captured white pieces ending at the center divider and captured black pieces starting there. The two equal-height sections keep that divider fixed at the board midpoint. Pieces are ordered from highest value at the center to lowest value outward, use the board's piece image resource, and rotate with their associated board.
