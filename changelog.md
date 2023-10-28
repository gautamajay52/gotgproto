# GoTGProto Changelog
---
---
## v1.0.0-beta10
#### Released on 22 May, 2023
- Updated GoTD to v0.82.0
- Deprecated `ctx.ForwardMessage` (Use `ctx.ForwardMessages` now)
- Replaced BigCache with AnimeKaizoku/Cacher for caching peers
- Fixed high memory usage by gotgproto (uses around 5MBs now, earlier it was 100+ MBs)
- Rewrote GoTGProto client, it should be more handy to create a new client now
- Added a new `dispatcher.Dispatcher` inteface
- Renamed `dispatcher.CustomDispatcher` to `dispatcher.NativeDispatcher`
- Optimised command and message handlers
- Added new `types.Message`, which is a union of `tg.Message`, `tg.MessageService`, `tg.MessageEmpty`
- `ext.Update.EffectiveMessage` is of type `*types.Message`
- Added a new optional field in ClientOpts, named `AutoFetchReply` (setting this field to true will automatically cast ReplyToMessage field)
- Save peers of logged in user in session, while logging in.
- Added `client.ExportSessionString()`, `client.RefreshContext(ctx)` and `client.CreateContext()` methods to `gotgproto.Client`.
- Remove an unintentional display of session data in `Stdout`.
- Added `SystemLangCode` and `ClientLangCode` optional fields to `gotgproto.Client`.
- Moved helper methods errors to `errors` package (gotgproto/errors)
- Added `gotgproto.Client.Stop()` to cancel the running context and stop the client.
- Added `dispatcher.StopClient` handler error, which if returned through a handler callback will result in stopping the client.
- Added `gotgproto.Client.Start()` to login and connect to telegram (It's already called by gotgproto.NewClient so no need to call it again. however, it should be used to re-establish a connection once it's closed via `gotgproto.Client.Stop()`)
- Fixed session database initialisation happening twice per login.
---
## v1.0.0-beta13
#### Released on 24 September, 2023
- Updated to GoTD to v0.88.0 (Layer 164)
- Redesigned session initialization (Now supports logging in with just string session in memory as well as session file)
- Added `Middlewares` and `Device` fields to `ClientOpts`
- `ForwardMediaGroup` won't omit error now