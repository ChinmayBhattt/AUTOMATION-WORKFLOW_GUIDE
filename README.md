# AUTOMATION-WORKFLOW_GUIDE


# Nano Banana 2 - Master JSON Prompt Reference Guide

This guide defines the ultimate JSON schema for prompting the Nano Banana 2 (Gemini 3.1 Flash) AI image generation model. Using this structured format ensures high consistency, detailed control, and takes advantage of the model's precise instruction-following capabilities.

## The JSON Schema

```json
{
  "prompt": "string - A dense, ultra-descriptive narrative merging subject, outfit, environment, and camera details. Use highly specific, unflattering language to force realism. (e.g., 'Ultra-realistic close-up mirror selfie... Natural male skin texture with visible pores, mild redness, subtle freckles, light acne marks. No makeup, no grooming enhancement. Direct on-camera flash creating sharp highlights. 85mm lens, f/1.8, ISO 200. Documentary realism. Do not beautify or alter facial features.')",
  
  "negative_prompt": "string - Comma-separated list of blockers (e.g., 'blurry, low resolution, distorted face, extra fingers, overexposed, heavy makeup, unrealistic skin, cartoon, CGI, oversaturated colors, anatomy normalization, datasets-average body')",
  
  "settings": {
    "resolution": "string - e.g., '1024x1792', '4k'",
    "style": "string - e.g., 'photorealistic, documentary realism', 'candid amateur', 'fashion photography, flash photography'",
    "lighting": "string - e.g., 'natural golden hour', 'harsh overhead fluorescent', 'direct on-camera flash, high contrast'",
    "camera_angle": "string - e.g., 'high-angle arm-extended selfie', 'side profile view'",
    "depth_of_field": "string - e.g., 'shallow depth of field', 'deep, infinite focus'",
    "quality": "string - e.g., 'high detail, unretouched skin', 'visible film grain, slightly soft'"
  }
}
```

## How to Use This Dual Paradigm

You now have two core ways to construct a prompt:

1.  **The Dense Narrative (Classic V4 Paradigm):** Use the dense text-based `prompt` string when feeding a standard model/API. **Language Masterclass:** Use explicit camera mathematics (`85mm lens, f/2.0, ISO 200`), explicitly call for imperfections (`mild redness, light acne marks`), describe lighting behavior (`creating sharp highlights on skin`), and include direct negative commands *within* the positive prompt (`Do not beautify or alter facial features`, `unretouched skin`).
2.  **The Deep Grid (V3 Paradigm):** If you need absolute 2x2 grid control or explicit JSON constraints to break the model's structure down, map it out using the complex JSON objects (subject, lighting, camera).

