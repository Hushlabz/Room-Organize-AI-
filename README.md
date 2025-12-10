# Room Organize - AI-Powered Room Organization App

An AI-powered mobile app that helps you organize and beautify any room. Simply take a photo of your space, and AI will generate a vision of what it could look like organized, plus provide step-by-step instructions to achieve that transformation.

## Features

- **📸 Photo Capture**: Take or upload photos of any space
- **🏠 21 Space Categories**: Organize rooms, offices, kitchens, gyms, studios, and more
- **🤖 AI Vision**: Generate organized, functional versions using Nano Banana Pro (Gemini 3)
- **📝 Smart Instructions**: Get 5-7 actionable steps tailored to your space type
- **📚 History**: View past transformations and revisit instructions
- **✨ Beautiful UI**: Clean, modern design inspired by Pinterest and interior design apps
- **🎁 Free Trial**: 1 free transformation to try the app
- **👑 Premium Subscription**: Unlock unlimited transformations for $4.99/month
- **🔐 Google Sign-In**: Save progress and sync across devices

## Tech Stack

- **Frontend**: Expo SDK 53, React Native 0.76.7, TypeScript
- **Navigation**: React Navigation 7 (Stack Navigator)
- **Styling**: NativeWind (Tailwind CSS)
- **State**: Zustand with AsyncStorage persistence
- **AI**: Nano Banana Pro (Gemini 3 Pro Image Preview) - Text & Image generation
- **Payments**: RevenueCat for subscription management
- **Auth**: Better Auth with Google OAuth
- **Backend**: Bun + Hono + Prisma (SQLite) + Better Auth
- **Icons**: Lucide React Native

## How It Works

1. **Sign In** (Optional): Sign in with Google to save your transformations
2. **Free Trial**: Get 1 free transformation
3. **Choose Category**: Select from 21 space types (room, office, kitchen, gym, studio, etc.)
4. **Capture**: Take a photo or select from your gallery
5. **Analyze**: Nano Banana Pro analyzes your space with category-specific context
6. **Transform**: AI generates a 2K quality image of your organized space (~30 seconds)
7. **Guide**: Get 5-7 specific, actionable steps tailored to your space type
8. **Subscribe**: After free trial, subscribe for unlimited access

## Space Categories

The app supports 21 different space types, each with tailored AI analysis:

**Residential:**
- Room (bedroom/living room)
- Kitchen
- Home Gym
- Garage / Workshop
- Garden / Backyard
- Studio Apartment
- Home Theatre

**Workspace:**
- Office Workspace
- Classroom / Study Area
- Photography / YouTube Studio
- Music Studio

**Commercial:**
- Event Hall / Banquet Hall
- Hotel Room
- Doctor's Clinic / Medical Room
- Car Showroom
- Exhibition / Booth Setup
- Gym / Fitness Center
- Airbnb Space

**Specialized:**
- VR Gaming Room
- Camper Van / RV Interior
- Pop-up Shop / Kiosk

## Subscription & Monetization

**Free Tier:**
- 1 free transformation (any space type)
- Full access to all features for first use
- View transformation history

**Premium - $4.99/month:**
- ✅ Unlimited space transformations (all 21 categories)
- ✅ High-quality 2K AI-generated images
- ✅ Priority AI processing
- ✅ Save unlimited history
- ✅ Export before/after images
- ✅ Ad-free experience

## Authentication

**Google Sign-In:**
- Secure OAuth authentication via Better Auth
- Sync transformations across devices
- Track usage per user
- Optional (can use app without signing in)

## Setup

### Prerequisites
The app comes pre-configured with:
- Nano Banana Pro API integration (ready to use)
- RevenueCat payments (Test Store + App Store configured)
- Better Auth with Google OAuth support

### Google OAuth Setup (Optional)
To enable Google Sign-In, add these environment variables:
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create OAuth 2.0 credentials
3. Add to ENV tab in Vibecode:
   - `GOOGLE_CLIENT_ID`
   - `GOOGLE_CLIENT_SECRET`

## App Structure

