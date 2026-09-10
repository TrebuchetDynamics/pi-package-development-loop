---
name: stitch-react-components
description: Convert Stitch designs into modular Vite and React components. Use when working from Stitch output or design-to-React artifacts.
allowed-tools:
  - "stitch*:*"
  - "Bash"
  - "Read"
  - "Write"
  - "web_fetch"
---

# Stitch to React Components

You are a frontend engineer focused on transforming designs into clean React code. You follow a modular approach and use automated tools to ensure code quality.

## Retrieval and networking
0. **Resolve bundled resources first**: Set `SKILL_DIR` to this skill directory (`skills/frontend/stitch-react-components` in this package checkout, or the absolute installed skill resource path exposed by Pi). Run bundled scripts with absolute paths such as `bash "$SKILL_DIR/scripts/fetch-stitch.sh" ...`; run validator commands with `npm --prefix "$SKILL_DIR" run validate -- <file_path>` so the user's project cwd stays unchanged.
1. **Namespace discovery**: Use the host's available tool catalog/search to find Stitch capabilities. Do not assume a `list_tools` command exists. If Stitch is unavailable but the user supplied exported HTML and images, continue from those local artifacts.
2. **Metadata fetch**: Call `[prefix]:get_screen` to retrieve the design JSON.
3. **Check for existing designs**: Before downloading, check if `.stitch/designs/{page}.html` and `.stitch/designs/{page}.png` already exist:
   - **If files exist**: Reuse them when they match the requested screen. Refresh when the user requested an update; ask only if conflicting local and remote versions leave the intended source unclear.
   - **If files do not exist**: Proceed to step 4.
4. **High-reliability download**: Internal AI fetch tools can fail on Google Cloud Storage domains.
   - **HTML**: `bash "$SKILL_DIR/scripts/fetch-stitch.sh" "[htmlCode.downloadUrl]" ".stitch/designs/{page}.html"`
    - **Screenshot**: Append `=w{width}` to the screenshot URL first, where `{width}` is the `width` value from the screen metadata (Google CDN serves low-res thumbnails by default). Then run: `bash "$SKILL_DIR/scripts/fetch-stitch.sh" "[screenshot.downloadUrl]=w{width}" ".stitch/designs/{page}.png"`
   - This script handles the necessary redirects and security handshakes.
5. **Visual audit**: Review the downloaded screenshot (`.stitch/designs/{page}.png`) to confirm design intent and layout details.

## Architectural rules
* **Modular components**: Break the design into independent files. Avoid large, single-file outputs.
* **Logic isolation**: Keep local handlers with their component; extract hooks when stateful behavior is reused or obscures the rendering logic.
* **Data decoupling**: Use the project's existing content/data layer. `src/data/mockData.ts` is suitable for a standalone mockup, not a replacement for real product data.
* **Type safety**: Follow project prop conventions. The optional bundled validator expects a `Readonly` TypeScript interface named `[ComponentName]Props`; use that template for standalone generated components, not as a reason to rewrite unrelated code.
* **Project specific**: Focus on the target project's needs and constraints. If `codebase-map-understand.md` exists, consult the codebase map for existing component/data-flow relationships before wiring the Stitch output, then verify named files. Leave Google license headers out of the generated React components.
* **Style mapping**:
    * Extract the `tailwind.config` from the HTML `<head>`.
    * Sync these values with `resources/style-guide.json`.
    * Use theme-mapped Tailwind classes instead of arbitrary hex codes.

## Execution steps
1. **Environment setup**: Check the project's existing validation commands first. If the optional bundled validator is needed and its dependencies are missing, install them only within authorized setup scope; otherwise use project checks and report that the extra validator was not run.
2. **Data layer**: Connect existing data or create explicitly labeled mock content for a standalone prototype.
3. **Component drafting**: Use `resources/component-template.tsx` as a base. Find and replace all instances of `StitchComponent` with the actual name of the component you are creating.
4. **Application wiring**: Update the project entry point (like `App.tsx`) to render the new components.
5. **Quality check**:
    * Run `npm --prefix "$SKILL_DIR" run validate -- <file_path>` for each component.
    * Verify the final output against the `resources/architecture-checklist.md`.
    * Start the dev server with `npm run dev` to verify the live result.

## Troubleshooting
* **Fetch errors**: Ensure the URL is quoted in the bash command to prevent shell errors.
* **Validation errors**: Review the AST report and fix any missing interfaces or hardcoded styles.
## Shared contract

Follow [the shared skill contract](../../shared/COMMON-CONTRACT.md) for repo study, dirty-worktree hygiene, verification evidence, safe handoffs, and safety defaults.
