# AI1301_Contribution_Log-2

# Contribution [#22506]: UX issues in User's assigned Groups tab

## Problem Summary
Contribution Number: #24305 
Student: Kashvi Teli 
Issue: wso2/identity-appss#24305
Status: Phase III FINISHED

## Why I Chose This Issue

This issue interests me because:

1. I think helping design a simple UI component will not only help me gain confidence in my decision making skills but also teach me how to communicate alongside getting to work on my UI/UX technical skills. 
2. I am very interested in frontend and am capable in handling bugs from experience since most of my hackathons and college courses projects involved me working on similar issues and implementing frontend.
3. I am proficient in the languages involved in this interface, [Java, Javascript, Typescript and CSS] so I will be able to contribute efficiently.
4. I want to learn how to fix bugs in the frontend in the context of a real world project since it is a much larger scale application.
   
## Reproduction Process
### Environment Setup
Installed Maven and WSO2's Identity Server (talks to the frontend and keep it running locally) — had it running in about 1.5 hours. I ran pnpm install and build in the app directory of WSO2's Identity-Apps Repo in VSCode while also starting the WSO2 Server to access the frontend interface. 

Working branch: https://github.com/kashvii-1/identity-apps/tree/fix-issue-22506

## Steps to Reproduce
Issue 1:
1. Navigate to the localhost link for Console after starting the W2O2 Server from terminal.
2. Login using credentials 
3. Click on Activity in the dashboard bar on the left
4. Click on an Action Tile
5. Fill out the Action Tile form prompted upon clicking on the Action Tile 
6. Activate by clicking on the switch button at the top of the form then click "Go back to Actions"
7. **Expected:** The Action Tile would show the status of activation labelled "Active"
8. **Actual:** The Action Tile does not reveal any indication of status about whether it is active or not
   
### Solution Plan
**Understand:** Action Tile Plan needs an additional feature that reveals its activation status or the lack thereof

**Match:** 
The Pre Configuration Status Indication is already listed and a functioning feature in the Action Tile Container, so the status indication structure should be similar.

**Plan:**
Summary: 
1. Design an UI mockup following the style guidelines listed in the directory of ReadMe in WSO2/Identity-Apps and get it approved by the product team.
2. Upon approval of the design, I can began implementation. First I will integrate an API call or a hook within Action Tile module to retrieve the on/off button component's activity. 
3. Then I will create a conditional ifEnabled component in the Action Tile UI that shows activty status whenever toggled on/off or inactive. 

**Temporary Update for June 30th Submission** - Was unable to contribute due to not feeling well over the past week, however did look at the code where I will be adding this new feature and consult the UI design style in the main repo's ReadMe.md. 

### Phase III (COMPLETION REACHED)

### Progress For June 30th - July 8th [Continuation of July 8th-15 Below]
**What I built:**
- Implemented the `renderActionConfiguredStatus` utility function using  TypeScript.
- Added JSX mapping to support multi-status badge renders (Configured + Active/Inactive tags) nested inside a dedicated `.status-tags-container`.
- Implemented new CSS styles for visibility of the new tags inside status-tag-container [rule configuration summary box]

### Progress For July 8th - July 15th 
- Implemented test cases in "actions.test.tsx" for "configure-status-active-tag" feature (that I built as mentioned above) to check if active/inactive status renders
- Tried to solve failed test cases that are caused due to environment set up issues.

### Progress For July 15th - July 22nd
- Tried to get my unit test to run however am running into issues between Vitest (the test runner) trying to resolve React in 'modules/forms/src/legacy/forms.tsx'. Module resolution that instructs Vitest on how to handle packages is in 'modules/unit-testing/vitest.config.ts' and I cannot edit that without potentially changing configuration for other unit tests. 

**Files I touched:**
- `src/components/actions/actions.tsx`
- `src/components/actions/actions.scss`
- 'src/components/actions.test.tsx' [NEW]

**Challenges faced:**
- Issue: The browser renders failed to show the new status tags despite successful compilation cycles [no related or new bugs found that's allegedly blocking visibility, seems entirely an css nesting issue].
- Resolution: I was nesting the containers for configu_status_tag wrongly, I was meant to put the active/inactive container outside the sub component, and directly under the parent container. 

- Issue [NEW] : The test cases are failing due to a complex monorepo/workspace that's causing Vitest (testing tool) in terminal to hault compilation before it reaches test code.
- Resolution : Since the issue is occuring between a shared dependency package and Vitest due to Vitest's configuration, I may have to consult the repo maintainer to take further steps. 

**Testing Notes**
1. Tests I made so far : I've made 2 unit tests using Vitest and @testing-library/react inside a new test file: src/components/actions.test.tsx (this mocks the container layout rendered via ActionTypesListingPage). These tests specifically target the dual-tag render logic inside the .status-tags-container where the first test checks the configured and "active" status tags, and second test checks the configured and "inactive" status tag.
2. For Manual Verification, I manually verified via the browser UI that toggling the rule configurations correctly reflects both the "Configured" status badge alongside the newly styled "Active" or "Inactive" tags in the rule configuration summary box. 
3. Final Conclusion for Unit Test and Why It Failed Due to Factors Outside my Scope:
   > The test runner Vitest cannot load a shared workspace package [cannot resolve React] when compiling 'modules/forms/src/legacy/forms.tsx' despite React being installed and hoisted locally
   > The reason why the dependency package is unable to be resolved is due to how the vitest.config.ts file is configured for the entire repo's testing.
   > I cannot edit the vitest.config.ts file since lots of tests depend on it, but cannot get my local environment to run my unit test either due to problems between my test runner and dependency package. [Attempted to bug for 2 hours but no avail].
 
**Commits this week:**
- 1455b0fdc9: Implemented Logic for "Active/Not Active" status to render onto website based upon active rule configuration form submitted by users.
- 5d9235e433 — "Add unit test for actions status rendering"





