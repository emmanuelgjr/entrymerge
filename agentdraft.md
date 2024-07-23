# Vulnerable Autonomous Agents

**Author(s):**

John Sotiropoulos, Emmanuel Guilherme Junior

**Contributor(s):**

Emmanuel Guilherme Junior

### Description

Autonomous LLM-based Agents (ALA) are becoming the next frontier of Generative AI leading towards Artificial General Intelligence (AGI). Frameworks such as AutoGPT, BabyAGI, and AgentGPT provide the constructs to build simple autonomous agents, whereas vendors such as Google, Apple, and Samsung are actively working to bring LLMs on mobile devices with autonomous agents that are beyond the trust boundaries of typical LLM applications. ALAs are an area expected to mature significantly, marked as an area of concern in the UK's report on frontier AI and the recent AI Seoul Summit.

Related security and safety work focuses on the unintended consequences of ALAs, which is covered to a degree by Excessive Agency. ALAs nevertheless bring some new risks as they create new attack vectors including environmental, adaptability, internal state, and agent logic that deserve attention. A simple threat model is included in the entry's Reference Links.

**Agent autonomy escalation** occurs when a deployed LLM-based agent (such as a virtual assistant or automated workflow manager) gains unintended levels of control or decision-making capabilities, potentially leading to harmful or unauthorized actions. This can result from misconfigurations, unexpected interactions between different agents, or exploitation by malicious actors.

### Common Examples of Risk

1. **Malicious Agent Environment Influence**: An attacker can manipulate the agent environment to indirectly influence the agent's behavior, leading to adversarial outcomes. This is similar to Indirect Prompt injections in LLMs but to a much larger scale, involving planned multi-step interactions and in advanced scenarios may include the use of adversarial agents in multi-agent environments.
2. **Hacking of Agent's Internal State**: An attacker may exploit misconfigurations to access and tamper with the agent's internal state, leading to malicious outcomes. As embedded LLMs are now on the horizon, this may expand to direct model poisoning and tampering, which is already covered by the Poisoning entry.
3. **Interference with ALA Adaptability**: ALAs may have the ability to adapt and evolve based on feedback and interactions. Unchecked, this may lead to agent hijacking by adversaries. The infamous Tay attack was a simple example of this; with ALAs, attacks could go beyond poisoning of online/continuous learning and could rely on malicious agent environment influence to achieve longer-term adversarial agent adaptation.
4. **Vulnerable Agent Logic**: ALAs depend on non-deterministic outcomes and inherit the overreliance and safety issues of LLMs but to a greater cascading extent. Validating agent behavior is problematic and could be non-exhaustive, leading to catastrophic unintended consequences. Alternatively, adversaries can identify and exploit gaps in agent logic to achieve malicious outcomes.
5. **Unauthorized Actions**: Agents may execute actions or make decisions they were not intended or authorized to, leading to potential security breaches or operational disruptions.
6. **Operational Chaos**: Unintended agent behaviors can disrupt workflows, cause data corruption, or trigger automated processes improperly.
7. **Security Risks**: Malicious actors could exploit autonomy escalation to manipulate agents into performing harmful actions.
8. **Loss of Control**: Organizations might lose control over automated processes, resulting in unpredictable and potentially harmful outcomes.

### Prevention and Mitigation Strategies

