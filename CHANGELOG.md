# Changelog

## [0.2.3]

- Version used by CultivationCraft 0.5.0.
- Added `PoseHandler.getHeightAdjustment(UUID)`: the height adjustment of a player's model, or 0 when their pose handler is not set up yet (a remote player not rendered so far, or a skin still loading). It fixes crashes in multiplayer.
- Fixed player pose handlers being compared by reference instead of by UUID, so a player's handler could not be found again.
- The jar no longer has a build timestamp in its manifest, so it stays the same between builds.

## [0.2.2]

- Version used by CultivationCraft 0.4.x. Earlier changes are listed in the GitHub releases.
