# Peer Feedback for Austin — Dialogue Summarization Capstone

## Success Highlights
Your project reads with a level of clarity and structure that makes the whole problem space feel grounded and approachable. The pitch lays out the business pain points with well-chosen metrics, and the infographic on the first page sets the stage in a way that’s easy to follow. I tend to explain things in a more winding way, so seeing how directly you framed the problem --> impact --> scope was genuinely helpful for me.

Your notebook mirrors that same discipline. The code is clean, consistently formatted, and easy to trace from data loading to evaluation. I also want to highlight your use of **BART-large-CNN** on consumer hardware. I went with BART-base for practicality, so seeing you fine-tune the larger model successfully made me curious about your setup and training duration. That information isn’t in the notebook, but having it would strengthen reproducibility for anyone revisiting the project later.

Our results ended up in similar places—BART outperforming Gemini on ROUGE, despite Gemini sometimes sounding more natural. The alignment across two separate approaches reinforces the validity of your design choices.

## Constructive Feedback
The main thing I found myself missing was the training curve or per-epoch metrics. I imagine you cleaned the notebook before pushing it to GitHub, but having even a simple record of ROUGE progression or loss curves would make the final scores easier to contextualize. It also helps with future re-runs if something changes in the environment.

On evaluation metrics: I’ve run into the same struggle with ROUGE that you described. So unfortunately, I don't have an answer here. But, conversing with ChatGPT, here's what I'll be exploring for the same issue:

- **BERTScore** — Embedding-based; often aligns better with human judgment.  
- **METEOR** — More tolerant of paraphrasing.  
- **MoverScore** — Focuses on semantic similarity rather than exact token overlap.  
- **LLM-as-Judge** — A practical way to assess coherence and usefulness.  
- **QAFactEval** — More relevant when factual consistency is a priority.

## New Perspective
Reviewing your work gave me a useful reminder about the value of a clear narrative. Your pitch flows in a straight line, and it made me think about tightening the structure of my own materials. Your willingness to fine-tune a larger model also nudged me to reconsider some of my assumptions about model size and feasibility on local hardware.

Overall, I think your project is well executed and thoughtfully communicated. The comparison between a fine-tuned local model and a modern LLM aligns closely with real industry questions, and you handled that contrast in a way that’s both technically solid and easy to interpret. Your work made me think more deliberately about evaluation, documentation, and the broader framing around this kind of system.