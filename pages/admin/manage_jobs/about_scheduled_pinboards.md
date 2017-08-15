---
title: [About scheduled pinboards]
tags: [formatting]
keywords: tbd
last_updated: tbd
summary: "blerg"
sidebar: mydoc_sidebar
---
You can get pinboards emailed to you on a regular basis and do analysis offline. This introduces an additional format for you to consume and share pinboards with others, including those who don’t have a ThoughtSpot account.

Scheduled pinboards should help with preparing for recurrent meetings, when reviewing the same pinboard is necessary. They should also be useful when you have metrics you want to monitor at a consistent interval, like daily or monthly sales targets.

Contact ThoughtSpot Support if scheduled pinboards is not enabled on your cluster, or you can run the command `tscli scheduled-pinboards` to enable it yourself.

## Scheduled pinboard creators

Administrators and users with can schedule pinboard privilege can schedule and manage pinboard jobs. These scheduled pinboard creators must have at least edit-only and view-only rights to the pinboard they want to share.

CAUTION:

It is recommended that admins carefully choose who to give can schedule pinboard privilege to, since there is a possible security hole where a user with limited access can get a pinboard email with all access data.

## Row level security

The scheduled pinboards respect row level security rules. This means if the recipients are users in ThoughtSpot, then they can only see data based on their own access to the pinboard. If the user does not have at least view-only access to the pinboard, then they will not see anything in the email. However, if the recipients are from outside of the cluster, then they will have access to the dataset of the pinboard based on the sender’s permissions.

## Scheduled pinboard formats

The pinboard visualizations are attached to the scheduled email as CSV or PDF files. Saved configurations such as pinboard filters are applied to the attachments. Refer to the table to see how the pinboard data is represented in each file format.

|CSV|PDF|
|---|---|
|The CSV file gets data only for table visualizations.|The PDF file gets data for all visualizations.|
|The email has n CSV attachments, where there are n table visualizations in the pinboard.|The email has only one attachment file, which includes every visualization on its own page.|
|Table visualizations have all data rows that they're supposed to have.|Table visualizations include only the first 100 rows.|
|In the case of a corrupted pinboard: no email is sent. An error message indicating failure to export data is visible on the Admin Jobs Management page.|In the case of a corrupted pinboard: the PDF attachment has empty/error screenshots.|
|In the case of a corrupted visualization: an email with the visualizations whose data can be exported is sent. An error message indicating visualization export error is visible on the Jobs Management page.|In the case of a corrupted visualization: the PDF attachment has empty/error slots for the corrupted visualizations.|

The size of each email is limited to 25 MB, which matches most email services size limitations.

And the total number of recipients for a scheduled pinboard job cannot exceed the default of 1000.

-   **[Schedule a pinboard job](../../admin/manage_jobs/schedule_a_pinboard_job.html)**  
You can schedule a pinboard job for any pinboard by using the Add a schedule prompt page.
-   **[Scheduled pinboards management](../../admin/manage_jobs/scheduled_pinboards_management.html)**  
You can manage all scheduled pinboards on the Jobs Management page under Admin.

**Parent topic:** [Manage jobs](../../admin/manage_jobs/manage_jobs.html)