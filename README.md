# TF2_Scripting
Team Fortress 2: Scripts

##Subsystems
| Name          | Purpose       |
| ------------- | ------------- |
| `core`        | Contain the core scripts referenced by TF2; common libraries; and standard class scripts.
| `ctrl`        | 'Control' scripts that encapsulate specific functions.
| `behav`       | 'Behaviour' scripts that add non-functional behaviour to classes.
| `mvm`         | 'MvM' scripts that contains class scripts for MvM; MvM libraries.

##Frameworks
- Default controls can be restored or temporarily changed using `core.core_controls` (execution and `_default` aliases)
- Sets of class scripts can be changed out as sets for different scenarios by setting `script_[class]` aliases
  + `core_class_redir` provides normal setup; generally the same as defaults
  + `mvm_class_redir` provides setup for the MvM mode

##Subsystem Documentation

###Core
> Split into `core`, containing elements not expected to change, and `corez` containing elements that are expected to be modified.

- `[class]` scripts (`core`) as entry points reset controls and provide the framework for class script redirection
- `autoexec` (`corez`) as an initial entry point sets up libraries and sets the initial set of class scripts
- `core_voice` (`core`) provides friendly aliases for `VoiceMenu` parameters
- `core_controls` (`corez`) contains default bindings and aliases that can be used to reset changes made by other scripts
- `core_class_redir` (`core`) provides the redirects to the `core_` set of class scripts
- `core_[class]` (`corez`) are the set of class scripts for standard TF2

###Control
> These scripts make assumptions about the default bindings, as there is no framework to provide a level of indirection.

- `ctrl_NoAutoReload` (`Mouse2`) disables automatic reloading while Mouse2 is held, and then restores it to the default value
- `ctrl_SecondaryAttack` (`q`) switches to the secondary weapon and uses it, before switching back (e.g. for Banners and Jars)

###Behaviour
> These scripts make assumptions about the default bindings, as there is no framework to provide a level of indirection.

Scripts within this subsystem make use of the `behav_cleanup` alias to reduce the number of bound aliases to those actually in use.
- `behav_ActionScout` (`space`) uses the action item slot when jumping (e.g. for noisemakers)
- `behav_AngryHeavy` (`Mouse2`) calls out the Battlecry when spinning up/down the minigun
- `behav_JollyDemo` (`Mouse2`) calls out Positive when detonating stickies (frequency limited)
- `behav_JollyHeavy` (`Mouse1`, `Mouse2`) calls out Positive/Cheers based on minigun spinup/firing state transitions
- `behav_SpamScout` (`space`) calls out Battlecry when jumping (frequency limited) (e.g. for Halloween items)

###MvM
MvM class scripts assume that the loadout is in slot A, and assign some controls based on expected loadout.
- `mvm_class_redir` provides the redirects to the `mvm_` set of class scripts
- `mvm_[class]` scripts are the set of mvm scripts for standard TF2
- `mvm_rules` provides aliases for some common phrases
