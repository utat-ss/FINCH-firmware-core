# Flight MCU Code PR

_Any changes in this PR should be ready to go to space. **At least two reviewer approvals are required to merge the PR.**_

## Target information

- **Link to associated Notion chapter:** [Notion link]
- **What type of modification is this?** [adding driver, bugfix, etc.]
- **Is this PR targeting all MCUs?** [answer]
    - _If yes, the base branch should be `main`_
    - **If no, what MCU is this targeting?** [ADCS, OBC/EPS, PAY]
        - _If no, the base branch should be an MCU, like `ADCS-STM32G431RBT6`_

## Summary

[Give a one sentence explanation of what this pull request adds.]

## Details

[Provide a more detailed explanation of what this pull request includes. This can include bullet points of new features, a link to the sensor being added, Notion pages with explanations, and so on. Any testing done should also be explained here.]

## Checklist

- [ ] This PR has been tested to ensure that existing MCU functionality still works.
- [ ] This PR has been tested to ensure new/modified/removed MCU functionality still works/didn't break anything.
- [ ] This PR has been tested on hardware.
- [ ] The branch has been rebased against the head of the target branch
- [ ] The code is "complete" (it can be merged without needing any other branch or external code). If not, _leave this box unchecked_ and explain in the **Details section**.
- [ ] The **Target Information** section above has been filled out.
- [ ] The **Summary** and **Details** sections have been filled out.
