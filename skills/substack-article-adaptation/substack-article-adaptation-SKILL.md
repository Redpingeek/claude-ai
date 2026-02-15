---
name: substack-article-adaptation
description: >
  Deterministic 3-checkpoint workflow that transforms blog posts into Substack-optimized articles
  with consistent voice, structure, and positioning for email audiences. Maintains Andrea's voice
  (technical but accessible, no corporate jargon) while adapting content from blog readers to
  email subscribers. Use when adapting Red Pin Geek blog posts for Substack Premium subscribers.
---

# Substack Article Adaptation Engine

Transform blog posts into Substack-optimized articles through 3 structured review checkpoints with consistent voice and positioning.

## When to Use This Skill

- Adapting Red Pin Geek blog posts for Substack Premium subscribers
- Converting case studies for email distribution
- Repurposing educational content for engaged audience
- **Do NOT use for:** Creating original Substack content, social media posts, or content targeting cold audiences

## Workflow

### **Step 1: Fetch Blog Content**

**Process:**
1. Call `web_fetch` tool with blog URL
2. Extract main content (title, body, sections, examples)
3. Identify key concepts, proof points, CTAs

**Error Handling:**
- If fetch fails → Ask user to verify URL or paste content directly
- If content < 500 words → Ask if user wants to proceed or choose different post
- If content is primarily images → Flag and suggest alternative format

---

### **Step 2: CHECKPOINT 1 - Structure & Positioning Review**

**Process:**
1. Generate adapted headline (outcome-focused for email)
2. Write hook (first 2 sentences, grabs attention)
3. Create section outline (7-9 sections typical)
4. Position for Substack audience (email subscribers who know Andrea)

**Present to user:**
```
Here's the structure and positioning. Review:
(1) Does the headline hook your Substack audience?
(2) Does the section flow work?
(3) What needs adjustment?
```

**Decision Criteria:**

**Accept when:**
- Headline clearly positions Substack angle (not just blog recycling)
- Section flow builds logically for email readers
- Hook engages within first 2 sentences

**Refine when:**
- Headline is accurate but not compelling
- Sections are out of order or need consolidation
- Hook buries the lead

**Redirect when:**
- Positioning misses Substack audience entirely
- Structure requires blog-style navigation
- Approach doesn't align with current content strategy

---

### **Step 3: CHECKPOINT 2 - Body Content Review**

**Process:**
1. Write full article body with Andrea's voice
2. Include examples from original blog
3. Add conversational CTAs (not salesy)
4. Maintain technical accuracy with accessible language

**Present to user:**
```
Here's the full draft. Review:
(1) Does this sound like Andrea?
(2) Are examples/stories working?
(3) Do CTAs feel natural?
```

**Decision Criteria:**

**Accept when:**
- Voice sounds like Andrea (technical but accessible, no corporate jargon)
- Examples are specific and relevant to jewelry/creative businesses
- CTAs feel conversational, not salesy

**Refine when:**
- Tone is slightly off (too formal/informal)
- Examples are generic or need swapping
- CTAs need repositioning or softer language

**Redirect when:**
- Voice is fundamentally wrong (sounds like different person)
- Content strays from original blog's core value
- CTAs push products instead of inviting engagement

---

### **Step 4: CHECKPOINT 3 - Final Polish Review**

**Process:**
1. Incorporate user feedback from Checkpoint 2
2. Final proofread for typos, flow, consistency
3. Verify all links work
4. Confirm CTAs are correctly placed

**Present to user:**
```
Final version based on your feedback. Ready to publish or what else needs adjustment?
```

**Decision Criteria:**

**Accept when:**
- All checkpoint feedback incorporated accurately
- No new issues introduced during revision
- Feels ready to copy-paste into Substack

**Refine when:**
- Minor wording tweaks needed
- One section still feels off
- CTA placement could be better

**Redirect when:**
- Major feedback was missed or misinterpreted
- Revision created new problems
- Need to revisit positioning from Checkpoint 1

---

## Voice Guidelines

**Andrea's Voice Characteristics:**
- Technical but accessible (explains concepts simply)
- No corporate jargon or marketing speak
- Direct and confident
- Educational without being condescending
- Uses specific examples from jewelry/creative business world
- Conversational CTAs (invitations, not pressure)

**Avoid:**
- Overly poetic language
- Generic business advice
- Salesy product pushes
- Vague platitudes
- Industry buzzwords without explanation

---

## Error Handling

### **Blog URL Fetch Failure**
- **Symptoms:** 404, authentication required, paywall, timeout
- **Action:** Ask user to verify URL or paste content directly

### **Voice Mismatch**
- **Symptoms:** User says "doesn't sound like me"
- **Action:** Ask for voice sample (2-3 sentences), request specifics on what feels off

### **Incomplete Blog Content**
- **Symptoms:** < 500 words, missing sections, primarily images
- **Action:** Ask if user wants to proceed or choose different post

### **CTA/Link Broken**
- **Symptoms:** Premium link 404, outdated URLs
- **Action:** Flag immediately, request correct URL

### **Checkpoint Approval Ambiguity**
- **Symptoms:** "Mostly good", "fine I guess", partial approval
- **Action:** Seek specificity, present options, treat as "refine" not "accept"

### **Substack Formatting Issues**
- **Symptoms:** Markdown doesn't render, broken headers, plain text links
- **Action:** Provide clean markdown, note common fixes

### **Content Too Long**
- **Symptoms:** > 2,500 words
- **Action:** Suggest split into parts or condensation

### **Missing Context**
- **Symptoms:** Blog assumes knowledge unfamiliar to email subscribers
- **Action:** Add 1-2 sentences context for email-only readers

---

## Output

Deliver the final Substack article with:
- Subject line
- Complete article body in Substack markdown format
- All links verified
- CTAs properly positioned

Tell the user: "Here's your publication-ready Substack article. Copy-paste into your Substack editor."

---

## Performance Metrics

**Target benchmarks:**
- Time per adaptation: < 30 minutes
- Checkpoint rejection rate: < 10%
- Voice match accuracy: User approval on first draft
- Zero revisions needed across checkpoints (ideal state)

**Tested consistency:** 100% success rate across 3 different blog posts
