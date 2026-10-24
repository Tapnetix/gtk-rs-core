# Local GLib 0.18.5 backport

This directory is the unmodified crates.io `glib` 0.18.5 source except for the
small `VariantStrIter::impl_get` safety correction in `src/variant_iter.rs` and
a focused regression test in that same file. The source is crates.io `glib` 0.18.5
from upstream git revision
`42b9caf98e03ded086362d9653ca58fe94dc8658`, recorded in
`.cargo_vcs_info.json`). Its archive SHA-256 is
`233daaf6e83ae6a12a52055f568f9d7cf4671dabb78ff9560ab6da230ce00ee5`; the
original cached source file SHA-256 for `src/variant_iter.rs` is
`1fd02859333761c45321b32f28b24233446b97d0022a90d3a937ed162585b90e`.

The two-line implementation change follows gtk-rs-core PR 1343: make the local
C out-pointer mutable and pass `&mut p` to `g_variant_get_child`. This is a
downstream source backport only. It does not change the package version, assert
that RustSec considers 0.18.5 patched, or remove the advisory from review.

The original crate manifest, README, COPYRIGHT, and LICENSE are retained from
the crates.io source.
