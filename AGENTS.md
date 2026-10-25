<!-- LOVABLE:BEGIN -->
> [!IMPORTANT]
> This project is connected to [Lovable](https://lovable.dev). Avoid rewriting
> published git history — force pushing, or rebasing/amending/squashing commits
> that are already pushed — as it rewrites history on Lovable's side and the
> user will likely lose their project history.
>
> Commits you push to the connected branch sync back to Lovable and show up in
> the editor, so keep the branch in a working state.
<!-- LOVABLE:END -->

- Keep camera pulse capture browser-only in the Health section and signal analysis in a pure module backed by fft.js, so privacy, device cleanup, and quality rejection remain independently testable.
- Camera pulse readings are transient estimates: do not write them into manual blood-pressure records or infer blood pressure from camera images.
- The Map screen renders the real Google Maps JavaScript API (managed browser key, loading=async + callback + channel) centered on the fixed school anchor; do not replace it with hand-drawn SVG maps.
- Rankings and grade totals must derive only from registered users' stored activity, with empty totals starting at zero; never seed fictional participants or aggregate offsets because they distort the school competition.
- Custom CSS and SVG colors must reference the scoped semantic variables (such as --card and --foreground), not Tailwind --color aliases, so nested theme switches resolve at the element rather than inheriting root colors.
- Tracking listeners belong to the active training session, with cleanup on pause, stop, hiding, and unmount; never mount a global automatic counter or promise locked-screen browser tracking.
- Cloud Auth owns account identity; preserve email-keyed UI state only as an adapter, never as authentication or plaintext password storage. Private account tables are owner-scoped; competition RPC exposes only name, grade, totals, and streak.
- Activity is stored by atomic, idempotent UUID operations with a per-account durable retry queue, while Realtime competition notifications refresh server-derived rankings. Protected content lives under the shared authenticated layout.
- A student's grade must be explicitly chosen before their activity counts toward a grade total: email signups pick it in the signup form, social identities confirm it in the profile wizard (and can change it in Ajustes), and the confirmation flag lives on the profiles row so no account can be silently assigned to a grade.
- Phone packaging is manifest-only (public/manifest.webmanifest plus generated icons under public/); never add a service worker, because the app needs the network for cloud accounts and a cache would serve stale screens in the Lovable preview.
