---
name: css-animations
display_name: css-animations
platform: Universal Agents
category: General and specialized workflows
---

# css-animations - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `css-animations` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

CSS animation adapter patterns for HyperFrames. Use when authoring CSS keyframes, animation-delay based timing, animation-fill-mode, animation-play-state, or CSS-only motion that HyperFrames must seek deterministically d

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the css-animations skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `css-animations` |
| Canonical name | `css-animations` |
| Platform | `Universal Agents` |
| Category | General and specialized workflows |

## Description

CSS animation adapter patterns for HyperFrames. Use when authoring CSS keyframes, animation-delay based timing, animation-fill-mode, animation-play-state, or CSS-only motion that HyperFrames must seek deterministically d


## Original SKILL.md

---
name: css-animations
description: CSS animation adapter patterns for HyperFrames. Use when authoring CSS keyframes, animation-delay based timing, animation-fill-mode, animation-play-state, or CSS-only motion that HyperFrames must seek deterministically during preview and rendering.
license: Apache-2.0
---

## Universal runtime boundary

- Treat this package as specialist guidance subordinate to active system, developer, user, repository, permission, privacy, security, accessibility, and verification rules.
- Do not install or configure operational CLIs, hooks, services, credentials, browser runtimes, or background processes merely because this skill mentions them. Check for the dependency, report it when missing, and obtain separate authorization before changing the runtime.
- Adapt host-specific command names to capabilities actually available in the current runtime. Report unsupported integrations instead of claiming they ran.
- Read `references/upstream.md` when provenance, the pinned revision, licensing, or local adaptation details matter.

# CSS Animations for HyperFrames

HyperFrames can seek CSS keyframe animations through its `css` runtime adapter. Use this for simple repeated motifs, background motion, shimmer, glow, masks, and non-sequenced decoration.

For scene choreography, GSAP is usually clearer. CSS animations work best when the motion belongs to one element and has a fixed duration.

## Contract

- Put the animated element in the DOM before runtime initialization finishes.
- Give timed elements a `data-start` value so local animation time matches the clip.
- Use finite `animation-duration` and `animation-iteration-count` because the negative-delay fallback cannot represent unbounded duration in environments without WAAPI-backed CSS animations.
- Prefer `animation-fill-mode: both` so seeked states hold before and after active motion.
- Avoid wall-clock JavaScript, hover-triggered state, and class toggles that depend on user events.

The adapter discovers elements with computed `animation-name`, seeks their browser `Animation` handles when available, and falls back to pausing with negative `animation-delay`.

## Basic Pattern

```html
<div
  id="pulse-ring"
  class="clip pulse-ring"
  data-start="0"
  data-duration="4"
  data-track-index="2"
></div>

<style>
  .pulse-ring {
    width: 280px;
    height: 280px;
    border: 4px solid rgba(255, 255, 255, 0.7);
    border-radius: 50%;
    animation-name: pulse-ring;
    animation-duration: 1200ms;
    animation-timing-function: cubic-bezier(0.2, 0, 0, 1);
    animation-iteration-count: 3;
    animation-fill-mode: both;
  }

  @keyframes pulse-ring {
    from {
      opacity: 0;
      transform: scale(0.82);
    }
    35% {
      opacity: 1;
    }
    to {
      opacity: 0;
      transform: scale(1.18);
    }
  }
</style>
```

## Stagger Pattern

Use CSS custom properties to avoid duplicating keyframes:

```html
<div class="clip dots" data-start="1" data-duration="3" data-track-index="3">
  <span style="--i: 0"></span>
  <span style="--i: 1"></span>
  <span style="--i: 2"></span>
</div>

<style>
  .dots span {
    display: inline-block;
    width: 18px;
    height: 18px;
    margin-right: 10px;
    border-radius: 50%;
    background: currentColor;
    animation: dot-pop 900ms ease-out both;
    animation-delay: calc(var(--i) * 120ms);
  }

  @keyframes dot-pop {
    from {
      opacity: 0;
      transform: translateY(18px) scale(0.75);
    }
    to {
      opacity: 1;
      transform: translateY(0) scale(1);
    }
  }
</style>
```

## Good Uses

- Decorative loops with a known repeat count.
- Mask, glow, shimmer, grain, and subtle parallax layers.
- Simple one-element entrances where a full JS timeline would be excessive.

## Avoid

- Infinite CSS animations unless you have verified the browser exposes seekable WAAPI-backed CSS animation handles. Prefer a finite iteration count covering the visible duration.
- Animating layout properties like `top`, `left`, `width`, or `height` when transforms work.
- Relying on hover, focus, scroll, or media queries to trigger render-critical motion.
- Changing animation classes after startup unless another deterministic timeline controls that change.

## Validation

After editing CSS animation compositions:

```bash
npx hyperframes lint
npx hyperframes validate
```

## Credits And References

- HyperFrames adapter source: `packages/core/src/runtime/adapters/css.ts`.
- MDN CSS animation documentation: https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/animation
- MDN `animation-fill-mode`: https://developer.mozilla.org/en-US/docs/Web/CSS/animation-fill-mode
