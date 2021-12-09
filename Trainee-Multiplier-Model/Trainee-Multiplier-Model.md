<!-- @format -->

# Trainee Multiplier Model

This model is multiplying itself and find best model at each iteration and giving its properties to other models for next iteration.

### Algo:

-   Create N difference instance of Trainee model which provides actions given a state
-   Take the first model and generate (state, **_Pseudo gradient_**) pairs to fill up **_Buffer_**.

*   Train the N models to train with the buffer.
*   A **_Race_** will start after that. We will take avarage of of the races for N models. Pick at most 2 of them and forward them to next iteration.
*   The remaining models will get the weights of the best model.
*   In next iteration, the best model will fill up the buffer.

### Note:

_Pseudo gradient_ are weighted discounted return difference of in transition to next state.
_Buffer_ is the replays to best model at each iterations.
_Race_ is to play each model for couple of time to check which model is best given a iteration.

### Drawback:

-   The model stuck at a local maxima, never gets out.