When sending data to the **Kie.ai API**, compile your choices into a single JSON object (using the Dense Narrative structure above) and pass it as a stringified payload into the `input.prompt` field!
{
  "task": "string - High-level goal (e.g., 'sports_selfie_collage', 'single_macro_portrait')",
  
  "output": {
    "type": "string - e.g., 'single_image', '4-panel_collage'",
    "layout": "string - e.g., '1x1', '2x2_grid', 'side-by-side'",
    "aspect_ratio": "string - e.g., '3:4', '16:9', '4:5'",
    "resolution": "string - e.g., 'ultra_high', 'medium_low'",
    "camera_style": "string - e.g., 'smartphone_front_camera', 'professional_dslr'"
  },

  "image_quality_simulation": {
    "sharpness": "string - e.g., 'tack_sharp', 'slightly_soft_edges'",
    "noise": "string - e.g., 'unfiltered_sensor_grain', 'visible_film_grain', 'clean_digital'",
    "compression_artifacts": "boolean - true if attempting to simulate uploaded UGC",
    "dynamic_range": "string - e.g., 'limited', 'hdr_capable'",
    "white_balance": "string - e.g., 'slightly_warm', 'cool_fluorescent'",
    "lens_imperfections": [
      "array of strings - e.g., 'subtle chromatic aberration', 'minor lens distortion', 'vignetting'"
    ]
  },

  "subject": {
    "identity": "string - Specific identity or consistency tags.",
    "appearance": {
      "gender_or_type": "string",
      "age_or_condition": "string",
      "ethnicity_or_origin": "string",
      "skin_texture": "string - Highly specific, e.g., 'realistic, visible pores, natural imperfections'",
      "hair": "string - e.g., 'natural blonde, tied back in sporty ponytail'",
      "makeup": "string - e.g., 'minimal, natural, slightly flushed from activity'",
      "expression": "string - e.g., 'casual confident smile, candid selfie energy'"
    },
    "outfit": {
      "type": "string - e.g., 'sporty', 'casual streetwear'",
      "top": "string - e.g., 'athletic sports bra'",
      "bottom": "string - e.g., 'high-waisted leggings'",
      "colors": "string - e.g., 'neutral or soft sporty tones'"
    }
  },

  "multi_panel_layout": {
    "grid_panels": [
      {
        "panel": "string - e.g., 'top_left', 'full_frame' (if not a grid)",
        "pose": "string - e.g., 'slight upward selfie angle, relaxed smile'",
        "action": "string - e.g., 'holding phone with one hand, casual posture'"
      }
    ]
  },

  "environment": {
    "location": "string - e.g., 'gym or outdoor sports area'",
    "background": "string - What is behind the subject (e.g., 'blurred gym equipment')",
    "lighting": {
      "type": "string - e.g., 'natural or overhead gym lighting', 'harsh direct sunlight'",
      "quality": "string - e.g., 'uneven, realistic, non-studio', 'high-contrast dramatic'"
    }
  },

  "embedded_text_and_overlays": {
    "text": "string (optional)",
    "location": "string (optional)"
  },

  "structural_preservation": {
    "preservation_rules": [
      "array of strings - e.g., 'Exact physical proportions must be preserved'"
    ]
  },

  "controlnet": {
    "pose_control": {
      "model_type": "string - e.g., 'DWPose'",
      "purpose": "string",
      "constraints": ["array of strings"],
      "recommended_weight": "number"
    },
    "depth_control": {
      "model_type": "string - e.g., 'ZoeDepth'",
      "purpose": "string",
      "constraints": ["array of strings"],
      "recommended_weight": "number"
    }
  },

  "explicit_restrictions": {
    "no_professional_retouching": "boolean - typically true for realism",
    "no_studio_lighting": "boolean - typically true for candid shots",
    "no_ai_beauty_filters": "boolean - mandatory true to avoid plastic look",
    "no_high_end_camera_look": "boolean - true if simulating smartphones"
  },

  "negative_prompt": {
    "forbidden_elements": [
      "array of strings - Massive list of 'AI style' blockers required for extreme realism. Example stack: 'anatomy normalization', 'body proportion averaging', 'dataset-average female anatomy', 'wide-angle distortion not in reference', 'lens compression not in reference', 'cropping that removes volume', 'depth flattening', 'mirror selfies', 'reflections', 'beautification filters', 'skin smoothing', 'plastic skin', 'airbrushed texture', 'stylized realism', 'editorial fashion proportions'."
    ]
  }
}
```

## How to Use This Template

This reference guide is designed to produce **hyper-realistic, consistently structured images**. When generating prompts for Nano Banana 2:

1. **Be Granular, Not Vague:** Do not just say "a woman." Use the `character_or_object_details` block to define exactly how the skin reflects light, the specific clothing material, and micro-textures like pores or weathering.
2. **Lock the Camera and Light:** Real photography relies on physics. Always define the `lens` (e.g., "90mm macro"), the `camera.height`, and the exact `lighting.direction`.
3. **Use the `structural_preservation` Block:** If you are trying to maintain exact body types, physical laws, or character consistency, use this block to explicitly tell the model *not* to average out the data.
4. **Heavily Populate the `negative_prompt`:** To combat "AI look," you must explicitly forbid "plastic skin," "smoothing," "beautification filters," and "anatomy normalization."
5. **Drop Unused Fields:** If you are generating a landscape, omit the `pose_and_action` block entirely. The JSON should only contain blocks relevant to the scene.

## Best Practices for Nano Banana 2 Prompting

1.  **Leverage Character Consistency:** Use the `character_consistency_tags` to define specific traits you want to persist if we are generating multiple shots of the same subject.
2.  **Exploit Text Accuracy:** Nano Banana 2 is exceptionally good at text rendering. If you want neon signs, graffiti, or labels, explicitly state the exact string in `text_elements`.
3.  **High-Fidelity Textures:** The model excels at photorealism and textures. Be specific in `style_and_rendering` (e.g., "visible film grain", "hyper-detailed skin pores").
4.  **Keep it Focused:** While JSON allows for massive detail, start with the core elements (Subject, Lighting, Style) before overly complicating the scene.
5.  **Use Iteration:** We will use this schema to generate an initial image, review, and then simply tweak one or two JSON values (like `lighting_style` or `camera_angle`) for the next generation.


```

---
name: skill-builder
description: Use when creating new skills, optimizing existing skills, or auditing skill quality. Guides skill development following Claude Code official best practices.
---

