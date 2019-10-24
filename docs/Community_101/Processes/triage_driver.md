---
title: GitHub Triage Driver Workflow
description: Outline of workflow for GitHub triage process.
author: miubezzi
date: 10/24/2019
---

# GitHub Triage Driver Workflow

## Overview

This document describes the responsibilities of triage driver as well as guidance on different workflows. There will be two active Triage drivers assigned for each week with equal responsibilities, one from Redmond/Atlanta and one from IDC and assinged through IcM. The schedule for the week is Mon – Sun.

## Out of Scope

This documents the process, independent of the tool used for Triaging. For example, WatchTower or Power BI etc. 

## Triage Driver Responsibilities

* Triage at least twice in a day (in the morning after coming into the office and in the evening before leaving).  

[!Note]  Be mindful of the holidays in all team locations and assign the issue accordingly to the teams available. Similarly, during the Redmond evening triage, assign issues to the India team members and not the Redmond team members and vice versa. 

* Enforce adherence to triage SLA of 24hr initial response across all service areas. 
* Review and Triage all issues in Triage list. (Triage tab in PowerBI or Triage bucket in WatchTower)  
  * On Weekdays, triage scope is limited to unassigned issues missing service label or not assigned to a service bucket/area. (Please consider reviewing the service mapping and provide feedback to the WT team as an effort to reduce the un mapped items as we progress) 
  * In WatchTower, the Triage – Unmapped Issues bucket should be emptied at the end of each day. There might be some issues that do not belong to any buckets, re-route those issue to your service area buckets and work on it from there. At the end of the ‘week’ for a given triage driver rotation, the unmapped issues bucket should be cleaned and ready for the next week’s triage driver rotation. 
* Triage the GitHub issues which have passed 15 hrs since creation time and still untriaged. This needs to be done irrespective of the fact whether the issue is mapped to a service or not. This can happen due to the following reasons: 
  * If the service area owner is OOF or does not have a backup: 
    Triage the issue and share it with the respective lead (For example, Diego for Infra). The lead might be aware of the backup or can arrange one from their team. 
  * If the service area owners are in different time zone and it results in issues staying in untriaged state for 15-18 hours but eventually gets triaged within 24 hrs: At 15 hrs, share the state with the respective lead as a first checkpoint warning (update Eng Lead). Triage at 18 hrs and share the status again with the respective team lead. 
* Update the state of the GitHub issues as described below: 
  * Add In-Progress label: Add the in-progress label for issues where authors add the #in-progress comment. 
  * Close issues: Check twice a day and close GitHub issues where authors added the #please-close comment. 
* Ensure the Triage – Unmapped Issues bucket is processed and emptied every day.  
  * Some issues may linger due to lack of clarity or needing additional information but, the triage driver needs to empty this bucket each day ideally but needs to be empty before rotation ends absolutely. 
* Alert tools team if any of the triage tools are broken or showing stale data. 
  * Power BI: Email [aman.arneja@microsoft.com](mailto:aman.arneja@microsoft.com)
  * WatchTower :   
* Share feedback on the triage workflow and processes if needed.  
* Triage driver will be responsible for outages (P0/P1) detection by monitoring WAINC notifications received via Azure CXP Community - Outage Notifications DL or using the other mechanism as described in the Detect section. 
* If the triage driver see any outages he will Inform the Engineering lead/Service Area Leads about the outage by using the CXP Community - Azure Outage Teams Channel. 

## Weekend Triaging

* Each co-triage driver takes a “weekend” day to allow each driver at least one triage-free day. 
For example, Triage Driver A can take Saturday and Triage Driver B can take Sunday or vice versa. They can mutually negotiate and work accordingly. 
* On weekends, triage all untriaged issues across all service areas. 

## Triage Driving Workflows

### Ideal Scenario

* If the GitHub issue opened by the customer has all the following: 
  * Issue is tied to a Microsoft Docs entity i.e. has the Document details section. 
  * It has the Service area label (like virtual-machines-windows/svc) 
   * There will be cases where the `service` label will not map to a service area or an individual (Per the PowerBI Github_CXP Report) and as the Triage Driver, you are responsible for handling these. Example service labels: multiple, azure 
* This GitHub issue will be considered triaged, if you do the following: 
  * Add the following labels: 
   1. Triaged label 
   2. Feedback type label (e.g.product-question, doc-bug etc) 
   3. Ownership label, either cxp or assigned-to-author 
  * Add the assignee: someone from the respective service area. 
  * Add the appropriate initial response, either the answer itself or general initial response, e.g. “Thanks for the feedback! We are currently investigating and will update you shortly.” 
  
