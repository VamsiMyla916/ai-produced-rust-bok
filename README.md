# AI produced Rust Body of Knowledge (BoK)

This repository contains the two prompts where one is used to generate the Body of Knowledge for the Rust programming language and the other one for evaluating the generated response using Large Language Models (LLMs) following the ACM CS2023 curriculum standards.

## Prompts Used

Below are the exact prompts used to generate and verify the curriculum.

### Prompt 1: The Generator (Creation): This prompt generates the actual curriculum. It includes strict template enforcement to ensure formatting and comparisons are included.

```
**System Role:**
Act as a Senior Computer Science Curriculum Designer. Construct a formal **Body of Knowledge (BoK)** for the **Rust Programming Language**.

**Objective:**
Generate a hierarchical knowledge structure strictly adhering to the **ACM CS2023** format. The content must be grounded in "Programming Rust" (Blandy & Orendorff) but expanded to include modern production tools.

**Strict Formatting Template:**
You **must** follow this exact layout for every Knowledge Unit. Do not deviate.

> **KA-RUST-[Number]: [Title]**
>
> - **KU-[Number]: [Subtitle]**
>   - **Topic:** [Concept Name]
>   - **Topic:** [Concept Name]
>   - **Comparative Context:**
>     - _vs. C++:_ [Specific comparison of overhead/safety]
>     - _vs. Java/GC:_ [Specific comparison of runtime model]

**Content Requirements (Pass/Fail Criteria):**

1.  **Comparisons are Mandatory:** Every single Knowledge Unit (KU) must end with a "Comparative Context" section. You must contrast Rust against C++, Java, or Go using metrics like "Runtime Overhead," "Memory Safety," or "Developer Ergonomics."
2.  **Production Ecosystem:** You must explicitly cover:
    - **Async:** The **Tokio** runtime (not just generic async).
    - **Web:** **Axum** or **Hyper**.
    - **Data:** **Polars** (DataFrames) and **Serde**.
    - **Unsafe:** FFI and raw pointers.
3.  **Terminology:** Use high-level systems terms: "Affine Types," "Monomorphization," "Vtables," "RAII."

**Task:**
Draft the full Body of Knowledge now. Ensure "Move Semantics," "Borrow Checker," and "Tokio" are prominent topics.
```

### Prompt 2: The Evaluator (Quality Assurance): This prompt helps to grade the output. If the first prompt missed anything, this prompt will force the AI to identify the missing pieces.

```
**System Role:**
Act as a strict Computer Science Professor and Rust Expert. I am submitting the following **Body of Knowledge (BoK)** for your review.

**Your Task:**
Grade this curriculum on a Pass/Fail basis against the **ACM CS2023 Systems Curriculum Standards**.

**Grading Checklist (You must verify each):**

1.  **Syntax Accuracy:** Is the generic notation (like `<T>`, `&mut T`) used correctly? (Pass/Fail)
2.  **Mandatory Tooling:** Does it explicitly list **Tokio** (runtime), **Axum** (web), **Polars** (data), and **Serde**? (Pass/Fail)
3.  **Comparative Rigor:** Does _every_ Knowledge Unit (KU) end with a specific "Comparative Context" section contrasting Rust vs. C++ or Java? (Pass/Fail)
4.  **Formatting:** Is the hierarchy clear (`KA` -> `KU` -> `Topic`), and are topics separated by newlines? (Pass/Fail)

**Output:**

- If **PASS**: Simply say "✅ APPROVED: High-quality, standard-compliant curriculum."
- If **FAIL**: List exactly which keywords or sections are missing and write the _specific text_ I need to add to fix it.
```