## What This Skill Does

Guides the creation and optimization of Claude Code skills using official best practices. Use this whenever:

- Building a new skill from scratch
- Optimizing or auditing an existing skill
- Deciding on advanced features (subagent execution, hooks, dynamic context, etc.)
- Troubleshooting a skill that isn't working correctly

For the complete technical reference on all frontmatter fields, advanced patterns, and troubleshooting, see [reference.md](reference.md).

## Quick Start: What Is a Skill?

A skill is a reusable set of instructions that tells Claude Code how to handle a specific task. Skills live in `.claude/skills/[skill-name]/SKILL.md` inside your project. When you type `/skill-name` or describe what you need in natural language, Claude loads the skill's instructions and follows them.

Think of skills as SOPs for Claude. Instead of re-explaining a workflow every conversation, you write it once and invoke it forever.

**How they work under the hood:**
- Your project's `CLAUDE.md` instructions are always loaded, every conversation
- Skill *descriptions* (from frontmatter) are always loaded so Claude knows what's available
- The full skill content only loads when the skill is actually invoked
- Once loaded, Claude follows the skill's instructions while still respecting your CLAUDE.md rules

---

## Mode 1: Build a New Skill

When building a new skill, run the **Discovery Interview** first. Do NOT start writing files until discovery is complete.

### Discovery Interview

Ask questions using AskUserQuestion, one round at a time. Each round covers one topic. Move to the next round only after the user answers. Keep going until you're 95% confident you understand the skill well enough to build it without further clarification.

**Round 1: Goal & Name**
*Why this matters: A clear goal prevents scope creep. The name becomes the `/slash-command`, so it needs to be memorable and specific.*

- What does this skill do? What problem does it solve or what workflow does it automate?
- What should we call it? (Suggest a name based on their answer -- lowercase, hyphens, max 64 chars)

**Round 2: Trigger**
*Why this matters: The `description` field is how Claude decides whether to load your skill. Bad trigger words mean Claude never uses it. Too broad means Claude fires it when you don't want it.*

- What would someone say to trigger this? (Get 2-3 natural language phrases)
- Should it be user-only (`/slash-command`), Claude-auto-invocable, or both?
- Does it accept arguments? If so, what? (e.g., a topic, a URL, a file path)

**Round 3: Step-by-Step Process**
*Why this matters: Claude follows instructions literally. Vague steps produce vague results. Specific steps produce consistent output every time.*

- Walk me through exactly what should happen from trigger to output. What's step 1? Step 2? Keep going.
- For each step: Does Claude do it directly, or delegate to a subagent/script?
- Does this need to be conversational (back-and-forth with the user) or is it a fire-and-forget task?

**Round 4: Inputs, Outputs & Dependencies**
*Why this matters: Skills that don't specify where to find inputs or where to put outputs produce inconsistent results. Nailing this down makes the skill reliable.*

- What inputs does the skill need? (Files, API responses, user arguments, live data)
- What does it produce? (Files, text output, structured data) Where do outputs go?
- Does it need external APIs, scripts, or tools? Which ones?
- Does it need reference files, style guides, templates, or examples?

**Round 5: Guardrails & Edge Cases**
*Why this matters: Skills without guardrails can produce unexpected behavior -- wrong outputs, unnecessary API costs, or actions you didn't intend.*

- What could go wrong? What are the common failure modes?
- What should this skill NOT do? Any hard boundaries?
- Are there cost concerns? (API calls, AI image generation, etc.)
- Any ordering or dependency constraints? (e.g., "must check X before doing Y")

**Round 6: Confirmation**
*Why this matters: Misunderstandings caught here save you from rebuilding the skill later.*

After all rounds, summarize your understanding back to the user in this format:

```
## Skill Summary: [name]

**Goal:** [one sentence]
**Trigger:** `/name` + [natural language phrases]
**Arguments:** [what it accepts, or "none"]

**Process:**
1. [step]
2. [step]
...

**Inputs:** [what it reads/needs]
**Outputs:** [what it produces + where]
**Dependencies:** [APIs, scripts, agents, reference files]
**Guardrails:** [what can go wrong, what to avoid]
```

Ask: "Does this capture it? Anything to add or change?" Only proceed to building once the user confirms.

**Skipping rounds:** If the user provides enough context upfront (e.g., they describe the full workflow in their first message), skip rounds that are already answered. Don't re-ask what you already know.

### Build Phase

Once discovery is complete, build the skill following these steps:

**Step 1: Choose the skill type**

