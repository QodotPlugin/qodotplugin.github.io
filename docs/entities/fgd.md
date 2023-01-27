---
layout: default
title: FGD Files
nav_order: 7
---

## Adding new entity definitions

1. Increase the size of the Entity Definitions array
2. Drag-and-drop the new entity resource into the array
3. Save your FGD resource

## Saving an FGD

When saving the current scene with <kbd>Ctrl</kbd> + <kbd>S</kbd>, all affected resources are also saved. You can save just the FGD as it's open by clicking the Save icon at the top of the Inspector.

## Updating a Game Definition with a modified FGD

1. Open `config_folder.tres` and add your FGD to the FGD list
2. Click Export File in the Inspector
3. Press <kbd>F6</kbd> in Trenchbroom to refresh entity collections
