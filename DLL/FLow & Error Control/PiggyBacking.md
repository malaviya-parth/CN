# Piggybacking

- In order to improve efficieny, ACK is not sent in seperate frame rather data frame is used to send ACK.
- THe technique of temporary delaying the outgoing ACK. So that it can be hooked on to the next outgoing data frame is called as Piggybacking.
- It is not always possible to use piggybacking.

## Question
- Efficiency of Stop&Wait if piggybacking is used?

### Solution
- Here if piggbacking is used then Useful cycle time is 2 T.T. and total cycle time is 2 T.P. + 2 T.T.
- $\eta$ = $\frac{2 T.T.}{2 T.P. + 2 T.T.}$ = $\frac{T.T.}{T.P. + T.T.}$ = $\frac{1}{1 + \alpha}$, where $\alpha$ = $\frac{T.P.}{T.T.}$