- **Task skills** (most common) give step-by-step instructions for a specific action. Invoked with `/name` or natural language. Examples: generate a report, summarize a PR, deploy code.
- **Reference skills** add knowledge Claude applies to current work without performing an action. Examples: coding conventions, API patterns, style guides.

**Step 2: Configure frontmatter**

Set these fields based on what you learned in discovery:

- `name` -- Matches the directory name. Lowercase, hyphens, max 64 chars.
- `description` -- Written as: "Use when someone asks to [action], [action], or [action]." Include natural keywords from the trigger phrases.
- `disable-model-invocation: true` -- Set if the skill has side effects (file generation, API calls, costs money). Prevents Claude from auto-invoking.
- `argument-hint` -- Set if the skill accepts arguments. Shows in the `/` menu autocomplete.
- `context: fork` + `agent` -- Set if the skill is self-contained and doesn't need conversation history.
- `model` -- Set if a specific model capability is needed.
- `allowed-tools` -- Set if the skill should have restricted tool access.

Only set fields you actually need. Don't add frontmatter just because you can.

For the full field reference and invocation control matrix, see [reference.md](reference.md).

**Step 3: Write the skill content**

Structure task skills as:
1. **Context** -- Files to read, APIs to call, reference material to load
2. **Step-by-step workflow** -- Numbered steps. Each step tells Claude exactly what to do.
3. **Output format** -- What the result looks like. Include templates, file paths, structured formats.
4. **Notes** -- Edge cases, constraints, what to delegate, what NOT to do.

Content rules:
- Keep SKILL.md under 500 lines. Move detailed reference material to supporting files.
- Use `$ARGUMENTS` / `$N` for dynamic input from arguments.
- Use `!`command`` for dynamic context injection (preprocessing).
- Be specific about agent delegation -- include exact prompt text.
- Specify all file paths (inputs, outputs, scripts, references).

**Step 4: Add supporting files (if needed)**

If your skill needs detailed reference docs, examples, or scripts, add them alongside SKILL.md in the same directory. Reference them from SKILL.md so Claude knows they exist. Supporting files are NOT loaded automatically -- they load only when Claude needs them. See [reference.md](reference.md) for the full pattern.

**Step 5: Document in CLAUDE.md**

Your project's `CLAUDE.md` file is where Claude loads project-wide instructions every conversation. After creating a skill, add a brief entry so you (and your team) know what's available:

- Skill name and `/slash-command`
- Trigger phrases
- Brief description of what it does
- Output location (if it produces files)

This isn't required for the skill to work, but it keeps your project organized and helps Claude understand how skills fit into your broader workflow.

**Step 6: Test**

Test both invocation methods:

1. **Natural language** -- Say something matching the description. Does Claude load the skill?
   - If not, revise the `description` field to include the keywords you used
   - Try 2-3 different phrasings to verify it triggers reliably
2. **Direct invocation** -- Run `/skill-name` with test arguments
   - Verify `$ARGUMENTS` / `$N` are substituting correctly
   - Check that outputs go where expected
3. **Edge cases** -- Try invoking with missing arguments, unusual input, or empty input
4. **Character budget** -- If you have many skills, run `/context` to confirm your skill's description is being loaded. If it's not, your total descriptions may exceed the budget (see [reference.md](reference.md) for details).

If issues arise, see Troubleshooting in [reference.md](reference.md).

### Complete Example

Here's a minimal but complete skill you can use as a starting template:

**File:** `.claude/skills/meeting-notes/SKILL.md`

```yaml
---
name: meeting-notes
description: Use when someone asks to summarize meeting notes, recap a meeting, or format meeting minutes.
argument-hint: [topic or date]
---

## What This Skill Does

Takes raw meeting notes and produces a structured summary with action items.

## Steps

1. Ask the user to paste their raw meeting notes (or provide a file path).
2. Extract the following from the notes:
   - **Attendees** -- Who was in the meeting
   - **Key decisions** -- What was decided
   - **Action items** -- Who owes what, with deadlines if mentioned
   - **Open questions** -- Anything unresolved
3. Format the output using the template below.
4. If $ARGUMENTS is provided, use it as the meeting title. Otherwise, infer a title from the content.

## Output Template

# Meeting: [title]
**Date:** [date if mentioned, otherwise "Not specified"]
**Attendees:** [comma-separated list]

## Key Decisions
- [decision]

## Action Items
- [ ] [person]: [task] (due: [date or "TBD"])

## Open Questions
- [question]

## Notes

- Keep summaries concise. Don't add commentary or embellish.
- If notes are too vague to extract action items, flag that to the user instead of making them up.
```

---

