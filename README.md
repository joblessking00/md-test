# 깃허브에서 그려지는 것들

## 머메이드 (도표)

```mermaid
flowchart LR
    A[아이디어] --> B{그림이 필요한가}
    B -- 예 --> C[SVG 파일로 저장]
    B -- 아니오 --> D[글로 작성]
    C --> E[README에서 불러오기]
    D --> E
```

## GeoJSON (지도 위 도형)

```geojson
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "properties": { "name": "한라산" },
      "geometry": {
        "type": "Point",
        "coordinates": [126.53, 33.36]
      }
    },
    {
      "type": "Feature",
      "properties": { "name": "제주도 영역" },
      "geometry": {
        "type": "Polygon",
        "coordinates": [[
          [126.15, 33.25],
          [126.95, 33.25],
          [126.95, 33.57],
          [126.15, 33.57],
          [126.15, 33.25]
        ]]
      }
    }
  ]
}
```

## STL (3D 모델)

```stl
solid tetrahedron
  facet normal 0 0 -1
    outer loop
      vertex 0 0 0
      vertex 5 8.66 0
      vertex 10 0 0
    endloop
  endfacet
  facet normal 0 -0.943 0.334
    outer loop
      vertex 0 0 0
      vertex 10 0 0
      vertex 5 2.89 8.16
    endloop
  endfacet
  facet normal 0.816 0.471 0.333
    outer loop
      vertex 10 0 0
      vertex 5 8.66 0
      vertex 5 2.89 8.16
    endloop
  endfacet
  facet normal -0.816 0.471 0.333
    outer loop
      vertex 5 8.66 0
      vertex 0 0 0
      vertex 5 2.89 8.16
    endloop
  endfacet
endsolid tetrahedron
```
