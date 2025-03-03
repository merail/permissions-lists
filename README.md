According to the [documentation](https://developer.android.com/guide/topics/permissions/overview#types), permissions in Android can be divided into three groups: install-time (the system automatically grants your app the permissions when the user installs your app), runtime (when your app requests a runtime permission, the system presents a runtime permission prompt) and special (the user must go to the application settings to grant permission). Based on this division, the following is implemented in this repository:

1. All permissions from the source code of the API levels 34 and 35 (Android 14 and 15) Manifest are collected. You can find them in the [permissions.xml](https://github.com/merail/permissions-lists/blob/main/permissions.xml) file.
2. All install-time permissions are collected in a separate file [install_time_permissions.xml](https://github.com/merail/permissions-lists/blob/main/install_time_permissions.xml). This list contains all permissions with [protection level](https://developer.android.com/reference/android/R.attr#protectionLevel) NORMAL.
3. All runtime permissions are collected in a separate file [runtime_permissions.xml](https://github.com/merail/permissions-lists/blob/main/runtime_permissions.xml). This list contains all permissions with protection level DANGEROUS.
4. All special permissions are collected in a separate file [special_permissions.xml](https://github.com/merail/permissions-lists/blob/main/special_permissions.xml). This list contains all permissions with **appop** protection flag and not with the NORMAL protection level.

All permissions not subject to these conditions have been combined into an additional group SYSTEM ([system_permissions.xml](https://github.com/merail/permissions-lists/blob/main/system_permissions.xml)).
>[!NOTE]
>In other words, SYSTEM are all permissions with protection level SIGNATURE or deprecated SIGNATURE_OR_SYSTEM without the **appop** flag, as well as permissions with protection level INTERNAL.

Among other things, in [min_sdks.xml](https://github.com/merail/permissions-lists/blob/main/min_sdks.xml) you can find "masks" with required min SDK for all permissions from [permissions.xml](https://github.com/merail/permissions-lists/blob/main/permissions.xml): if the permission requires min SDK > 21, in this file the value with the corresponding index will indicate the numeric value with the required SDK, otherwise value **-1** will be indicated there. Also in [deprecated_permissions.xml](https://github.com/merail/permissions-lists/blob/main/deprecated_permissions.xml) you can find all currently deprecated permissions.
> [!WARNING]
> These lists are completely relevant only for API level 34+.

>[!NOTE]
>You can use the [request-permissions-tool](https://github.com/merail/request-permissions-tool) for handling permissions.
