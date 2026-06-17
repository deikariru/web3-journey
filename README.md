# Simple Counter Smart Contract

Today I learn how to make a small contract on solidify that can
- Stores a uint value
- increment() increases value by 1
- decrement() decreases value by 1
- get() returns current value
- Added ownership control

Tested in Remix VM:
- Compiled in Paris vers 0.8.19..
- Deploy successful using LONDON VM
- increment works
- decrement works
- state updates correctly
- Only deployer can modify value
- Tested in Remix with multiple accounts
- Non-owner calls correctly revert
