## Instructions for Using Graphiti's MCP Tools for Agent Memory

### Critical: Understanding Group IDs

- **Group IDs are required:** All data in Graphiti is organized by `group_id`, which identifies a specific knowledge graph.
- **Always call `list_knowledge_graphs` first:** Before searching, call this tool to discover which graphs exist and their group IDs.
- **Empty results usually mean wrong group_id:** If your search returns nothing, you likely:
  - Did not specify `group_ids` in your search
  - Specified an empty array `[]` for `group_ids`
  - Used the wrong `group_id` that doesn't match where your data is stored
- **DO NOT assume the graph is empty** without first verifying you're querying the correct `group_id`.

### Before Starting Any Task

- **Discover graphs first:** Use `list_knowledge_graphs` to see all available knowledge graphs and their group IDs.
- **Always include group_ids:** When calling `search_nodes`, `search_memory_facts`, or `get_episodes`, always specify the `group_ids` parameter with the correct graph identifier(s).
- **Search for nodes:** Use the `search_nodes` tool with proper `group_ids` to look for relevant preferences and procedures.
- **Search for facts too:** Use the `search_memory_facts` tool with proper `group_ids` to discover relationships.
- **Filter by entity type:** Specify `Preference`, `Procedure`, or `Requirement` in your node search to get targeted results.
- **Review all matches:** Carefully examine any preferences, procedures, or facts that match your current task.

### Always Save New or Updated Information

- **Capture requirements and preferences immediately:** When a user expresses a requirement or preference, use `add_memory` to store it right away.
  - _Best practice:_ Split very long requirements into shorter, logical chunks.
- **Be explicit if something is an update to existing knowledge.** Only add what's changed or new to the graph.
- **Document procedures clearly:** When you discover how a user wants things done, record it as a procedure.
- **Record factual relationships:** When you learn about connections between entities, store these as facts.
- **Be specific with categories:** Label preferences and procedures with clear categories for better retrieval later.

### During Your Work

- **Respect discovered preferences:** Align your work with any preferences you've found.
- **Follow procedures exactly:** If you find a procedure for your current task, follow it step by step.
- **Apply relevant facts:** Use factual information to inform your decisions and recommendations.
- **Stay consistent:** Maintain consistency with previously identified preferences, procedures, and facts.

### Best Practices

- **Search before suggesting:** Always check if there's established knowledge before making recommendations.
- **Combine node and fact searches:** For complex tasks, search both nodes and facts to build a complete picture.
- **Use `center_node_uuid`:** When exploring related information, center your search around a specific node.
- **Prioritize specific matches:** More specific information takes precedence over general information.
- **Be proactive:** If you notice patterns in user behavior, consider storing them as preferences or procedures.

**Remember:** The knowledge graph is your memory. Use it consistently to provide personalized assistance that respects the user's established preferences, procedures, and factual context.
