# Elicitation Techniques

Use these when the stakeholder says "go deeper on X", when answers stay vague after one follow-up, or when an area feels thin.

## Five whys
When the stakeholder proposes a solution ("we need a dashboard"), ask why until you reach the underlying problem ("…so managers can spot late orders before the customer calls"). Write the requirement against the problem, and keep the proposed solution as one option.

## Narrate a real session
"Think of the last time someone hit this problem. Walk me through exactly what they did, step by step." Real stories surface workarounds, hidden steps, and edge cases that abstract questions miss. Workarounds are unmet requirements.

## Day-in-the-life
"What does a typical day look like for <persona>? Where does this task fit, and what comes right before and after it?" This reveals frequency, context switches, and integration points.

## Pre-mortem
"It's a year from now and this project failed. What went wrong?" Each answer is a risk, a missing requirement, or a success metric.

## Inversion / anti-goals
"What would make this product *worse* than what people do today?" This surfaces counter-metrics and non-goals.

## Quantify the adjective
Any of "fast, simple, secure, scalable, intuitive, robust, real-time" becomes a number or an observable behavior. Offer two concrete anchors ("under 1 second or under 5 seconds?") so the stakeholder can pick instead of inventing a number.

## Forced ranking
When everything is "important", ask: "If you could ship only three of these, which three?" Then: "If the deadline moved up a month, what drops first?"

## Extremes and edges
"What happens with zero items? With 10,000? With a user who has no permissions? Two people editing at once? A network drop halfway through?"

## Example mapping
For a rule, ask for one concrete example that passes, one that fails, and one the stakeholder is unsure about. The unsure ones become open questions.

## Stakeholder map
"Who else cares how this turns out? Who could block it? Who has to live with it after launch?" Each person may contribute requirements, approvals, or risks.

## Anti-patterns to avoid
- Leading questions ("You'd want SSO, right?") when the question is divergent.
- Hypotheticals ("Would you use…?") instead of actual behavior ("When did you last…?").
- Recording solutions as requirements.
- Asking the stakeholder for facts you could look up.
- Quizzing the stakeholder through a long chain of multiple-choice questions about things they don't care about. Make a sensible assumption, tag it, and move on.
