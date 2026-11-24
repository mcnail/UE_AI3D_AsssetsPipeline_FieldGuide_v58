# Tripo Agentic Canvas — 부품 분리·조립 프롬프트

실제로 작동한 위성 프롬프트를 기준으로 만든 기본형과, 그것을 탐사선에 적용한 예시입니다.

## 1. 기본형

```
Use the attached original image ({SUBJECT}) to create a fully editable asset. Ignore any previous assets on this canvas.

[Workflow]
1. Generate ONE single image with an Image Generation node (do NOT create a Multi-view node): a 2×2 orthographic reference sheet of the same object — front (top-left), left (top-right), right (bottom-left), back (bottom-right) — plain light-gray background, same scale and camera height in every panel, each panel captioned with its view name, "AGENT_REFERENCE_ONLY" printed at the top. Use the original image as reference input. Keep proportions, part count, and layout consistent across all four panels. This sheet is for the final Agent only; do not use it for extraction or HD generation.
2. Extract ≤{N} actual component groups, each with a separate reference image:
{GROUP_LIST}
   {SYMMETRY_RULE}
3. For every group, execute separately, verbatim: "Create an HD model from this image with Texture turned on." Do not merge/rewrite it.
4. Disable retopology, Smart UV, and independent texture generation; keep TOTAL triangles across all components ≤500,000.
5. After each HD model, add a PBR node and use existing textures to produce usable Base Color, Metallic, Roughness, Normal, AO.{EXTRA_MAPS}
6. Connect to the final Agent: all PBR outputs, the single reference sheet, and the original image node. Also attach the sheet and the original image directly into the final Agent's context, not only as wires.

[Final Agent only]
The Agent must assemble the asset from the original image and the reference sheet: {PLACEMENT}
Create and assign physical materials:
{MATERIALS}
Do not redesign/regenerate textures. Validate side/back and three-quarter views, lighting, reflections, {CONTACT_CHECK}, and joints between the body and each attached part (no gaps or interpenetration). Deliver an editable scene with {DELIVERABLE_OBJECTS}, connected PBR materials, and final render.
```

## 2. 칸 채우기 일람표

| 칸 | 넣을 내용 |
|---|---|
| `{SUBJECT}` | 대상과 스타일 한 줄 |
| `{N}` | 최대 그룹 수 |
| `{GROUP_LIST}` | `NAME: 포함할 부품들` 형식으로 한 줄씩 |
| `{SYMMETRY_RULE}` | 같은 부품이 반복되면 `The two X are identical. Extract only one.` / 비슷해 보여도 다른 부품이면 `A and B are different parts. Do not mirror one onto the other.` / 해당 없으면 줄 삭제 |
| `{EXTRA_MAPS}` | 필요한 경우만 추가. 망사: ` Add Opacity only if X is see-through.` / 유리·보석: ` Add Opacity and Transmission for transparent parts.` |
| `{PLACEMENT}` | 부품별 위치를 쉼표로 나열 |
| `{MATERIALS}` | `- 재질 (metal 또는 dielectric, roughness)` 형식으로 한 줄씩 |
| `{CONTACT_CHECK}` | 바닥 접촉 항목. 예: `footpad-ground contact` |
| `{DELIVERABLE_OBJECTS}` | 최종 오브젝트 수와 이름 |

## 3. 적용 예시 — 탐사선

```
Use the attached original image (abandoned space probe, weathered retro style) to create a fully editable asset. Ignore any previous assets on this canvas.

[Workflow]
1. Generate ONE single image with an Image Generation node (do NOT create a Multi-view node): a 2×2 orthographic reference sheet of the same probe — front (top-left), left (top-right), right (bottom-left), back (bottom-right) — plain light-gray background, same scale and camera height in every panel, each panel captioned with its view name, "AGENT_REFERENCE_ONLY" printed at the top. Use the original image as reference input. Keep proportions, part count, and layout consistent across all four panels. This sheet is for the final Agent only; do not use it for extraction or HD generation.
2. Extract ≤4 actual component groups, each with a separate reference image:
   ANTENNA: dish with support wires, twin-lens stereo camera head, vertical mast with brass bands, base flange
   BODY: main box, silver and gold foil insulation, side robotic arm, small top fittings, bottom lugs
   OPTICS: large hooded camera, rotating turret base, bent pipe
   SOLAR: one folded solar wing (three stacked panels + hinge rod + mounting bracket)
   The two solar wings are identical. Extract only one.
3. For every group, execute separately, verbatim: "Create an HD model from this image with Texture turned on." Do not merge/rewrite it.
4. Disable retopology, Smart UV, and independent texture generation; keep TOTAL triangles across all components ≤500,000.
5. After each HD model, add a PBR node and use existing textures to produce usable Base Color, Metallic, Roughness, Normal, AO.
6. Connect to the final Agent: all four PBR outputs, the single reference sheet, and the original image node. Also attach the sheet and the original image directly into the final Agent's context, not only as wires.

[Final Agent only]
The Agent must assemble the asset from the original image and the reference sheet: main body at center, optics on the body top front-left, antenna mast on the body top right of center, solar wing on the left side of the body and a mirrored copy on the right side, bottom lugs on one ground plane.
Create and assign physical materials:
- weathered beige-silver painted metal with orange rust lines (dielectric paint, mid roughness)
- brass/gold rivets, bands, and fittings (metal)
- silver and gold foil insulation (metal, low roughness, crinkled normal)
- gunmetal steel mast and pipes (metal, mid roughness)
- solar cells (dark navy with gold grid lines, glossy, opaque)
- black rubber caps (dielectric)
- camera lenses (dark coated glass, low roughness; Transmission with IOR ≈1.5 optional)
Do not redesign/regenerate textures. Validate side/back and three-quarter views, lighting, reflections, lug-ground contact, and joints between the body and each attached part (no gaps or interpenetration). Deliver an editable scene with five objects (BODY, OPTICS, ANTENNA, SOLAR_L, SOLAR_R as a mirrored copy), connected PBR materials, and final render.
```
