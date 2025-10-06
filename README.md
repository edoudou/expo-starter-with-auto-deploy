# Expo-starter 
Start FAST with Expo + Supabase + NativeBase + Zustand.

## Features

- Expo SDK `47`
- [Supabase](https://github.com/supabase/supabase) 
- [Zustand](https://github.com/pmndrs/zustand)
- [NativeBase](https://github.com/GeekyAnts/NativeBase)
- [React Navigation](https://github.com/react-navigation/react-navigation)
- Auth flow (Login, Register, Session management)

## Installation

1. Clone this project

```bash
git clone https://github.com/linus1703/expo-starter
```
2. Change into the directory and install the dependencies

```bash
cd expo-starter

yarn install
```

3. Update `/app/config/config.base.ts` with your own configuration, e.g.:

```shell
# Replace XXXX's with your own Supabase keys
SUPABASE_URL: "XXXX",
SUPABASE_ANON_KEY: "XXXX",
```

4. Start the project:

- `yarn start`

## File Structure

```shell
Expo Starter/
├─ app/
│  ├─ components/
│  ├─ config/
│  ├─ constants/
│  ├─ hooks/
│  ├─ navigation/
│  ├─ screens/
│  ├─ services/
│  ├─ stores/
├─ assets/
│  ├─ fonts/
│  ├─ images/
App.tsx

```

## Screens

Main screens:

- Login
- Signup
- Home (Bare Minimum) with a logout button

![Login screen](https://i.imgur.com/ynyvDe5.png)

![Signup screen](https://i.imgur.com/ZtWEpnx.png)

## Continuous deployment

This starter includes GitHub Actions workflows to automate deployments:

- **Deploy Expo App** (`.github/workflows/expo-deploy.yml`) publishes the app to Expo on pushes to `main`. Set the `EXPO_TOKEN` repository secret with a token generated from your Expo account so the workflow can authenticate before running `expo publish`.
- **Publish Expo Preview** (`.github/workflows/expo-preview.yml`) builds a testing release for each pull request using a dedicated Expo release channel named after the PR number (e.g. `pr-42`). It re-publishes the preview whenever the pull request is updated, allowing reviewers to try the latest changes.
- **Cleanup Expo Preview** (`.github/workflows/expo-preview-cleanup.yml`) automatically removes the temporary preview release channel once a pull request is merged to keep your Expo project tidy. Both preview workflows use the same `EXPO_TOKEN` secret as the production deployment.
- **Deploy Supabase Edge Functions** (`.github/workflows/supabase-edge-functions.yml`) deploys any edge functions stored under `supabase/functions` using the Supabase CLI. Provide `SUPABASE_ACCESS_TOKEN` and `SUPABASE_PROJECT_ID` secrets so the workflow can log in and target the correct project.

Each workflow can also be triggered manually from the GitHub Actions tab with the **Run workflow** button.