### Frontend
- `src/screens/HomeScreen.tsx` - Landing page with usage indicator and login button
- `src/screens/CategorySelectionScreen.tsx` - Choose from 21 space types
- `src/screens/CameraScreen.tsx` - Photo capture with usage check
- `src/screens/ResultsScreen.tsx` - Before/after with AI instructions
- `src/screens/SubscriptionScreen.tsx` - Premium paywall
- `src/screens/LoginScreen.tsx` - Google Sign-In flow
- `src/constants/categories.ts` - Space category definitions and AI prompts
- `src/state/roomStore.ts` - Room organization history
- `src/state/usageStore.ts` - Usage tracking and premium status
- `src/navigation/RootNavigator.tsx` - App navigation
- `src/lib/revenuecatClient.ts` - RevenueCat SDK wrapper
- `src/lib/authClient.ts` - Better Auth client

### Backend
- `backend/src/auth.ts` - Better Auth config with Google OAuth
- `backend/src/env.ts` - Environment validation
- `backend/prisma/schema.prisma` - Database schema

## RevenueCat Configuration

- **Project**: Organizer AI (`proj83c86f8e`)
- **Entitlement**: Premium Access (`premium`)
- **Apps**:
  - Test Store (for development testing)
  - App Store (bundle: `com.vibecode.roomremixai.3svrfs`)
- **Product**: Premium Monthly ($4.99)
- **Offering**: Premium Subscription (default)
- **Package**: `$rc_monthly`

Note: To publish to App Store, manually configure App Store Connect API credentials in RevenueCat dashboard.

## User Flow

1. User opens app → sees HomeScreen with usage indicator
2. Optional: Click login button → Sign in with Google
3. Click "Organize a Room" → CategorySelectionScreen with 21 space types
4. Select category (e.g., "Kitchen", "Office", "Home Gym") → CameraScreen
5. Select or take photo → Usage check:
   - **First time**: Proceed to ResultsScreen → AI processes with category-specific prompts → Usage counter increments
   - **After 1st use**: Show paywall alert → Navigate to SubscriptionScreen
6. Subscribe → Premium status activated → Unlimited access to all categories

## Design System

