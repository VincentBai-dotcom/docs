# Documentation outline draft

Date: 2026-05-02
Status: Draft

## Goal

Design a documentation information architecture that supports both:

- a guided learning path for developers building their first game
- a fast lookup path for experienced users who need exact concepts or APIs

This draft assumes the published docs should avoid a public `Examples` section for now because the current example implementation is based on an existing commercial game.

## Proposed navigation outline

# Learn

## Quickstart
### Installation
### Build your first game

## Build your game
### Define your game state
### Define your commands
### Define your stages
### Assemble the game definition
### Add game rules and validation
### Model hidden information
### Return sanitized views to players
### Test commands
### Test stage transitions
### Test full game flows
### Test hidden information behavior
### Reproduce bugs with snapshots and replay

## Connect the engine
### Generate protocol artifacts
### Use the client SDK
### Connect a frontend
### Connect a server transport
### Keep clients in sync

# Reference

## Core types
### Game definition
### State schema types
### State decorators
### Visibility types
### Snapshot types
### Replay types

## Authoring APIs
### `createGameDefinitionBuilder`
### `createCommandFactory`
### `createStageFactory`
### `configureVisibility`
### `defineConfig`

## Runtime APIs
### `createGameExecutor`
### Execution result
### Game events
### Command discovery
### Stage progression

## Testing APIs
### `runScenario`
### Snapshot helpers
### Replay helpers

## CLI
### Overview
### `generate`
### `validate`
### Configuration
### Flags

## Protocol
### Overview
### AsyncAPI generation
### Client SDK generation
### Transport contract
### Sync model

## Rationale

This outline uses a two-track model:

- `Learn` for guided progression
- `Reference` for direct lookup

That split matches the dual goal of serving both first-time users and experienced users. A single mixed sidebar would force tutorial content and API content into the same navigation model, which usually makes both harder to use.

The `Learn` section is organized around developer workflow. Instead of isolating all concepts in a separate conceptual block, the draft introduces concepts when a developer needs them:

- state while defining the game model
- commands while defining player actions
- stages while defining flow control
- visibility when hidden information becomes relevant

This reflects how the product is likely to be learned in practice. Developers usually understand the abstractions better when they appear in the context of a concrete authoring task.

The `Quickstart` section is intentionally small. It follows a pattern closer to `react.dev`:

- one page for the core mental model
- one page for installation
- one page for a first guided build

This keeps the entry path approachable while still giving users a concrete end-to-end success case.

The deeper authoring guidance then moves into `Build your game`, which is where generalized patterns and more complete explanations belong.

`Connect the engine` is promoted to a first-class section because it represents a real milestone in adoption:

- first make the engine work
- then integrate it into a client-server system

The `Reference` section is grouped by use case rather than by repository folder:

- core types for foundational data structures
- authoring APIs for game definition work
- runtime APIs for execution behavior
- testing, CLI, and protocol for supporting surfaces

This should make lookup faster than mirroring the package file layout directly.

## Open questions

1. `Build your first game` needs a sample game that is legally safe, small, and representative of the engine.
2. The current draft assumes advanced constraints and guarantees will be explained within relevant reference pages instead of as a dedicated group.