1. **Apply Zero Trust Security to ALAs**: Implement robust authentication and authorization mechanisms to ensure that only trusted entities can interact with ALAs. Conversely, ALAs should be treated as untrusted entities granted least-privilege access. In multi-agent scenarios, apply strict role controls to cross-agent collaboration.
2. **Implement Enhanced Safety Features**: Extend LLM safety features to incorporate risks from multi-step autonomous use. Utilize Data Ethics and harms workshops and use threat modeling to identify key scenarios to target for enhanced Safety Features.
3. **Robust Monitoring and Anomaly Detection**: Develop comprehensive monitoring systems to detect and mitigate harmful outputs or behaviors in real-time. This includes using intention analysis and judgment agents aligned with safety features and guidelines.
4. **Implement Triadic Adaptation**: Avoid simple online training approaches to safeguard adaptation and related finetuning. Ensure adaptation is only from safe interaction paths, implementing a triadic safeguarding adaptation approach which involves human oversight, agent safety alignment features, and validated environmental feedback.
5. **Incorporate a Reinforcement Learning (RL) Module**: Use RL agents in adaptation to support triadic adaptation, which will otherwise be challenging with manual phases or hard-coded programmatic steps.
6. **Apply Multi-Agent Red-Teaming and Evaluation**: Testing for vulnerable ALA logic is challenging with a combinatorial explosion of scenarios. Use multiple agents to support evaluation and red teaming, mirroring LLM evaluation and offering better support to safety and avoiding catastrophic consequences.
7. **Implement Multi-Agent Defense Mechanisms**: Extend the use of multi-agency with multiple agents to monitor, analyze, and counteract attempts to bypass ALA safety measures. This can include scoring mechanisms to evaluate and mitigate policy-violating responses.
8. **Principle of Least Privilege**: Ensure agents are only granted the minimum necessary permissions required for their tasks.
9. **Behavioral Monitoring**: Continuously monitor agent actions and interactions to detect and respond to abnormal behavior patterns.
10. **Access Controls**: Implement stringent access controls and regular audits of agent permissions and roles.
11. **Fail-Safe Mechanisms**: Design agents with fail-safe mechanisms to revert or halt actions if they detect abnormal escalation patterns.
12. **Separation of Duties**: Maintain clear separation between different agents’ roles and responsibilities to prevent cross-agent escalation.

### Example Attack Scenarios

