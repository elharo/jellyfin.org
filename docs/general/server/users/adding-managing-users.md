---
uid: server-users-managing
title: Managing Users
---

# Managing Users

User management can be done under `Users` in the `Dashboard`. Here you can see your current users, add new ones, and manage your users' settings.

## Adding a User

To add a new user, click the `+` symbol at the top of the page. This opens a new page where you can enter the user's name. This name can either be displayed on the login screen, or typed in by the user. By default, the name will be shown, but this can be changed.

### Manage User Library Access

The `enables access to all libraries` option is enabled by default. Unchecking this option enables you to give the user access rights per library. Libraries can consist of several folders. When new libraries are added, any user that does have access to `all libraries` will not have rights to open the new library.

## Manage a User

To manage a user, either click on their portrait to go straight to their `Profile` tab, or click the `...` symbol inside that user's portrait. The latter  opens a small submenu with four options: `Open`, `Library access`, `Parental control`, and `delete`. Except for delete, these options lead to different tabs but are otherwise all on the same page. `Open` corresponds to the Profile tab, `Library access` to access, `Parental control` to Parental Control, and there is an additional fourth tab `Password` for Password control. Changes to any option on any of these tabs needs to be saved using the `Save` at the bottom of the page.

### Profile

Directly under the tabs, you have a link to `Edit this user's profile, image and personal preferences.` Clicking that allows you to change the user's personal settings. Any setting here can be changed by both user and admin.

Under `name` you can change the user's name. This is either displayed on the login screen or typed in.

Under `Authentication Provider` you have the option to change the backend that handles the login. The only pre-installed option here is `default` which means Jellyfin will handle this user. This option is sufficient for most use cases. Currently, the only other possibility is to have a LDAP server handle the login by installing the LDAP-Auth plugin. If you wish to change a user's provider to LDAP after creating it in Jellyfin, the username needs to be identical to the user's UID in LDAP, including capitalization.

`Allow remote connections to this Jellyfin Server.` Unchecking this option blocks login attempts this user makes from outside the networks defined as local. By default this is the subnet assigned to your network, but others can be added.

#### Feature Access

For the following options it should be noted that if you never set up Live TV, users are blocked regardless of the state. See [the docs page for `Live TV` » `Live TV`](/docs/general/server/live-tv) for more information.

`Allow Live TV access` Unchecking this option blocks the user's access to watch Live TV.

`Allow Live TV recording management` Unchecking this option blocks the user's access to set recording schedules.

#### Media Playback

`Allow media playback` Unchecking this option blocks the user's access to media libraries. This does not include Live TV.

:::note

Find more information in the [transcoding documentation](/docs/general/post-install/transcoding).

:::

`Allow audio/video playback that requires transcoding` Unchecking this option blocks the user's access to video playback that requires transcoding.

`Allow video playback that requires conversion without re-encoding` Unchecking this option blocks the user's access to video playback that requires conversion without re-encoding.

`Internet streaming bitrate limit (Mbps)` Under this option you can set a bitrate limit per stream for all out of network devices.

#### Allow Media Deletion From

These checkboxes allow a user to remove media from `All libraries` or a specific library. Be careful when enabling these as some plugins automatically remove media after watching.

#### Remote Control

These allow a user to control other devices that are currently logged into Jellyfin, for example if you run a separate client on a HTPC without remote control.

`Allow remote control of other users` Allows this user to control what other users are playing and send messages but does not give them administrative rights.

`Allow remote control of shared devices` Allows this user to control unclaimed DLNA devices, and devices they are logged in to at the moment.

#### Download & Sync

These allow a user to download media. Syncing and Transcoding are currently not available.

#### Additional options

`Allow media conversion` This option is currently not available.

`Allow social media sharing` Allows this user to share the URL to web pages containing media information, for example when viewing information about a movie, series, season, or episode.

`Disable this user` Blocks the user from logging in. Existing connections will be abruptly terminated.

`Hide this user from login screens` Useful for private or hidden administrator accounts. The user will need to sign in manually by entering their username and password. All newly created users are hidden by default.

#### Locking and Unlocking users

Locking

`Failed login attempts before user is locked out` Determines how many incorrect login attempts can be made before lockout occurs, disabling the user. 0 means inheriting the default of 3 for non-admin and 5 for admin, -1 disables lockout

When a user is locked out after the set amount of attempts, the user will receive the following message when trying to login to the Jellyfin instance:

```sh
Connection Failure
We\'re unable to connect to the selected server right now. Please ensure it is running and try again.
```

Unlocking

Unlocking a user is a manual process for the Jellyfin administrator. When a user is locked-out, a message appears on the activity feed on the administrator dashboard. To unlock the user, the administrator needs to navigate to the profile of the locked out user. When on the profile of the locked-out user, the following message should appear:

```sh
This user is currently disabled
See below to reenable
```

To reenable the user the administrator must navigate to the `Disable this user` option in the Additional options section uncheck the checkmark and hit `Save`. The disabled user should be able to login again.

### Library Access

These options allow you to restrict access to libraries, or from devices.

`Enable access to all libraries` By default the `Enable access to all libraries` option is enabled. Unchecking this option enables you to give the user access rights per library. When adding a new library, any user that does not have access to `all libraries` will not receive the rights to open the new library.

`Enable access from all devices` By default the `Enable access from all devices` option is enabled. Unchecking this option allows you to specify  user access rights per device. Logins from new devices are blocked until they've been approved here.

### Parental Control

These options allow you to restrict access to specific content by this user, or the timeframe in which they may watch it. Content that matches these restrictions will be hidden, while the timeframe effectively disables the user.

`Maximum allowed parental rating` Allows you to select the highest rating **shown** for this user.

`Block items with no or unrecognized rating information` Allows you to always hide items with no or unrecognized rating information.

`Block items with tags` Allows you to always hide items when they contain specific tags. You add tags to items by editing their metadata.

`Access Schedule` Allows you to set the times when this user is allowed to login. Media can only play during that time and will be stopped outside of it.

### Password

Allows you to set or change the user's password. Users can change their own passwords in their personal settings.

`Reset Password` allows the user to log in without giving a password.

If the user has a password, additional options are shown.
