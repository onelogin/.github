# Pull Request Instructions

Title your PR in the following format:
`<Jira ticket number>: <short description>`

Example:
ADMIN-1822: update navbar height to match portal

This is important to ensure the Jira ticket is kept in sync with automated processes
that are parsing the ticket number with regular expressions

Multiple ticket numbers also work:
ADMIN-1822, PORTAL-1343: unpdate nav bar heights in admin and portal

# Rules

1. Respond to every conversation.
2. Don't resolve any conversation you didn't start.

## Respond to every conversation
Every conversation should have a response, and there are only 3 valid responses:

1. A question seeking clarity of the changes request.
2. An explanation of why the changes made are correct.
3. The SHA of the commit containing the changes requested.

The SHA of the commit?
If PR Author understands and agrees with the request, after making the changes, find the commit that contains the changes and click on the copy icon to Copy full SHA for the commit...then paste that SHA as your entire response to the conversation
 
You do not need to say "Okay" or "Done" or "Here ya go".  When PR Reviewer sees a hyperlink like that as the response, they know that it means PR Author understood & agrees with the request and has addressed it in the commit linked.  It is a big help to PR Reviewer to be able to immediately jump from the open conversation to associated changes.
 
## Don't resolve conversations you didn't start

It is easy for PR Author to misunderstand the changes PR Reviewer is requesting.  If PR Reviewer asks for X and PR Author changes Y, it would be quite frustrating for PR Reviewer to see the conversation marked as resolved when, in fact, it is not resolved.
 
The other reason to allow PR Reviewer to be the one to resolve the conversation is that many PR Reviewers are constantly context switching, across many different repos, and use these "open conversations" as breadcrumbs to keep track of what changes they asked for.  If PR Author marks these conversations as resolved, PR Author will completely lose track of where they were in the PR review process.
