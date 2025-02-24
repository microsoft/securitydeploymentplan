# Project

> This repo has been populated by an initial template to help get you started. Please
> make sure to update the content to build a great experience for community-building.

As the maintainer of this project, please make a few updates:

- Improving this README.MD file to provide a great experience
- Updating SUPPORT.MD with content about this project's support experience
- Understanding the security reporting process in SECURITY.MD
- Remove this section from the README

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.

## Content Structure

### Recommendations Format
Each security component in `recommendations.md` follows this structure:
```markdown
### Component Name {#ComponentID}
**Why it's important:**
- Key benefit 1
- Key benefit 2
- Additional benefits...

**Implementation Steps:**
1. Major Step One
   - Sub-step detail
   - Sub-step detail
   ...
2. Major Step Two
   ...

**Learn More:**
- [Documentation Link](url)
- [Additional Resources](url)
```

### Assessment Questions
Questions are defined in `questions.json`:
```json
{
    "questions": [
        {
            "id": "ComponentID",  // Matches the ID in recommendations.md
            "text": "Question text?",
            "description": "Additional context for the question",
            "docLink": "https://learn.microsoft.com/...",
            "children": ["ChildID1", "ChildID2"]  // Optional: IDs of dependent components
        }
    ]
}
```

#### Parent-Child Relationships
- Use the `children` property to define dependencies between components
- Only define relationships on the parent question
- Child questions will be automatically hidden when parent is marked as "Yes"
- Example relationships:
  ```json
  {
      "id": "CA",  // Conditional Access
      "children": ["MFA", "CloudID"]  // CA depends on MFA and Cloud Identity
  },
  {
      "id": "XDR",  // Extended Detection and Response
      "children": ["DID", "MDO", "MDCA", "MDE", "MDVM"]  // XDR includes multiple Defender products
  }
  ```

### Features
- **Implementation Steps Toggle:** Show/hide detailed implementation steps
- **PDF Export:** Generate a formatted PDF including:
  - Current deployment status
  - Mermaid diagram visualization
  - Prioritized recommendations
  - Clickable documentation links
- **Deployment Visualization:** Interactive diagram showing:
  - Deployed components (green)
  - Pending components (pink)
  - Component relationships

### File Organization
- `index.html`: Main application and UI logic
- `questions.json`: Assessment questions and component relationships
- `recommendations.md`: Component documentation and implementation steps
- `DetailedDiagram.md`: Full deployment visualization
- `SimplifiedDiagram.md`: Condensed deployment visualization

## Making Updates

### Adding a New Component
1. Add component documentation to `recommendations.md`
2. Add assessment question to `questions.json`
3. Update parent-child relationships if needed
4. Update Mermaid diagrams in both `DetailedDiagram.md` and `SimplifiedDiagram.md`
5. Add component to appropriate deployment phase

### Updating Existing Content
1. Locate the component in `recommendations.md`
2. Update documentation while maintaining the established format
3. Update corresponding question in `questions.json`
4. Update parent-child relationships if dependencies change
5. Update diagram relationships if component dependencies change

### Best Practices
- Maintain consistent component IDs across all files
- Define relationships only on parent components
- Keep implementation steps clear and actionable
- Verify all documentation links
- Test parent-child behavior after making relationship changes
- Test PDF export after making changes
- Update both detailed and simplified diagrams
