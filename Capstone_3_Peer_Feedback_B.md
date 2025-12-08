# Second Peer Feedback for Austin — Broader Lens Review

## Strengths of the Current Implementation
The way you set up the comparison between a fine-tuned BART-large-CNN model and the Gemini API feels very natural and practical, almost like something a product team would actually do when weighing long-term options. I’m working on a similar problem, so seeing you lay the two approaches side by side helped me think more clearly about my own setup as well.

The notebook itself is incredibly clean. The modular organization makes it easy to follow the flow of the pipeline from start to finish. And running BART-large on consumer hardware is no small thing. I’d still love to know what your training times and hardware looked like, mostly because I’m curious how feasible it would be for me to try the same. That kind of detail also tends to be helpful later when things need to be reproduced.

## Engagement With Your Proposed Improvements
You raised the question of how to evaluate summaries when ROUGE doesn’t match human preference. I’ve been wrestling with the same issue, and I don’t have any special expertise here, so I asked an LLM to help me understand the landscape a bit. It surfaced a few metrics—BERTScore, METEOR, MoverScore, LLM-as-Judge, QAFactEval—that seem to capture more meaning and coherence than ROUGE alone. I’m not in a position to say which ones are “best,” but I’m planning to explore them too. Your instinct to broaden the evaluation makes sense, especially since both of us noticed the same mismatch between ROUGE scores and human impressions.

You also mentioned improving documentation. I agree this would strengthen the project. Even lightweight logs—training duration, GPU/CPU details, and per-epoch changes—can make a big difference when revisiting or scaling a model. I’m trying to get better at this myself.

## Suggested Alternative or Complementary Improvement Paths

Below are thoughts I'm toying with that would apply, really, to either of our capstones:

### 1. A/B User Evaluation Pipeline
**Summary:** Build a small interface that shows users two summaries (local model vs. Gemini) and records which one they prefer.  
**Why it might help:** Human preference often tells a different story than ROUGE, and having that data could guide future iteration.  
**How to implement:** A simple web form or notebook widget that logs user selections.  
**Industry parallel:** Many summarization systems now rely on preference modeling to guide improvements.

### 2. Domain-Specific Mini-Dataset
**Summary:** Put together a small set of real conversations from the target environment (anonymized).  
**Why it might help:** Fine-tuning even a small model on domain-specific data can dramatically improve relevance.  
**How to implement:** Collect 50–200 sample chats, write short reference summaries, and evaluate both pipelines on them.  
**Industry parallel:** Teams often find that “small but tailored” prompts or datasets outperform generic ones.

### 3. LLM-as-Grader
**Summary:** Use a strong model to score summaries directly.  
**Why it might help:** This can capture coherence, usefulness, and reading quality in a way ROUGE cannot.  
**How to implement:** Provide the dialogue and summary to an LLM and ask for a rating or short justification.  
**Industry parallel:** LLM evaluators are increasingly common for summarization and code review tasks.

### 4. Cost–Latency Modeling
**Summary:** Compare the long-term cost and runtime of local inference vs. API inference.  
**Why it might help:** Businesses often choose models based on efficiency as much as accuracy.  
**How to implement:** Measure tokens, runtime, and estimated dollars per 1K inferences for both paths.  
**Industry parallel:** Optimization and cost modeling are becoming core parts of ML deployment strategy.

### 5. Hybrid Fallback System
**Summary:** Use the local model as the default and the API as a reliable fallback, or vice versa.  
**Why it might help:** Ensures consistent performance even when one of the models fails or times out.  
**How to implement:** Wrap the summarization call in a simple “try local → fallback to API” structure.  
**Industry parallel:** Redundant pipelines are common in production systems.

### 6. Smaller Efficient Models
**Summary:** Try lighter models like DistilBART or Flan-T5-Small.  
**Why it might help:** They may offer similar quality with better speed and cost.  
**How to implement:** Fine-tune the smaller model on the same dataset and compare with your current baselines.  
**Industry parallel:** There’s a growing trend toward compact models that perform well in constrained environments.

## Closing Thought
Your project is already strong and thoughtfully put together. These ideas aren’t recommendations from a position of authority—just possibilities that occurred to me while working through the same challenges. Your work is helping me think about clearer evaluation, better documentation, and more realistic deployment scenarios, and I hope some of these broader ideas offer useful directions for you as well.