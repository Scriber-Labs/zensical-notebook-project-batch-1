# Take Home Messages

1. Replicating your results with a separate training loops helps reveal any bugs that are masked by expected results. 
2. Don't carelessly introduce normalization steps without keeping track. If you make the decision to double normalize, have a justification and make note of it. 

    !!! note Project 2 Normalization Steps
        1. Normalized the ground truth wavefunction ( $\psi_n$ ) ...
        2. Normalized the learned wavefunction ($\psi_n^\theta$) ...

   