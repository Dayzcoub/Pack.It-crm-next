# 25 Shortages 10.389

Decision: an active review of a proposal by the warehouse operator temporarily blocks withdrawal of that proposal by the responsible person.

Behavior:
- the block begins when the warehouse operator opens the proposal in the decision form;
- while that review form remains active, the responsible person cannot withdraw the proposal;
- if the warehouse operator closes or abandons the form without saving a final decision, the block is released and withdrawal becomes available again;
- if the final decision is successfully saved, the proposal is no longer withdrawable because it has already been processed;
- the interface must clearly explain that withdrawal is temporarily unavailable because the proposal is currently being reviewed.

Architecture binding:
- the review lock is transient application state associated with the proposal review session;
- it does not transfer ownership of the shortage and does not itself create a shortage resolution;
- opening or closing the review form without saving creates no shortage history entry, audit event, or notification;
- successful final processing remains governed by the established shortage resolution transaction.

MVP:
- one active warehouse review temporarily blocks withdrawal;
- closing the review without saving removes the block;
- successful final processing permanently ends withdrawal availability.
