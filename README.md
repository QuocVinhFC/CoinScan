# CoinScan

## App Flow

![Flow scan coin](Flow%20scan%20coin.png)

## iOS App Structure (proposed)

### Navigation
- **AppRouter** decides initial route: `Splash -> (Onboarding) -> Main`
- **Main** uses a `TabView` with primary features

### Screens / Modules
1. **Splash**
   - Load config
   - Restore session (if any)

2. **Onboarding** *(first launch)*
   - Intro pages
   - Request permissions: Camera, Notifications

3. **Auth** *(optional)*
   - Sign in / Sign up
   - Continue as Guest

4. **Main (Tab Bar)**
   - **Scan**
     - Camera scanner (AVFoundation)
     - Scan result
     - Coin detail
   - **Market**
     - Market list + search
     - Coin detail
   - **Watchlist**
     - Saved coins
     - Price alerts
   - **Settings**
     - Currency, theme
     - Manage permissions

### Architecture
- **SwiftUI + MVVM**
- Layers:
  - `Presentation` (Views/ViewModels)
  - `Domain` (UseCases/Models)
  - `Data` (API/Repositories/Cache)

### Suggested project folders
- `App/`
- `Features/Scan/`
- `Features/Market/`
- `Features/Watchlist/`
- `Features/Settings/`
- `Shared/Networking/`
- `Shared/Persistence/`
- `Shared/Components/`