- **Colors**:
  - Background: Soft cream (#FAF9F6)
  - Primary accent: Terracotta (#E07A5F)
  - Secondary: Sage green (#81B29A)
  - Text: Charcoal (#2F3E46)
- **Style**: Clean, spacious, minimal with warm aesthetics
- **Inspiration**: Pinterest, Houzz, Calm app

## AI Processing Time

- Image analysis: ~5-10 seconds
- Room transformation generation: ~30 seconds
- Total: ~40 seconds per transformation

---

# Template App 53 — AI Agent & Engineer Guide
You are using this app template (pre-cloned into `/home/user/workspace`) to build out the user's requested app. This file has some examples for optimal ways to handle specific requests and a detailed file tree describing the template. Do not edit this file.

This repository includes a production-ready Expo + React Native template designed for AI agents and engineers to rapidly build high-quality mobile apps in the [Vibecode](https://vibecodeapp.com) mobile app and website. This guide explains how the template is set up, the technical decisions behind it, best practices, and the first steps you should take after the initial prompt.

If you are an AI engineer (human or agent), please read the whole file carefully before making changes.


## Stack and key decisions
- Expo SDK 53, React Native 0.79.2, React 19.0.0.
- Navigation: React Navigation 7
  - `@react-navigation/native-stack` for native-feeling stacks and `@react-navigation/bottom-tabs` for tabs.
  - Example Router is implemented in `src/navigation/RootNavigator.tsx` with a root stack and a tab navigator as an example.
  - You must edit the navigator after the first prompt from the user. Remove all unused tabs from the navigator and their corresponding screen files in `src/screens/`
  — DO NOT leave empty or placeholder tabs/screens when you edit the navigator.
  - For Games and full screen app experiences, remove the tab navigator entirely. You may also want to remove the header and back button. You will be punished if the user sees any existing placeholder tab and page.
  - Please either create at least 2 fully functional tabs with real content, or remove the tab navigator. Never create apps with 1 tab or empty tabs. When removing tabs, also remove the unused screen files.
  - Don't customize insets in tabs and header. That means no SafeAreaView or useSafeAreaInsets in screens that are tabs or use default react navigation header.
- TypeScript with strict mode
  - Path alias `@/*` configured in `tsconfig.json` for clean imports.
  - Follow strict typing and avoid `any`. Use the TypeScript LSP and ESLint to help you write correct code with proper types.
- Styling: Nativewind (Tailwind) + Tailwind Merge
  - Global Tailwind is imported in `index.ts` via `global.css`.
  - Prefer `className` for `Text` and `View`; use `StyleSheet` for FlatList/Animated/complex components.
- Gestures & animations
  - `react-native-gesture-handler` and `react-native-reanimated@3` are preconfigured.
- Icons: Use `lucide-react-native` for all icons
- State management
  - Zustand + optional AsyncStorage persistence. Place stores in `src/state`. Persist minimally.

## Environment and constraints (Vibecode)
- Dev Expo server is managed automatically (port 8081). Do not check, change, or restart it; if preview issues occur, ask the user to click the refresh button or pull to refresh within the Vibecode app.
- Backend is running on port 3000 automatically. Do not check, change, or restart it. 
- Do not manage git. It is done automatically.
- You can view all logs by reading the `home/user/workspace/expo.log` file. The user can view the logs in the Vibecode app.
- Use `bun` (not npm/yarn). Scripts are in `template-app-53/package.json`.
- Environment variables are injected at runtime; access via `process.env.EXPO_PUBLIC_*` directly. Do NOT use `@env` or `expo-constants` for secrets.
- The user can add new enviroment variables using the ENV tab on the Vibecode app.

## Dependency policy: why versions are fixed
- Stability first: The template pins React Native and Expo to known-good versions that work with the included patches in `patches/` and `patchedDependencies` in `package.json`.
- Predictability for agents: Avoids unexpected native changes or autolinking inconsistencies that break the build.
- Security and review: Minimizes drift so changes are deliberate and reviewable.

### What you can install
- Allowed: JavaScript-only libraries (e.g., utilities like `lodash`, validation like `zod`, UI helpers without native modules, icon fonts, or Google font packages like `@expo/google-fonts` packages like `@expo/google-fonts/Roboto` or `@expo/google-fonts/Inter` for fonts.).
- Allowed: ANY packages in the `backend` directory.
- Avoid: New native modules or libraries that require custom native configuration. Many common native modules are already included; prefer using what is preinstalled.
- If in doubt, prefer using or extending the included modules. Do not add packages that require custom config plugins or manual native steps.

## First steps after the first prompt
1. Update navigation
   - Edit `src/navigation/RootNavigator.tsx` to define the routes you need. Add or rename tabs and stack screens. Use `headerShown`/`headerTransparent`/`presentation` as appropriate.
2. Create screens
   - Add files in `src/screens/` using the strongly-typed helpers from `src/navigation/types.ts`. Use `Pressable` (not `TouchableOpacity`).
   - For scrollable screens with headers, use `useHeaderHeight()` and set `contentInsetAdjustmentBehavior="automatic"` where needed.
3. Set up state
   - Create minimal Zustand stores in `src/state`. Use individual selectors to avoid infinite loops. Persist only the necessary slices with AsyncStorage if needed.
4. Styling and theming
   - Use Tailwind classes via `className` on `Text`/`View`. Use `StyleSheet` for complex or animated components.
   - Use `lucide-react-native` for iconography.
5. Safe areas & headers
   - `App.tsx` already includes `SafeAreaProvider`. Inside screens use `View`, not `SafeAreaView`, unless you use a custom header component. Most cases you can configure headers via navigator options.
6. Keyboard safety
   - Ensure inputs are not obscured by the keyboard. Use appropriate padding/scrolling and dismiss keyboards when tapping outside.
   - Use the `KeyboardAvoidingView` or `KeyboardAvoidingScrollView` or `react-native-keyboard-controller` library to manage the keyboard.

## Commands
There are only a few scripts you will need, as the Vibecode dev Expo server is managed automatically, and the app can be previwed using the Vibecode app.
```bash
bun run typecheck    # typecheck with TypeScript
bun run lint         # lint with Expo config
bun run format       # Prettier format
```