### Other Scenarios
  
  For each issue, verify if the following is true and take appropriate action as described below:  
  
  Scenario|Action Needed
  ---|---
  Issue has the doc mapped but the question/feedback is unclear/uncomprehensive.|Add `needs-more-info` label and ask original poster for more information. Assign it to yourself until you have all the required information to be able to assign it to the service area owner.
  Missing reference url to doc/content.| 1. Add `needs-more-info` label and assign to yourself. 2. Ask the customer to share the url of the doc he is referencing. 3. Once customer replies with the document url, go to the document url and click `Ctrl+Alt+G` to copy the document metadata. 4. Go back to the GitHub issue, click on three dots (...) and then ‘Edit’ on the original poster’s issue description and do Ctrl+V. 5. This will add the document details section below the issue description. 6. Add the service label based on the doc provided. 7. Add all other appropriate labels and assign to the respective service area owners as mapped in this sheet.
Missing author in GitHub (name/alias not showing up in assignee list)| In the Document details section for the GitHub issue, click on the article link (.md) for ‘Content Source’. You will see the author as well as the manager’s GitHub alias there. Check if author is member of the docs repo by searching with their alias here. If author is not a member of the repo, assign the issue to the manager. Follow up with the manager via email to get the author name/alias updated in the metadata or have them added to the repo. 
Missing service tag assignment|Refer to: [Process and labeling table](https://review.docs.microsoft.com/en-us/help/contribute/contribute-customer-feedback-azure-cxp-process?branch=master#process-and-labeling-table)
Is Kudos on process or content|Refer to: [Process and labeling table](https://review.docs.microsoft.com/en-us/help/contribute/contribute-customer-feedback-azure-cxp-process?branch=master#process-and-labeling-table)
Issue violates Microsoft’s code of conduct|Refer to: [Process and labeling table](https://review.docs.microsoft.com/en-us/help/contribute/contribute-customer-feedback-azure-cxp-process?branch=master#process-and-labeling-table)
Is Product feedback|Ask the customer to share the feedback on feedback.azure.com (UserVoice) and keep track of the feedback and share in MBRs, if an impactful feature request.
Is Product Issue|If you can reproduce the issue, check MSSolve if the case already exists for the issue. If not, share the issue details with the Product team SMEs for your area in an email. Open IcM or Azure Devops issue, as needed.
Closed by the customer prior to triage|Update the issue with the appropriate labels: Triaged, [root cause label e.g.`doc-enhancement`, `product-issue`], [add owning team label = e.g. `cxp` or `assigned-to-author`], `resolved-by-customer` label, etc. as needed.
How to question|For how-to scenarios very specific to the customer, redirect to the forums (MSDN, Stack overflow) and help the customer on the forum.

## Process Flow-chart

Working on images for repo.

## References

* [GitHub process for CXP Community team](https://review.docs.microsoft.com/en-us/help/contribute/contribute-customer-feedback-azure-cxp-process?branch=master): More info on various labels, looking for authors in Azure-docs repo etc. 
* Github Saved Messages [(Web view)](https://microsoft.sharepoint.com/teams/AzCXP/Community/Internal/_layouts/OneNote.aspx?id=%2Fteams%2FAzCXP%2FCommunity%2FInternal%2FShared%20Documents%2FTeam%20Notebook%2FAzure%20CXP%20Community%20Team%20Notebook&wd=target%28Processes%2FDocumentation%20Comments.one%7C4C06C49E-CABC-4D99-8668-78C1EFF6111D%2FGithub%20Saved%20Messages%7C9F48B0F6-01DD-4F2E-8253-D728C33D9466%2F%29): Ideas on creating your own GitHub replies for typical scenarios like closing the issue, assigning to author, initial response etc. 
* [WatchTower GitHub Triaging Workflow](https://teams.microsoft.com/_#/docx/viewer/teams/https:~2F~2Fmicrosoft.sharepoint.com~2Fteams~2FWatchtowerV-Team~2FShared%20Documents~2FGeneral~2FGitHub%20Triaging%20Workflows.docx?threadId=19:ed793a56d0e34a94a6f8fe09e434acc6@thread.skype&baseUrl=https:~2F~2Fmicrosoft.sharepoint.com~2) 
* Services and service area owners mapping


  
  
