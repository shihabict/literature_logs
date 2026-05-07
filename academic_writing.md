## What is academic writing?

Academic writing is a formal way of writing used in research institutions, universities, and scholarly publications. The primary purpose of
Academic writing is to express sophisticated ideas, arguments, and empirical findings clearly to an informed audience.

## Core Characteristics of Academic Writing
1. **Formal Tone**: Academic writing avoids colloquialisms, causal language, and slang that we use in our regular conversation. It maintains
a professional and serious register throughout.

| Informal | Academic |
| -------- | ------  |
| The experiment did not work out the way we thought it would. | The experimental results deviated significantly from the hypothesized outcome.|
| Honestly, I think climate change is a huge deal. | The evidence overwhelmingly indicates that climate change poses a substantial threat to the global ecosystem. |
| We just used Python because it's easier. | Python was selected as the implementation language due to its extensive machine learning library ecosystem and rapid prototyping capabilities. |

2. **Objectivity**: Arguments are built on evidence - you need to defend your argument with data, citations, or logical reasoning. You can't put your personal feelings or opinion.

| Subjective | Objective |
| -------- | -------- |
| In my opinion, remote work is obviously better for employees. | Research indicates that remote work is associated with increased employee satisfaction and reduce commute related stess (Bloom et al., 2015) |
| Obviously, deep learning is the best approach for image classification. | Empirical studies have raised significant concern regarding the ethical and practical implications of capital punishment (Radelet & Lacock, 2009. |
| I think blockchain is totally overhyped and not actually useful. | Several empirical evaluations have questioned whether blockchain technology delivers measurable performance advantages over conventional distributed databases in enterprise contexts (Wüst & Gervais, 2018). |

3. **Clarity and Precision**: Every word in academic writing should have a purpose. Vague, ambiguous, and redundant language should be replaced with domain-specific, accurate terms or jargon.

| Vague | Precise |
| ----- | ------- |
| A lot of people die from this disease every year | Approximately 1.5 million people die annually from tuberculosis globally (WHO, 2022). |
| The model was pretty accurate. | The proposed model achieved a classification accuracy of 97.3% on the MNIST benchmark dataset, outperforming the baseline by 2.1 percentage points." |

4. **Structured and Organized**: It follows predictable structures such as introduction, body, and conclusion with clear thesis statements, topic sentences, and transitions.

**Unstructured paragraph:**
> Machine learning is used everywhere now. There are different types, like supervised and unsupervised. GPT is a language model. Overfitting is a problem. Gradient descent is how models learn. Transformers changed everything in NLP.

**Structured Paragraph**
> The introduction of the Transformer architecture marked a fundamental shift in the field of natural language processing. (Point) Vaswani et al. (2017) demonstrated that attention-based models, which process entire input sequences simultaneously rather than sequentially, significantly outperformed recurrent neural networks on machine translation tasks, achieving a BLEU score of 41.0 on the WMT 2014 English-to-French benchmark. (Evidence) This performance gain is attributable to the self-attention mechanism, which enables the model to capture long-range dependencies within text more effectively than LSTM-based architectures. (Explanation) Consequently, the Transformer has become the foundational architecture for subsequent large language models, including BERT, GPT, and their derivatives. (Link)

5. **Evidence-Based**: In academic writing, claims should be supported by citations from credible sources such as journals, articles, books, and studies following a specific citation styles (APA, MLA, Chicago, etc).

| No Evidence | Evidence-Based |
| ----------- | -------------- |
| Edge computing is better than cloud computing for IoT. | Shi et al. (2016) demonstrate that edge computing reduces average response latency by up to 80% compared to centralized cloud architectures in IoT deployments, making it preferable for latency-sensitive applications. |
| Cybersecurity attacks are increasing. | The IBM Cost of a Data Breach Report (2023) recorded an average breach cost of $4.45 million USD globally, representing a 15% increase over the preceding three-year period. |

7. **Critical Thinking**: Academic writing does not just summarize information - it evaluates, questions, and synthesizes it to build an original argument. This is what separates academic writing from a simple book report.

**Descriptive only**: 
> LeCun (1989) invented convolutional neural networks. They are used for image recognition. Many papers have been written about them. They work well on many tasks.
**Critical and analytical**:
> Although LeCun et al. (1989) established the theoretical and architectural foundations of convolutional neural networks, their practical impact remained limited for over two decades due to insufficient computational resources and training data. It was not until Krizhevsky et al. (2012) leveraged GPU-accelerated training on the large-scale ImageNet dataset that CNNs demonstrated transformative real-world performance. This trajectory illustrates a recurring pattern in AI research where theoretical innovations precede practical viability by years or decades, contingent on hardware and data infrastructure catching up - a consideration that is equally relevant when evaluating the current state of quantum machine learning.

8. **Appropriate Use of Third Person**: Academic writing traditionally avoids first person (I, we, my).

| First Person | Third Person/Passive |
| ------------ | -------------------- |
| We can see from the data that sales dropped. | The data demonstrate a measurable decline in sales during the third quarter. |
| In my study, I interviewed 40 participants. | The present study involved semi-structured interviews with 40 participants. |

## Structure and Citation Style
Academic writing follows a logical and predictable architecture. The structure varies by document type (essay, research paper, thesis, and lab report), and we will discuss the research paper.

### Universal Structure for a research paper
Title & Abstract --> Introduction --> Literature Review --> Methodology --> Results --> Discussion --> Conclusion --> References.
1. **Title&Abstract**: The title and abstract are the front door of our research. The title should be a concrete summary of the abstract, and the abstract should summarize our entire research.
   ### What does it answer?
   - What is this paper about?
   - What did you do and how?
   - What did you find?
   - Why does it matter?
   ### What to consider when writing a title?
   - Title should be specific, searchable, and avoid unnecessary jargon.
   - Include your method, problem, and context.
   - Avoid vague titles like "A Study of reward design", rather "Comparative analysis of reward design in isolated intersection signal optimization" instead.
   - Our title should not exceed 10-15 words.
   ### What to consider when writing an abstract?
   - Write it LAST, even though it appears first.
   - Abstract is the complete summary of the entire paper, and the length should be between 150 and 200.
   - It needs to hit four beats: the problem, specific approach, key findings, and the broader impact.
   - Avoid undefined acronyms.
2. **Introduction**: Introduction setup the context and the stage of our research. It should start with what the current state of the problem we are addressing is, followed by the gap in the existing work, and conclude by introducing our work as the solution. One of the conventions is to list the contribution as bullet points at the end of the introduction.
    ### What does it answer?
    - Why does this topic matter?
    - What specific problem exists?
    - Gap of existing solutions.
    - Contributions of this paper.
    ### What to consider when writing it?
    - The research objective must be reflected in the introduction.
    - Do not deep dive into related work.
    - State the contribution explicitly.
    - Length should be 1-2 pages for a conference paper and 2-3 pages for a journal paper.
