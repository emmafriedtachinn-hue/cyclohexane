# DWSIM Simulation Files

Store the working and released DWSIM flowsheet files in this directory.

## Versioning approach

Do not save a new file for every tiny edit.

Create milestone files/releases when the process meaningfully changes, for example:

~~~text
v0.1-feed-and-thermo
v0.2-feed-conditioning
v0.3-reactor-base
v0.4-staged-reactor
v0.5-effluent-separation
v0.6-recycle-open-loop
v0.7-shortcut-distillation
v0.8-rigorous-column
v0.9-closed-loop
v1.0-validated-base-case
~~~

The Git history and the model construction log should explain each milestone.

## Current status

No simulation binary/XML file has been committed here yet.

The current DWSIM model should be added when the next stable milestone is ready, rather than uploading an undocumented intermediate file.
