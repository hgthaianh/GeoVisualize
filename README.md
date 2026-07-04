# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some Oxlint rules.

## Forest cover and valuation API

The React app calls a local Python API for Microsoft Planetary Computer analysis:

```bash
python -m pip install -r scripts/requirements-pc-cover.txt
npm run cover-api
```

Run the Vite app in another terminal:

```bash
npm run dev
```

The API listens on `http://127.0.0.1:8765` and receives the selected KML polygon as GeoJSON. It searches Sentinel-2 L2A scenes through Microsoft Planetary Computer STAC, clips `B04/B08/SCL` by the polygon, masks cloud classes from SCL, calculates:

- `tree_area_pct`: NDVI >= 0.45
- `dense_canopy_pct`: NDVI >= 0.60
- `fvc_density_pct`
- AOI cloud and valid pixel percentage
- acacia yield/value estimates from the selected model, age, soil, rainfall, and VND/m3 price

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Oxc](https://oxc.rs)
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/)

## React Compiler

The React Compiler is not enabled on this template because of its impact on dev & build performances. To add it, see [this documentation](https://react.dev/learn/react-compiler/installation).

## Expanding the Oxlint configuration

If you are developing a production application, we recommend using TypeScript with type-aware lint rules enabled. Check out the [TS template](https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts) for information on how to integrate TypeScript and Oxlint's TypeScript related rules in your project.
