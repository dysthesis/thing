# Þing - a multi-agent research bot

![thing](https://upload.wikimedia.org/wikipedia/commons/thumb/2/20/Germaanse_volksvergadering_%28cropped%29.jpg/1920px-Germaanse_volksvergadering_%28cropped%29.jpg) 

## Architecture

- *Overseer* oversees the process to make sure things go as it should, and
- *messenger* is responsible for communicating with the user, such as to provide periodic updates on research progress and to ask for clarification if any part of the system encounters ambiguities or uncertainities that requires human intervention.

**Note.** Maybe let the overseer spawn a number of advisors if necessary?

### Planning

The direction of research is determined by 

- a council of "expert" agents, generating questions to direct the research and provide a wide range of perspectives, and
- a moderator, which injects unused-but-relevant directions.

### Execution

- *retriever* handles finding relevant information, and is the part that handles tool calls, and
- *reader* extracts relevant information from the contents acquired by the *reader*.

### Retrospective and criticism

In order to ensure the quality of the information being acquired, three *critic agents* are incorporated, which

- performs *source critique* in order to interrogate the reliability of the sources and provenance of information,
- evaluates the accuracy and relevance of the information itself, and
- identifies any biases in how the information is presented.

Information below a specified threshold of quality is rejected, while information that passes the aformentioned threshold is permitted, but with attached information on any of the aformentioned critiques, such that it can potentially be addressed by the other agents.

### Synthesis

Once done, spawn a dynamic number of agents in parallel (maybe similar to Grok 4 Heavy) to synthesise the final answer based on the available evidence.

Spawn an adjudicator agent, along with some $n$ sub-agents working in parallel. The pipeline therefore becomes

- synthesis of $n$ outlines by the sub-agents,
- merging of the $n$ outlines into one by the adjudicator agent,
- syntehsis of $n$ drafts based on the unified outline by the sub-agents,
- merging of the $n$ drafts into one by the adjudicator agent,
- syntehsis of $n$ suggested revision sets by the sub-agents,
- debate among the $n$ sub-agents to decide on a final set of revisions, and
- synthesis of final output by the adjudicator based on the draft and revisions.

Perhaps consider a 'council' of judges discussing and debating, where the decision is made when a threshold of consensus is reached, instead of a single adjudicator agent. Any unresolved disagreement can be resolved by the overseer anyways.

## Why the name?

I'm naming it "thing" because it's funny. It is both the term for an ancient Germanic governing assembly, as well as one of the most common English words.

## References

- [Assisting in Writing Wikipedia-like Articles From Scratch with Large Language Models](https://arxiv.org/abs/2402.14207) 
- [Into the Unknown Unknowns: Engaged Human Learning through Participation in Language Model Agent Conversations](https://www.arxiv.org/abs/2408.15232)
- [How we built our multi-agent research system](https://www.anthropic.com/engineering/multi-agent-research-system)
