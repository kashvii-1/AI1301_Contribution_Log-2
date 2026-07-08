# AI1301_Contribution_Log-2

# Contribution [#22506]: UX issues in User's assigned Groups tab

## Problem Summary
Contribution Number: #24305 
Student: Kashvi Teli 
Issue: wso2/identity-appss#24305
Status: [Phase III 50% PROGRESS REACHED]

## Why I Chose This Issue

This issue interests me because:

1. I think helping design a simple UI component will not only help me gain confidence in my decision making skills but also teach me how to communicate alongside getting to work on my UI/UX technical skills. 
2. I am very interested in frontend and am capable in handling bugs from experience since most of my hackathons and college courses projects involved me working on similar issues and implementing frontend.
3. I am proficient in the languages involved in this interface, [Java, Javascript, Typescript and CSS] so I will be able to contribute efficiently.
4. I want to learn how to fix bugs in the frontend in the context of a real world project since it is a much larger scale application.
   
## Reproduction Process
### Environment Setup
Installed Maven and WSO2's Identity Server (talks to the frontend and keep it running locally) — had it running in about 1.5 hours. I ran pnpm install and build in the app directory of WSO2's Identity-Apps Repo in VSCode while also starting the WSO2 Server to access the frontend interface. 

Working branch: https://github.com/kashvii-1/identity-apps/pull/new/fix-issue-24305

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

### Progress For June 30th - July 8th 
**What I built:**
- Implemented the `renderActionConfiguredStatus` utility function using  TypeScript.
- Added JSX mapping to support multi-status badge renders (Configured + Active/Inactive tags) nested inside a dedicated `.status-tags-container`.
- Implemented new CSS styles for visibility of the new tags inside status-tag-container [rule configuration summary box]


**Files I touched:**
- `src/components/actions/actions.tsx`
- `src/components/actions/actions.scss` 

**Challenges faced:**
- Issue: The browser renders failed to show the new status tags despite successful compilation cycles [no related or new bugs found that's allegedly blocking visibility, seems entirely an css nesting issue].
- Resolution: I am currently stuck in progress as I am unable to visibly see changes and hence test my progress. Currently am finding the solution by testing out the cache settings and css nesting issues that don't cause compilation issues but refuse to show up on the website.]

**Testing Notes**
Progress to be reached since currently am not able to visible see my changes into the interface despite 0 compilation issues! 


**Commits this week:**
- 1455b0fdc9: Implemented Logic for "Active/Not Active" status to render onto website based upon active rule configuration form submitted by users. 

**Proof of Commit: shown in the checkin form submission!**