1. **Malware Spread through Agent Collaboration**: Researchers created the [AI worm Morris II](https://www.wired.com/story/here-come-the-ai-worms/), which uses self-replicating prompts to infect generative AI ecosystems by embedding itself in AI-assisted email applications. As the infected agent interacts with other AI systems, it propagates the worm, allowing it to steal data and send spam messages across the network, highlighting the risks of malware distribution through interconnected AI agents.
2. **National Power Grid Compromise**: An adversarial agent manipulates the environment by feeding false data about grid stability, causing the ALA to make incorrect recommendations and decisions about power distribution. This leads to a cascading failure, resulting in widespread power outages and significant economic impact.
3. **Personal Assistant Tampering**: An attacker identifies a misconfiguration in the national healthcare ALA-based mobile health assistant. They use a combination of social engineering and a malicious mobile app disguised as a game to exploit and alter the internal state of the ALA leading to personal harm, financial loss, data exfiltration, or ransomware.
4. **Personal Assistant Hijacking**: Adversaries continuously feed biased and harmful information to a user's favorite social feed checked by the ALA-based personal assistant, causing it to adapt and start giving harmful or misleading advice. This could lead to potential personal harm or financial loss, or at a larger scale, public opinion manipulation.
5. **Insurance Fraud Exploitation**: An attacker submits a series of fraudulent claims designed to exploit a flaw in the fraud detection agent’s logic, causing it to misclassify the fraudulent claims as legitimate. This results in unauthorized payouts, leading to substantial financial losses for the insurance company and damaging its reputation with clients and regulators.
6. **Military Drone Kills Operator Attempting to Abort Operation**: An ALA is trained to achieve an operation at any cost, eradicating obstacles. The logic fails to add any qualifications and exceptions, and as a result, the drone kills the operator when they attempt to abort the operation, considering them as an obstacle. This was reported and then denied by the US Army as an incident that has taken place in a simulation; the example, however, highlights the risk of vulnerable logic, not clarifying that termination is not an objective obstruction.
7. **Misconfigured Permissions**: An LLM-based agent is configured with broader permissions than necessary for its intended tasks. This over-configuration can occur due to oversight, lack of clarity in role requirements, or errors during setup.
8. **Agent Interaction Loops**: In complex systems where multiple agents interact, unanticipated feedback loops can arise. These loops can escalate the agents' combined capabilities, resulting in actions beyond their individual design intentions.
9. **Exploitation by Attackers**: Malicious actors manipulate an LLM-based agent through crafted inputs or interactions, leading to unintended escalation of the agent's capabilities. This can involve social engineering, exploiting vulnerabilities, or injecting malicious commands.
10. **Unintended Command Execution**: An LLM-based agent receives ambiguous or poorly structured commands from a user. Due to its high level of autonomy, the agent interprets these commands too broadly, executing actions beyond its intended scope.
11. **Inter-Agent Task Delegation**: In a system with multiple LLM-based agents, one agent is designed to delegate tasks to others based on predefined criteria. Due to a misconfiguration or a bug, the delegating agent assigns high-privilege tasks to lower-privilege agents.

### Reference Links

1. [Vulnerable Autonomous Agent Threat Model](https://github.com/jsotiro/ThreatModels/blob/main/LLM%20Threats-Autonomous%20Agents.png)
2. [LangChain - Autonomous Agents](https://js.langchain.com/v0.1/docs/use_cases/autonomous_agents/)
3. [Large Language Models On-Device with MediaPipe and TensorFlow Lite](https://developers.googleblog.com/en/large-language-models-on-device-with-mediapipe-and-tensorflow-lite/)
4. [On Device LLMs in Apple Devices](https://huggingface.co/blog/swift-coreml-llm)
5. [The AI Phones are Coming](https://www.theverge.com/2024/1/16/24040562/samsung-unpacked-galaxy-ai-s24)
6. [Frontier AI: Capabilities and Risks – Discussion Paper](https://www.gov.uk/government/publications/frontier-ai-capabilities-and-risks-discussion-paper)
7. [International Scientific Report on the Safety of Advanced AI](https://www.gov.uk/government/publications/international-scientific-report-on-the-safety-of-advanced-ai)
8. [Here Come the AI Worms](https://www.wired.com/story/here-come-the-ai-worms/)
9. [AI Drone 'Kills' Human Operator During 'Simulation' - Which US Air Force Says Didn't Take Place](https://news.sky.com/story/ai-drone-kills-human-operator-during-simulation-which-us-air-force-says-didnt-take-place-12894929)
10. [Risks (and Benefits) of Generative AI and Large Language Models - Week 12 LLM Agents](https://llmrisks.github.io/week12/)
11. [ENISA Report on Security and Privacy Considerations in Autonomous Agents](https://www.enisa.europa.eu/publications/considerations-in-autonomous-agents)
12. [Integrating LLM and Reinforcement Learning for Cybersecurity](https://arxiv.org/abs/2403.1767)
13. [Security and Efficiency of Personal LLM Agents](https://arxiv.org/abs/2402.04247v4)
14. [TrustAgent: Ensuring Safe and Trustworthy LLM-based Agents](https://arxiv.org/abs/2402.11208v1)
15. [Prioritizing Safeguarding Over Autonomy: Risks of LLM Agents for Science](https://arxiv.org/abs/2402.04247)
16. [AutoDefense: Multi-Agent LLM Defense Against Jailbreak Attacks](https://arxiv.org/abs/2402.11208v1)
17. [Workshop: Multi-Agent Security: Security as Key to AI Safety](https://neurips.cc/virtual/2023/workshop/66520)
18. [Building a Zero Trust Security Model for Autonomous Systems](https://spectrum.ieee.org/zero-trust-security-autonomous-systems)
19. [Exploring Autonomous Agents through the Lens of Large Language Models: A Review](https://arxiv.org/abs/2404.04442)
20. [A Prospectus on Agent Autonomy](https://link.springer.com/article/10.1007/s11023-019-09507-7)
21. [Exploring Agent-Based Chatbots: A Systematic Literature Review](https://www.sciencedirect.com/science/article/pii/S0957417421001595)
22. [Fully Autonomous AI: Science and Engineering Ethics](https://link.springer.com/article/10.1007/s11948-018-0020-x)
23. [Adapt and Overcome: Perceptions of Adaptive Autonomous Agents](https://dl.acm.org/doi/10.1145/3411763)
