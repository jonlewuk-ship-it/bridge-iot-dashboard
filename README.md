# Bridge IoT Dashboard (proxy / simulated data)

Standalone monitoring dashboard for bridge digital twins, built to embed in GeoTwin (or any iframe host).
It contains no API keys and makes no server calls, so it is safe to leave public.

## Deploy
Vercel → Add New Project → import this repo → Framework Preset **Other**, leave Build/Install/Output empty → Deploy.
Then **Settings → Deployment Protection → Vercel Authentication: Disabled** (otherwise iframes show blank).

## URL options
`https://<domain>/?project=My%20Bridge&compact=1&theme=light&scenario=storm&sensor=LOAD-STAY-T1M14`
- `scenario`: normal | traffic | storm | flood | stay | heat
- `sensors`: URL of a CSV/JSON exported from the Parametric Modeller (needs CORS)

## postMessage API
- Out: `ready`, `status`, `statusAll`, `select`, `event`, `alarm`, `ack`, `ops`
- In: `focusSensor`, `setSensors`, `setProject`, `setScenario`

## Limits
Values and other users are simulated. Presence and alarms only reach other tabs in the same browser (BroadcastChannel).
Thresholds and settings are saved in localStorage per browser. Real multi-user alarms need a backend.
