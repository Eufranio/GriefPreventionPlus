####11.0.1
Applied all GP's patches up to 11.0.1 except commits: 
- 97c9347 Fixed a protection bug with pistons + slime blocks. (I can't apply this on MC 1.7 version)
- e28bb8a Logging for suspicious bucket dumps. (I don't need this)

Bug fix for getNearbyClaims.

New commands:
- Added /claim [range] - claim with a specified range around your position.
- Added /deleteclaim [id] - delete a claim by id.


####10.6.3 - Initial release
- Skipped GP 10.6.2 commit. Untrust in top level claims won't untrust in subdivisions.

- Now all claims and subdivisions have an unique ID. Right-click with a stick in your own claim shows the claim ID.
- Added a PermissionBukkit permission to every claim. The format is gpp.c(CLAIMID).(m/b/c/a) Example: if claim id is 27, build permission will be gpp.c27.b (this is very useful for other mods and GPP extensions -Kai)
- When a manager tries to untrust someone, he needs the same or higher permission of the player he wants to remove.
- Brackets are required when trust/untrust a "PermissionBukkit" permission.
- Server log entry for new claims, resizes, transfer, trust, untrust, abandon. Useful for checking what your users do.
- Claims will always respect MaxDepth specified on the config file. Blocks under the claim at y-level MaxDepth will be always unprotected. This is default to 0 (claims are protected from y level 0 to 255)
- Removed file-based storage. A MySQL database is required. Performances and data integrity are a MUST!
- Removed Player name to UUID migration and UUID Fetcher. Any playerdata/claim without an UUID will be removed (players who haven't join your server since you updated your bukkit server to MC 1.7.5 or higher.)
- Removed Last login field from PlayerData (Bukkit has an integrated "last login", so this was a duplicate)
- Redesigned MySQL tables for performance and efficiency. No more inefficient way to store data like binary data as text. No more  "delete, then insert again" queries, but "update" queries. Added indexes and unique fields in order to use MySQL's performances. (In my opinion, GPP is more than 10 times faster than GP in some cases like a claim resize. -Kai)
- Permissions are now stored as int. Bit-wise operators are used to manage permissions.
- Shift+Right Click with a stick to see all nearby claims is now enabled by default for all users (permission: griefprevention.visualizenearbyclaims)
- Changed claim ID from Long to Integer. (I don't think a server can reach more than 2 billion claims. You need about 80 GB of RAM to handle that amount. Moreover, MySQL claim id field was already Int, so that Long is a waste of resources. -Kai)
- Changed claim location to a custom one (performances and resources improvements)
- Renamed class CreateClaimResult to ClaimResult
- Enum ClaimPermission now has all permissions uppercase and Inventory is renamed to CONTAINER
- Fixed claim resizing bugs in some cases.
- Some other minor fix
