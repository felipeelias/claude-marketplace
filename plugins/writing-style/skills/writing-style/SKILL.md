---
name: writing-style
description: >
  This skill should be used when the user asks to "write a blog post",
  "draft a post", "write a PR description", "review my writing",
  "edit this draft", "check my writing style", or when any task involves
  producing or editing prose such as blog posts, PR descriptions,
  announcements, or documentation.
---

# Writing Style

Personal writing style skill. Apply when generating or reviewing prose.

## Format Detection

Before writing or reviewing, determine the format:

1. **Blog post**: writing for the Jekyll blog, markdown with front matter. Consult `references/blog-post.md` for structure and conventions.
2. **PR description**: writing a pull request body for GitHub. Consult `references/pr-description.md` for structure and style.
3. **Unknown**: anything else (commit message, docs, README, comment)

If the format is **unknown**, apply only the Voice Rules and AI Pattern Detection below. Do not force a structure template on content that does not match a known format.

## Voice Rules (Always Apply)

These rules apply to all writing, regardless of format.

### Tone

- Builder who writes about what he's made and why
- First person, practical, no posturing
- Smart but not academic
- Personal but not confessional
- Opinionated but fair: mention alternatives, link to competitors
- State motivation in one sentence and move on
- Trust the reader to figure out why they should care

### Sentence Level

- Short sentences. Rarely past 25 words.
- Lead with the concrete thing, not the abstract framing.
- Parentheticals for small asides rather than separate sentences.
- Colons to introduce lists, explanations, or examples.
- No em dashes. Use colons, commas, or restructure.

### Blacklisted Phrases

Never use these phrases or patterns:

- "In this post, I'll show you..."
- "Let's dive in" / "Without further ado"
- "You might be wondering..." / "You're probably wondering..."
- "In conclusion" / "To wrap up" / "To summarize"
- "It's worth noting that" / "One thing to note is that"
- "Game-changer" / "Powerful" / "Robust" / "Elegant" / "Seamless"
- "Leverage" / "Utilize" (use "use")
- "Ecosystem" / "Deep dive" / "At the end of the day"
- "Scratch my own itch"
- Hedges: "actually", "maybe", "just", "simply", "really"

### Patterns to Avoid

- Preambles that sell the importance of the topic before getting into it
- Summary/conclusion sections restating what was covered
- Rhetorical questions as transitions between sections
- Reader-mind-reading ("you might think", "you're probably wondering")
- Correlative constructions ("not X, but Y") as a rhetorical device
- Symmetrical constructions that sound polished but say nothing
- Abstract analysis without personal stakes or concrete examples

## AI Pattern Detection (Always Apply)

Scan all output for these AI writing tells. Based on [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing).

### AI Vocabulary

These words appear far more frequently in AI text. Avoid or replace: Additionally, align with, crucial, delve, emphasizing, enduring, enhance, fostering, garner, highlight (verb), interplay, intricate/intricacies, key (adjective), landscape (abstract noun), pivotal, showcase, tapestry (abstract noun), testament, underscore (verb), valuable, vibrant

### Significance Inflation

AI puffs up importance. Watch for: stands/serves as, is a testament/reminder, vital/significant/crucial/pivotal role/moment, underscores/highlights its importance, reflects broader, symbolizing its ongoing/enduring/lasting, setting the stage for, marking/shaping the, represents/marks a shift, key turning point, evolving landscape, indelible mark

"The library was established in 1989, marking a pivotal moment in regional education." -> "The library was established in 1989."

### Promotional Language

Watch for: boasts a, vibrant, rich (figurative), profound, enhancing its, showcasing, exemplifies, commitment to, natural beauty, nestled, in the heart of, groundbreaking, renowned, breathtaking, must-visit, stunning

### Copula Avoidance

AI substitutes elaborate constructions for simple "is"/"are"/"has". Watch for: serves as, stands as, marks, represents, boasts, features, offers

"Gallery 825 serves as the exhibition space." -> "Gallery 825 is the exhibition space."

### Structural Tells

- **Rule of three**: AI forces ideas into groups of three. Break them up.
- **Synonym cycling**: AI uses different words for the same thing across sentences to avoid repetition. Just use the same word.
- **False ranges**: "from X to Y" constructions where X and Y aren't on a meaningful scale.
- **Negative parallelisms**: "Not only...but...", "It's not just about..., it's..."
- **Formulaic challenges sections**: "Despite its... faces several challenges... Despite these challenges..."

### Style Tells

- **Boldface overuse**: AI emphasizes phrases mechanically. Use bold sparingly.
- **Inline-header lists**: bolded headers followed by colons in list items. Convert to prose or plain lists.
- **Title case in headings**: use sentence case instead.

### Communication Artifacts

Never leave these in output:

- Collaborative: "I hope this helps", "Of course!", "Certainly!", "Would you like...", "Let me know"
- Sycophantic: "Great question!", "You're absolutely right!", "That's an excellent point"
- Disclaimers: "as of [date]", "based on available information", "While specific details are limited..."

### Filler Phrases

- "In order to" -> "To"
- "Due to the fact that" -> "Because"
- "At this point in time" -> "Now"
- "In the event that" -> "If"
- "has the ability to" -> "can"
- "It is important to note that" -> just state the thing

### Generic Conclusions

"The future looks bright. Exciting times lie ahead." -> Replace with a specific fact, or remove entirely.

## Reviewing Existing Text

When asked to review or edit existing writing:

1. Identify the format (blog post, PR description, or unknown)
2. Check against Voice Rules: blacklisted phrases, sentence length, tone
3. Check against AI Pattern Detection: vocabulary, significance inflation, structural tells
4. Check against format-specific rules if applicable
5. Flag specific issues with concrete suggestions
6. Do not rewrite unless asked. Point out problems, let the author fix them.

## Revision Checklist

After drafting or reviewing, verify:

1. Does it start with the thing, not the context?
2. Is the intro under 2 sentences?
3. Is there a pointless conclusion? Remove it.
4. Any blacklisted phrases? Remove them.
5. Any sentence over 25 words? Break it up or cut it.
6. Does every paragraph earn its place, or is it filler?
7. Would I actually say this out loud? If not, rewrite.
8. Anti-AI pass: re-read the output and ask "what makes this obviously AI generated?" Fix any remaining tells.
