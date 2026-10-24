# Local GLib 0.18.5 backport

This directory uses the `glib` 0.18.5 source from gtk-rs-core revision
`42b9caf98e03ded086362d9653ca58fe94dc8658`, with the safety correction and
focused regression test in `src/variant_iter.rs`. Its source matches the
crates.io `glib` 0.18.5 archive (SHA-256
`233daaf6e83ae6a12a52055f568f9d7cf4671dabb78ff9560ab6da230ce00ee5`), except
for that correction and test. The original source file SHA-256 was
`1fd02859333761c45321b32f28b24233446b97d0022a90d3a937ed162585b90e`.

The two-line implementation change follows gtk-rs-core PR 1343: make the local
C out-pointer mutable and pass `&mut p` to `g_variant_get_child`. The focused
test covers forward, reverse, nth, and exhausted iterator access.

`Cargo.toml` retains Cargo's normalized manifest from the published 0.18.5
archive. It removes repository-local path dependencies so this Git source keeps
the same registry dependency resolution as the release and does not upgrade the
existing locked `glib-sys`, `gobject-sys`, or `gio-sys` packages.

The backport does not change the package version, assert that RustSec considers
0.18.5 patched, or remove the advisory from review.