## Mode 2: Audit an Existing Skill

Use this checklist to audit any existing skill. Read the skill file first before running through the checklist. Fix issues before marking the audit complete.

### Frontmatter Audit

- [ ] `name` matches the directory name
- [ ] `description` uses natural keywords someone would actually say when they need this skill
- [ ] `description` is specific enough to avoid false triggers but broad enough to catch real requests
- [ ] `disable-model-invocation: true` is set if the skill has side effects (generates files, calls APIs, sends messages, costs money)
- [ ] `argument-hint` is set if the skill accepts arguments via `/name`
- [ ] `allowed-tools` is set if the skill should NOT have access to all tools
- [ ] `context: fork` is used if the skill is self-contained and produces verbose output
- [ ] `model` is set only if a specific model capability is needed
- [ ] No unnecessary fields are set (don't add frontmatter just because you can)

### Content Audit

- [ ] Total SKILL.md is under 500 lines (detailed reference moved to supporting files)
- [ ] Clear step-by-step workflow with numbered steps (for task skills)
- [ ] Output format is specified with templates or examples
- [ ] All file paths and locations are documented
- [ ] Agent delegation instructions include the actual prompt text to send
- [ ] Notes section covers edge cases, constraints, and what NOT to do
- [ ] No vague instructions -- every step tells Claude exactly what to do
- [ ] String substitutions (`$ARGUMENTS`, `$N`) are used where the skill takes input

### Integration Audit

- [ ] Skill is documented in CLAUDE.md (recommended, not required)
- [ ] Supporting files (if any) are referenced from SKILL.md, not orphaned
- [ ] Scripts (if any) have correct file paths and are executable
- [ ] API keys (if any) are stored in environment variables, never hardcoded

### Quality Audit

- [ ] A beginner could follow the instructions without prior context
- [ ] Instructions are actionable, not abstract
- [ ] Delegates to subagents when appropriate to keep main context clean
- [ ] Doesn't duplicate information that lives elsewhere (CLAUDE.md, other skills)
- [ ] Output paths follow a predictable convention

### Optimization Opportunities

After running the audit, check [reference.md](reference.md) for advanced features that could improve the skill: `context: fork`, `allowed-tools`, dynamic context injection, hooks, and supporting files.

---

## Recommended Conventions

Adapt these to fit your project:

- Skills live in `.claude/skills/[skill-name]/SKILL.md`
- Output files go in a predictable location (e.g., `output/[skill-name]/`)
- API keys go in environment variables, never hardcoded in skill files
- Document all active skills in your project's CLAUDE.md
- Frontmatter `description` is written as: "Use when someone asks to [action], [action], or [action]."

## Important Notes

- Always read an existing skill before optimizing it. Never propose changes to a skill you haven't read.
- When building a new skill, check if a similar skill already exists that could be extended instead.
- For advanced patterns (subagent execution, hooks, permissions), see [reference.md](reference.md).
# Nano Banana 2 - Gemini Project Organizer

This document tracks our progress, generated assets, and custom scripts for the Nano Banana 2 image generation project using Anti-Gravity and Gemini 3.1 Pro.

## Project Structure

It is critical to **always keep prompts and images organized** within the project directory.

- `/images/` - All generated images must be saved here. Keep them organized by category if necessary.
- `/prompts/` - Saved JSON prompt configurations corresponding to the generated images must be stored here.
- `/scripts/` - Utility scripts for batch processing, API interaction, or prompt generation.
- `master_prompt_reference.md` - The compiled JSON schema and guide (To be created).

## Image Generation Workflow

Whenever the user requests to generate an image, you must use the **Nano Banana image generation skill**. 

1. Use the skill to generate the image based on the user's requirements.
2. Save the resulting image to the correctly categorized subfolder inside the `/images/` directory (e.g., `/images/infographics/`). **If a specific category cannot be determined, save it to `/images/miscellaneous/`.** This is mandatory for every single generation.
3. Save the corresponding prompt configuration to the `/prompts/` directory, mirroring the exact same subfolder used for the image (e.g., `/prompts/infographics/` or `/prompts/miscellaneous/`).
4. **Parallel Processing:** When you are processing multiple images at the same time, you MUST run their generation commands in parallel to save time.

## Current Phase: Schema Validation

**Goal:** Generate complex test images using the newly designed JSON schema to validate its effectiveness. Ensure that any output generated is properly filed according to the project structure.

## Scripts Log

| Script Name | Purpose | Status |
|-------------|---------|--------|
| `generate_kie.py` | Python script to hit Kie.ai API, poll, and download image safely | Active |

