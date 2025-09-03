# prompt-to-json-enhanser

## 📌 Description

`prompt-to-json-enhancer` is a lightweight tool designed to capture natural language prompts and transform them into structured JSON outputs. The goal is to help developers, researchers, and content creators easily organize unstructured text into a machine-readable format for further use.

## 🎯 Goals

- Allow users to input free-form prompts.

- Enhance and convert the prompts into structured JSON.

- Provide options to export, save, or copy the generated JSON for reuse.

## 👤 User Stories

### 1. Capture Prompts

- As a user, I want to type or paste my prompt into an input field so that I can start the transformation process.

### 2. Transform to JSON

- As a user, I want the system to automatically transform my input prompt into a clean JSON structure so that I can use it in my applications.

### 3. Export / Save or Copy

- As a user, I want to copy the generated JSON to my clipboard or download it as a file so that I can easily use it in my projects.

## 🛠 How I Will Implement

### ⚡ Tech Stack Decision

- Frontend / UI: React + TypeScript + Vite (for a fast and modern web app).

- Browser Extension: Chrome Manifest V3 (popup with shared logic).

- Backend (optional): Node.js + Express (only if server-side persistence/export is needed).

- Schema Validation: JSON Schema (`ajv` or similar validator).

- Testing: Jest (unit + schema validation tests).

### 🔄 Processing Pipeline Overview

The application will follow a structured pipeline:

1. Capture → Take raw user input (prompt via UI or extension).

2. Normalize → Clean and standardize input (trim spaces, unify casing, remove noise).

3. Parse → Extract potential intents, entities, constraints using rule-based + regex logic.

4. Enhance → Map parsed data to structured fields (intent, entities, constraints, metadata).

5. Validate → Check against `prompt_schema.json` to ensure consistent structure.

6. Output → Show JSON in UI, with options to copy or export.

### 📦 Planned Classes & Functions

Core Classes (src/)

- `PromptProcessor`

  - **Role**: High-level orchestrator for the pipeline.

  - **Methods**:

    - `process(rawPrompt: string): object` → Runs full pipeline (Capture → Output).

- `Normalizer`

  - **Role**: Cleans and standardizes input.

  - **Methods**:

    - `normalizeText(text: string): string`

- `Parser`

  - **Role**: Extracts intents, entities, and constraints.

  - **Methods**:

    - `extractIntent(text: string): string`

    - `extractEntities(text: string): string[]`

    - `extractConstraints(text: string): string[]`

- `Enhancer`

  - **Role**: Builds structured JSON with metadata.

  - **Methods**:

    - `buildJSON(rawPrompt: string, parsedData: object): object`

- `Validator`

  - **Role**: Ensures JSON matches schema.

  - **Methods**:

    - `validateAgainstSchema(json: object): boolean`

Utility Functions (src/utils/)

- `generateUUID(): string` → Generates unique IDs.

- `getTimestamp(): string` → Returns ISO timestamp.

- `copyToClipboard(json: object): void` → Copies output JSON.

- `downloadAsFile(json: object, filename: string): void` → Exports JSON
