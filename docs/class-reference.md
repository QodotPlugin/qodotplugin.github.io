# Warning

This class reference is incomplete. You can help complete it by [making an issue on GitHub](https://github.com/QodotPlugin/qodotplugin.github.io/issues/new) or [contributing to the class reference directly](https://github.com/QodotPlugin/qodotplugin.github.io).

# QodotFGDFile

**Fgd Name**

Reserves a namespace for your entity definitions in Trenchbroom under this name.

Note
{: .label .label-blue }
Trenchbroom will throw an error if you use two FGDs with the same Fgd Name. If you have Qodot.fgd as a base, make sure to change your own Fgd Name to something else.

**Entity Definitions**

An array containing Entity Definition resources.

Note
{: .label .label-blue }
Trenchbroom will fail to load any entity definitions missing a classname.
