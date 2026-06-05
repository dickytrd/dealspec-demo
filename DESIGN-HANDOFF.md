# 6963a684-6720-4a79-b9ac-e353b85ea4dd implementation handoff

This archive is the source of truth for turning the design into production code. Start from `index.html`, then preserve the visual system, responsive behavior, and interactions found in the exported files.

## Implementation target
- Build production UI from the exported design, not a loose reinterpretation.
- Preserve typography scale, spacing rhythm, color tokens, border radii, shadows, motion timing, and component states.
- Replace static placeholders only when the target app has real data or functional equivalents.
- Keep generated product UI free of Open Design chrome, preview labels, or design-process annotations.
- Treat this handoff as a visual contract: if implementation choices conflict, match the exported pixels and behavior first, then refactor internals.

## Source map
- Primary entry: `index.html`
- HTML screens detected: 13
- Stylesheets detected: 1
- Script/component files detected: 1
- Supporting assets detected: 360

## Responsive contract
Validate the implementation across this 2025–2026 viewport matrix:
- Mobile compact: 360×800
- Mobile standard: 390×844
- Mobile large: 430×932
- Foldable / small tablet: 600×960
- Tablet portrait: 820×1180
- Tablet landscape: 1024×768
- Laptop: 1366×768
- Desktop: 1440×900
- Wide desktop: 1920×1080

For responsive web exports, treat these as a modern breakpoint system for one adaptive web experience, not three fixed screenshots. Do not split responsive web into unrelated native app screens unless the project explicitly includes native targets. Use semantic layout thresholds, fluid `clamp()` type/spacing, and container queries where component width matters more than viewport width. Preserve any CSS media queries, container queries, fluid `clamp()` scales, and layout changes already present in the exported files.

## Design fidelity contract
- Extract reusable tokens before writing components: background, surface, foreground, muted text, border, accent, radius, shadow, spacing, type scale, and motion duration/easing.
- Map product screens, in-app modules/components, optional landing page, and optional OS widget surfaces before coding. Keep these surfaces separate in the target architecture.
- Match layout geometry: max-widths, gutters, grid columns, card proportions, sticky/fixed elements, and viewport-specific navigation.
- Preserve real copy, labels, and data shown in the export. Do not replace specific text with generic marketing filler.
- Preserve interactive affordances: hover, focus, pressed, disabled, loading, validation, copy/share, tab/accordion, modal/sheet, and keyboard states where present.
- Preserve accessibility semantics when converting: headings stay hierarchical, controls remain buttons/links/inputs, focus states stay visible.
- Do not keep prototype-only annotations, frame labels, or Open Design chrome in the production UI.

## CJX-ready UX contract
- Use `DESIGN-MANIFEST.json` as the machine-readable map for screens, app modules, OS widgets, landing pages, tokens, interactions, and viewport checks.
- Screen-file-first: when multiple user-facing surfaces exist, implement each HTML screen as its own route/file. Treat `index.html` as a launcher/overview when the manifest marks it that way, not as a combined final UI.
- If `landing.html`, app screens, platform screens, or OS widget files exist, preserve those boundaries in the target app instead of merging them into one page.
- A single self-contained `index.html` is acceptable only when the export truly contains one user-facing screen and its CSS/JS are structured enough to extract tokens, components, states, and behavior.
- If separate `css/` or `js/` files exist, treat them as source of truth for token/component/interactions before porting to React, Vue, SwiftUI, Compose, or another target stack.
- In-app modules/components are product UI blocks inside the app. OS widgets are home-screen/lock-screen/quick-access surfaces outside the app. Do not merge those concepts.

## Color and brand contract
- Use the exported design tokens and product/domain context as the color source of truth.
- Do not introduce warm beige / cream / peach / pink / orange-brown background washes unless they are already explicit brand/reference colors in the export.
- A stylesheet or design/token file was detected; inspect it for canonical color variables before choosing framework theme tokens.

## Implementation sequence for AI coding tools
1. Open `index.html` and `DESIGN-MANIFEST.json`; identify every screen file, launcher/overview file, app module, and interaction before coding.
2. If multiple HTML screens exist, map them to separate routes/surfaces first; do not merge `landing.html`, product app screens, platform screens, or OS widgets into one route.
3. Extract a token table from CSS/root styles and inline styles before building framework components.
4. Build product screens and domain-specific in-app modules from largest layout regions down to controls; avoid starting with isolated atoms that lose spatial intent.
5. Port responsive behavior across the modern viewport matrix and test each semantic breakpoint before cleanup.
6. Port interactions and states, then replace static placeholders only with real app data or functional equivalents.
7. Keep optional landing page and OS widget surfaces as separate surfaces if present.
8. Compare final screenshots against the export at 360×800, 390×844, 430×932, 820×1180, 1024×768, 1366×768, 1440×900, and 1920×1080 before declaring done.

## Entry points
- `components/all-request-hiw.html`
- `components/all-request.html`
- `components/centralized-flow.html`
- `components/document-management.html`
- `components/longlist-cards.html`
- `components/qa-management.html`
- `components/workflow-efficiency.html`
- `dealspec-homepage.html`
- `index.html`
- `service-overview-2.html`
- `services-homepage.html`
- `software-detail.html`
- `software-overview.html`

## Styles
- `shared-components.css`

## Scripts/components
- `figma-data/component-code.jsx`

## Assets and supporting files
- `assets/backgrounds/bg-callout.png`
- `assets/backgrounds/bg-hero.png`
- `assets/figma/00aee0eb9a953216622a4e0a0d33c2a36d6b7171.svg`
- `assets/figma/01777e6c618d06519db6d13a5e68d77152aef2b3.svg`
- `assets/figma/01dcc2882b4b4d3da8a1171daa4afac61ed33242.svg`
- `assets/figma/02fafbed5a4db88e217b326453811264c175f972.svg`
- `assets/figma/075026980f4c5609105512214f27af2057db6f7e.svg`
- `assets/figma/0c1cb3c92862a850f4e64206aef9182820820c41.svg`
- `assets/figma/0eb38a2ddf9990726ba1c7a1b5880f510c982644.png`
- `assets/figma/0f6247d12799416e568bb808cd5daff5cd8072b8.png`
- `assets/figma/10973467f94b76b8212da5be4b388454f7b0dcb9.svg`
- `assets/figma/10c13ac1a228a365cb98a0064b1d5afbc84887b2.png`
- `assets/figma/13cb6e9ed1c12933f1b852081940dc845e719587.svg`
- `assets/figma/1553935576692afad4c28c8fbc1273519c23dd9d.png`
- `assets/figma/16f59338315afce91b1a5ab1236b08f9fa43e09b.svg`
- `assets/figma/1bd200cd3e0621d36d34b41c3137374022493589.png`
- `assets/figma/1f9f8effde2eccb289ff28cbe6300d7352210203.svg`
- `assets/figma/20e1e500c6539c23085677d7928fad9acafebda9.svg`
- `assets/figma/21a5b54985b89fd2258d331e2aff5913b90499db.svg`
- `assets/figma/220bc3b1cca14a86c9b6298749ba04b798b06ac3.svg`
- `assets/figma/2607102b0c72920c87f3228d1be290d89cb741cb.png`
- `assets/figma/2d0e0aae39845746e05255f7e46950ceaae401cc.png`
- `assets/figma/2db7611239bb7eaee44c887f69e2e7fe90835cdb.svg`
- `assets/figma/2e3c01f7c78fd5c13eed4614226fba58851ef420.svg`
- `assets/figma/2e8d6685a05c98e09b42d791a63cdf726a018424.svg`
- `assets/figma/2eaa0141a646592051bc1bca9dfcb16eac467f98.svg`
- `assets/figma/2f5508f8585ba026cbaefa902dd56ede3ce823c2.svg`
- `assets/figma/33be1fc3f95b8acd7a2908d53b17a14be3301da2.svg`
- `assets/figma/346f926b8fbec2e79fc1b3709d35072d1b696ebb.png`
- `assets/figma/35fb3e570229393a40b5631ab68408e64d6edd24.png`
- `assets/figma/364412979b408782e95cac662a0a8690ae0f0a10.svg`
- `assets/figma/389a7fcb89b57c9e93c0043597d846e6986eae4b.png`
- `assets/figma/3cd103111c2f9e1c01f694742042f1e944802cbf.png`
- `assets/figma/3de2056e514dd7aaf8ce065a999bccc96515b45a.png`
- `assets/figma/40da1e79cc3fc967d0bb2609617e499b026a420c.svg`
- `assets/figma/43c7fe3495b5829ec9de6b268e7b71bfa1eabdae.svg`
- `assets/figma/49358a7f7192bb6fbee5329ae044a99d0b147446.svg`
- `assets/figma/4935dfa074c4bcc4caec40f52192b5763307af3d.svg`
- `assets/figma/4c689a7e48bfcc3055190a69a1a2b478a72a3eed.svg`
- `assets/figma/4f003ed4a29f7634838caea244ca67e71bc3bb13.svg`
- `assets/figma/51ef8f4a86931a451466ebf6b2ee9b51c44dd394.png`
- `assets/figma/534d6c2d22a92b3ce8a8d3d5dd6e303bc1cc527d.svg`
- `assets/figma/586ab8abb1fc0a40bd076cf581546ebe0b0a5372.svg`
- `assets/figma/5e27f8f0cc978024040832bcdf86091912c6a0c6.svg`
- `assets/figma/5e5497e8efe127e3d16e2131542c5fde48ffa564.png`
- `assets/figma/5ecdbe3963a19987518249a04a3548f9e5d46eae.svg`
- `assets/figma/619e4cd489076d0c2f5efcef368314bfff308ae5.svg`
- `assets/figma/645afcb2bfb5961945b434e9f5fe915b6b8f3f48.svg`
- `assets/figma/64dae2934cbc5d10c6373725deed285714eb08af.svg`
- `assets/figma/64e60e0ab71799484666e24f5e735a2b3d1311b8.svg`
- `assets/figma/652c66f4997542bede7ac72f34d6e26ac86fc447.png`
- `assets/figma/67eb260f896fb52385d8a77d199101f392bd8a35.svg`
- `assets/figma/6cd81accf697290e6e0897ca2f1d5483d34b9a17.png`
- `assets/figma/6cea9a84a64cf689ff703767d9e5ad3edd697652.svg`
- `assets/figma/6d23e20e0a94e6fc7f23d6c2d60e2b9bcafad20a.svg`
- `assets/figma/6eab7b782cb003f881f034735209cb43a2b0cb57.svg`
- `assets/figma/70038459812d97ce8264967aa663c6f5057eafee.png`
- `assets/figma/72ba56042b5d5dd2abcccd6d095f405a4e223458.png`
- `assets/figma/744e4f934bc64fdc56855bfc162a6af00d10bcfb.png`
- `assets/figma/7640fa53b78f3429f4f7c0374d159bd4a66693ce.svg`
- `assets/figma/76b8233fe172047808e84991c0492ed4ac2680f1.png`
- `assets/figma/76eb72c3a1bef4e57c304bca9bc60b32ca2f3ca0.svg`
- `assets/figma/7a741ff63816f728d196c21c18ec72dc696a2f33.svg`
- `assets/figma/7e82f82e15c93c4506ee2e90f68e758b073432f1.png`
- `assets/figma/7f9e11616f5323d383e7ed948deacaff9f323477.svg`
- `assets/figma/80c3af49be56523ec51887eebb642cb835944a0d.svg`
- `assets/figma/83f333b8a51159bbc1b840d4860a80a4705701af.svg`
- `assets/figma/85b9ef8502927dae1ec99ecf2d10ac5411047d32.svg`
- `assets/figma/85ff153e25477b6b93b0a18478614d1aaa0e51e7.png`
- `assets/figma/87cd3ecdb66e739002620b0ef9b520e6013755f5.png`
- `assets/figma/8a348b30b5ea94f67daa33af8b4c837b800d0dc4.svg`
- `assets/figma/8b4b7dafbd78fff603d6566df68c4b03d8179b11.png`
- `assets/figma/8ff6c4b975a5dcff7347bb8a72278be16a6a2e01.svg`
- `assets/figma/930fc0fbc3124e38d70cb83d984d8d47658cf5a3.svg`
- `assets/figma/95e951b2a450c2e8d036b5b7d003b8a1b39795aa.png`
- `assets/figma/95fe30c729801b1a6303c7435194624ce33f8f51.png`
- `assets/figma/960281453f803a6a9c03979a07b1d7fc65d92607.svg`
- `assets/figma/966b1be0b9e0763ec67075fe9e82c13cbeffda54.png`
- `assets/figma/9834067669fd7c52d65f9c6a5d3bb654048b9d51.svg`
- `assets/figma/993c7e3a37f09c72c46f9df6de9995897b3798df.svg`
- `assets/figma/9c765257b06be19c93b707de4ea32d3a9dedde91.svg`
- `assets/figma/9dd67efbabbd6099058bc5258c32d6468cad89b6.svg`
- `assets/figma/a1e120ed183bd3fe804a20b87cc79868308b48b3.png`
- `assets/figma/a31df0da719fb569a853dc504de9abe9fb64b958.png`
- `assets/figma/a5470b3e7a3d6f072eb861236234c8bda4b8f2d5.svg`
- `assets/figma/a6f03734584298e3888dcea1a7cf448da6116eb2.svg`
- `assets/figma/a7faf0dd484f0bf6ce0adb6ec08968c8d6b2dab5.svg`
- `assets/figma/aaa56b243be0074faf90a7ba4950b241413656dd.svg`
- `assets/figma/acc2d0d9300641887d9296979a695a709a4477b9.svg`
- `assets/figma/b2cc592f86dc03638a783c695df156ea1b6fc3ea.svg`
- `assets/figma/b2d98fe9240992f6ae1d7dd33be66e1a09d1c662.svg`
- `assets/figma/b3e6f51bad969d6e6e6f30d7c0c9c3514e0a7c18.svg`
- `assets/figma/b53ef57731f653cecae1671a3f32d3c992530c25.png`
- `assets/figma/b9db56c78ee125a10c214b7b07f8afa28d9a08af.svg`
- `assets/figma/ba517d70dac51441854467c4b73d3fbe4a43088b.png`
- `assets/figma/baea502353cac1f2fe871205b8726706d0869c6a.png`
- `assets/figma/bb558cacb5aa7fc7db10f6ead13a069be56a7b91.svg`
- `assets/figma/bf40acd30b98abf3f63865be24ff6f6848ef4ca0.svg`
- `assets/figma/c3a6cbdba2d937ea7da1f8d94d637aa6c378d5b4.svg`
- `assets/figma/c6f7ab9be6e9f222dd85956256f2000e5ac0149c.svg`
- `assets/figma/cb512e97ea65e5084bdb6017e666040d4fe594d3.svg`
- `assets/figma/cd8134532c605ea56744efdc3aead81c8920241b.svg`
- `assets/figma/d0db2ba4403651667b3d52638698ca1187cc0526.png`
- `assets/figma/d25290bce5d0964ec942c4e03654a4799a5a12ff.png`
- `assets/figma/d55830a6235d7ea8eee5654b7195dadaaf978caf.svg`
- `assets/figma/d6165cdb98a47b652bf30f95f422da3f5da4944a.svg`
- `assets/figma/d6c21929ad9b6e1d577e30d82a9b435bcbcd25bb.svg`
- `assets/figma/d7136ec337a7650f6af4c6a122ed3f2c8bcd4077.svg`
- `assets/figma/da2b40fd383fe2200ed9db62304be2fdf7e3f84e.svg`
- `assets/figma/dac62eddf0e8fabeec4df0f8dc8271835892e949.svg`
- `assets/figma/db17230c11df88131c508180f6f4ea0e322733d0.svg`
- `assets/figma/db4448e132aa8da23149ef6802b6a6fb8dee9160.png`
- `assets/figma/dbf6d058cf4252c4be9e93f3e00bb1b8935b2331.svg`
- `assets/figma/dd050f5b000abe5935db176a7aa2d3fa1ac5c4db.svg`
- `assets/figma/e17069e6b345d822634c985152e1c95ca6329a64.svg`
- `assets/figma/e1be21f341f38b1917299935d49ce420527ea01b.png`
- `assets/figma/e3259f5725d0f82b2c13fbc2834b5168d6ea6a0d.svg`
- `assets/figma/e42736a12e96eb5edebbf753f2aff54ddd168ffe.png`
- `assets/figma/e483f25f305df6c5ed19d796a4383a8c4d065a5e.svg`
- `assets/figma/e53e8aa05e85c7119ae54cc59d22181b86edf31c.png`
- `assets/figma/e7b085644f66e1da62f459b92332b88381906831.svg`
- `assets/figma/e92103a5556613d70a3fce1ce2bc70a941992334.svg`
- `assets/figma/eb4d586b94d795d6d8f8fe4a7df6a9d21eceebbd.png`
- `assets/figma/ebe0c86ed4fe8bd15ec2d460de04ed8a6eb11717.png`
- `assets/figma/f239d9134ddbcd6f7466e3e96940be26c1032de8.png`
- `assets/figma/f2cac708b01a10a5a8030bf1b245cfd475804695.png`
- `assets/figma/f55d3900198c5b54ed0f2ba1429b19d06aada8ff.svg`
- `assets/figma/f5c45bd9c73c997c9cc92a9b93e5866236fce89f.svg`
- `assets/figma/f5d9e1a00617a5865ee4d20329b34f5d7f91cc0b.svg`
- `assets/figma/f88729f12b979feb4e2c409022fdb62645fb2a70.svg`
- `assets/figma/f8b462b365b14ac3389b47a9aa0dc258c611eca8.png`
- `assets/figma/f98991ba1eb64adece1dbd602c85e810390959c4.png`
- `assets/figma/f9b903ac6c5eacad86609b9c535c722c637349f2.svg`
- `assets/figma/ffaf49af7683510d860f29cbc98f065245623239.svg`
- `assets/icons/advanced-analytics.svg`
- `assets/icons/buyer-group.svg`
- `assets/icons/centralized-data.svg`
- `assets/icons/company-finder.svg`
- `assets/icons/deal-management.svg`
- `assets/icons/doc-management.svg`
- `assets/icons/long-list-creation.svg`
- `assets/icons/qa-management.svg`
- `assets/icons/security-compliance.svg`
- `assets/images/dashboard-ai-qa.png`
- `assets/images/dashboard-deal-overview.webp`
- `assets/images/dashboard-main.png`
- `assets/images/dashboard-pipeline.png`
- `assets/images/dashboard-unified.png`
- `assets/images/key-advantage-mockup.png`
- `assets/images/workflow.png`
- `assets/logos/bloomberg-logo.png`
- `assets/logos/citi-logo.png`
- `assets/logos/deloitte-logo.png`
- `assets/logos/kpmg-logo.png`
- `assets/logos/morgan-stanley-logo.png`
- `assets/logos/sp-global-logo.png`
- `components/seamless-crm.svg`
- `components/security-compliance.svg`
- `docs/mpxtfdli-FIGMA-IMPLEMENTATION-BRIEF-v2.md`
- `docs/mpxtfdlj-figma-mcp-protocol-v2.md`
- `docs/mpy0nx5r-figma-mcp-protocol-v2.md`
- `docs/mpy0ohc4-figma-mcp-protocol-v2.md`
- `docs/navbar-spec.md`
- `figma-data/centralized-assets/avatar-icon.svg`
- `figma-data/centralized-assets/center-circle.svg`
- `figma-data/centralized-assets/checkmark-icon.svg`
- `figma-data/centralized-assets/database-icon.svg`
- `figma-data/centralized-assets/divider-line.svg`
- `figma-data/centralized-assets/feature-1.svg`
- `figma-data/centralized-assets/feature-2.svg`
- `figma-data/centralized-assets/feature-3.svg`
- `figma-data/centralized-assets/feature-4.svg`
- `figma-data/centralized-assets/left-arrow.svg`
- `figma-data/centralized-assets/private-icon.svg`
- `figma-data/centralized-assets/right-arrow.svg`
- `figma-data/centralized-assets/unified-globe.svg`
- `figma-data/centralized-flow-mcp.txt`
- `figma-data/design-context-full.txt`
- `figma-data/design-context-raw.json`
- `figma-data/design-context.txt`
- `figma-data/download-images.sh`
- `figma-data/how-it-works-assets/automation-icon.svg`
- `figma-data/how-it-works-assets/deal-icon-blue.svg`
- `figma-data/how-it-works-assets/deal-icon-brown.svg`
- `figma-data/how-it-works-assets/deal-icon-red.svg`
- `figma-data/how-it-works-assets/document-icon-blue.svg`
- `figma-data/how-it-works-assets/search-icon.svg`
- `figma-data/how-it-works-screenshot.png`
- `figma-data/images/00aee0eb9a953216622a4e0a0d33c2a36d6b7171.svg`
- `figma-data/images/01777e6c618d06519db6d13a5e68d77152aef2b3.svg`
- `figma-data/images/01dcc2882b4b4d3da8a1171daa4afac61ed33242.svg`
- `figma-data/images/02fafbed5a4db88e217b326453811264c175f972.svg`
- `figma-data/images/075026980f4c5609105512214f27af2057db6f7e.svg`
- `figma-data/images/0c1cb3c92862a850f4e64206aef9182820820c41.svg`
- `figma-data/images/0eb38a2ddf9990726ba1c7a1b5880f510c982644.png`
- `figma-data/images/0f6247d12799416e568bb808cd5daff5cd8072b8.png`
- `figma-data/images/10973467f94b76b8212da5be4b388454f7b0dcb9.svg`
- `figma-data/images/10c13ac1a228a365cb98a0064b1d5afbc84887b2.png`
- `figma-data/images/13cb6e9ed1c12933f1b852081940dc845e719587.svg`
- `figma-data/images/1553935576692afad4c28c8fbc1273519c23dd9d.png`
- `figma-data/images/16f59338315afce91b1a5ab1236b08f9fa43e09b.svg`
- `figma-data/images/1bd200cd3e0621d36d34b41c3137374022493589.png`
- `figma-data/images/1f9f8effde2eccb289ff28cbe6300d7352210203.svg`
- `figma-data/images/20e1e500c6539c23085677d7928fad9acafebda9.svg`
- `figma-data/images/21a5b54985b89fd2258d331e2aff5913b90499db.svg`
- `figma-data/images/220bc3b1cca14a86c9b6298749ba04b798b06ac3.svg`
- `figma-data/images/2607102b0c72920c87f3228d1be290d89cb741cb.png`
- `figma-data/images/2d0e0aae39845746e05255f7e46950ceaae401cc.png`
- `figma-data/images/2db7611239bb7eaee44c887f69e2e7fe90835cdb.svg`
- `figma-data/images/2e3c01f7c78fd5c13eed4614226fba58851ef420.svg`
- `figma-data/images/2e8d6685a05c98e09b42d791a63cdf726a018424.svg`
- `figma-data/images/2eaa0141a646592051bc1bca9dfcb16eac467f98.svg`
- `figma-data/images/2f5508f8585ba026cbaefa902dd56ede3ce823c2.svg`
- `figma-data/images/33be1fc3f95b8acd7a2908d53b17a14be3301da2.svg`
- `figma-data/images/346f926b8fbec2e79fc1b3709d35072d1b696ebb.png`
- `figma-data/images/35fb3e570229393a40b5631ab68408e64d6edd24.png`
- `figma-data/images/364412979b408782e95cac662a0a8690ae0f0a10.svg`
- `figma-data/images/389a7fcb89b57c9e93c0043597d846e6986eae4b.png`
- `figma-data/images/3cd103111c2f9e1c01f694742042f1e944802cbf.png`
- `figma-data/images/3de2056e514dd7aaf8ce065a999bccc96515b45a.png`
- `figma-data/images/40da1e79cc3fc967d0bb2609617e499b026a420c.svg`
- `figma-data/images/43c7fe3495b5829ec9de6b268e7b71bfa1eabdae.svg`
- `figma-data/images/49358a7f7192bb6fbee5329ae044a99d0b147446.svg`
- `figma-data/images/4935dfa074c4bcc4caec40f52192b5763307af3d.svg`
- `figma-data/images/4c689a7e48bfcc3055190a69a1a2b478a72a3eed.svg`
- `figma-data/images/4f003ed4a29f7634838caea244ca67e71bc3bb13.svg`
- `figma-data/images/51ef8f4a86931a451466ebf6b2ee9b51c44dd394.png`
- `figma-data/images/534d6c2d22a92b3ce8a8d3d5dd6e303bc1cc527d.svg`
- `figma-data/images/586ab8abb1fc0a40bd076cf581546ebe0b0a5372.svg`
- `figma-data/images/5e27f8f0cc978024040832bcdf86091912c6a0c6.svg`
- `figma-data/images/5e5497e8efe127e3d16e2131542c5fde48ffa564.png`
- `figma-data/images/5ecdbe3963a19987518249a04a3548f9e5d46eae.svg`
- `figma-data/images/619e4cd489076d0c2f5efcef368314bfff308ae5.svg`
- `figma-data/images/645afcb2bfb5961945b434e9f5fe915b6b8f3f48.svg`
- `figma-data/images/64dae2934cbc5d10c6373725deed285714eb08af.svg`
- `figma-data/images/64e60e0ab71799484666e24f5e735a2b3d1311b8.svg`
- `figma-data/images/652c66f4997542bede7ac72f34d6e26ac86fc447.png`
- `figma-data/images/67eb260f896fb52385d8a77d199101f392bd8a35.svg`
- `figma-data/images/6cd81accf697290e6e0897ca2f1d5483d34b9a17.png`
- `figma-data/images/6cea9a84a64cf689ff703767d9e5ad3edd697652.svg`
- `figma-data/images/6d23e20e0a94e6fc7f23d6c2d60e2b9bcafad20a.svg`
- `figma-data/images/6eab7b782cb003f881f034735209cb43a2b0cb57.svg`
- `figma-data/images/70038459812d97ce8264967aa663c6f5057eafee.png`
- `figma-data/images/72ba56042b5d5dd2abcccd6d095f405a4e223458.png`
- `figma-data/images/744e4f934bc64fdc56855bfc162a6af00d10bcfb.png`
- `figma-data/images/7640fa53b78f3429f4f7c0374d159bd4a66693ce.svg`
- `figma-data/images/76b8233fe172047808e84991c0492ed4ac2680f1.png`
- `figma-data/images/76eb72c3a1bef4e57c304bca9bc60b32ca2f3ca0.svg`
- `figma-data/images/7a741ff63816f728d196c21c18ec72dc696a2f33.svg`
- `figma-data/images/7e82f82e15c93c4506ee2e90f68e758b073432f1.png`
- `figma-data/images/7f9e11616f5323d383e7ed948deacaff9f323477.svg`
- `figma-data/images/80c3af49be56523ec51887eebb642cb835944a0d.svg`
- `figma-data/images/83f333b8a51159bbc1b840d4860a80a4705701af.svg`
- `figma-data/images/85b9ef8502927dae1ec99ecf2d10ac5411047d32.svg`
- `figma-data/images/85ff153e25477b6b93b0a18478614d1aaa0e51e7.png`
- `figma-data/images/87cd3ecdb66e739002620b0ef9b520e6013755f5.png`
- `figma-data/images/8a348b30b5ea94f67daa33af8b4c837b800d0dc4.svg`
- `figma-data/images/8b4b7dafbd78fff603d6566df68c4b03d8179b11.png`
- `figma-data/images/8ff6c4b975a5dcff7347bb8a72278be16a6a2e01.svg`
- `figma-data/images/930fc0fbc3124e38d70cb83d984d8d47658cf5a3.svg`
- `figma-data/images/95e951b2a450c2e8d036b5b7d003b8a1b39795aa.png`
- `figma-data/images/95fe30c729801b1a6303c7435194624ce33f8f51.png`
- `figma-data/images/960281453f803a6a9c03979a07b1d7fc65d92607.svg`
- `figma-data/images/966b1be0b9e0763ec67075fe9e82c13cbeffda54.png`
- `figma-data/images/9834067669fd7c52d65f9c6a5d3bb654048b9d51.svg`
- `figma-data/images/993c7e3a37f09c72c46f9df6de9995897b3798df.svg`
- `figma-data/images/9c765257b06be19c93b707de4ea32d3a9dedde91.svg`
- `figma-data/images/9dd67efbabbd6099058bc5258c32d6468cad89b6.svg`
- `figma-data/images/a1e120ed183bd3fe804a20b87cc79868308b48b3.png`
- `figma-data/images/a31df0da719fb569a853dc504de9abe9fb64b958.png`
- `figma-data/images/a5470b3e7a3d6f072eb861236234c8bda4b8f2d5.svg`
- `figma-data/images/a6f03734584298e3888dcea1a7cf448da6116eb2.svg`
- `figma-data/images/a7faf0dd484f0bf6ce0adb6ec08968c8d6b2dab5.svg`
- `figma-data/images/aaa56b243be0074faf90a7ba4950b241413656dd.svg`
- `figma-data/images/acc2d0d9300641887d9296979a695a709a4477b9.svg`
- `figma-data/images/b2cc592f86dc03638a783c695df156ea1b6fc3ea.svg`
- `figma-data/images/b2d98fe9240992f6ae1d7dd33be66e1a09d1c662.svg`
- `figma-data/images/b3e6f51bad969d6e6e6f30d7c0c9c3514e0a7c18.svg`
- `figma-data/images/b53ef57731f653cecae1671a3f32d3c992530c25.png`
- `figma-data/images/b9db56c78ee125a10c214b7b07f8afa28d9a08af.svg`
- `figma-data/images/ba517d70dac51441854467c4b73d3fbe4a43088b.png`
- `figma-data/images/baea502353cac1f2fe871205b8726706d0869c6a.png`
- `figma-data/images/bb558cacb5aa7fc7db10f6ead13a069be56a7b91.svg`
- `figma-data/images/bf40acd30b98abf3f63865be24ff6f6848ef4ca0.svg`
- `figma-data/images/c3a6cbdba2d937ea7da1f8d94d637aa6c378d5b4.svg`
- `figma-data/images/c6f7ab9be6e9f222dd85956256f2000e5ac0149c.svg`
- `figma-data/images/cb512e97ea65e5084bdb6017e666040d4fe594d3.svg`
- `figma-data/images/cd8134532c605ea56744efdc3aead81c8920241b.svg`
- `figma-data/images/d0db2ba4403651667b3d52638698ca1187cc0526.png`
- `figma-data/images/d25290bce5d0964ec942c4e03654a4799a5a12ff.png`
- `figma-data/images/d55830a6235d7ea8eee5654b7195dadaaf978caf.svg`
- `figma-data/images/d6165cdb98a47b652bf30f95f422da3f5da4944a.svg`
- `figma-data/images/d6c21929ad9b6e1d577e30d82a9b435bcbcd25bb.svg`
- `figma-data/images/d7136ec337a7650f6af4c6a122ed3f2c8bcd4077.svg`
- `figma-data/images/da2b40fd383fe2200ed9db62304be2fdf7e3f84e.svg`
- `figma-data/images/dac62eddf0e8fabeec4df0f8dc8271835892e949.svg`
- `figma-data/images/db17230c11df88131c508180f6f4ea0e322733d0.svg`
- `figma-data/images/db4448e132aa8da23149ef6802b6a6fb8dee9160.png`
- `figma-data/images/dbf6d058cf4252c4be9e93f3e00bb1b8935b2331.svg`
- `figma-data/images/dd050f5b000abe5935db176a7aa2d3fa1ac5c4db.svg`
- `figma-data/images/e17069e6b345d822634c985152e1c95ca6329a64.svg`
- `figma-data/images/e1be21f341f38b1917299935d49ce420527ea01b.png`
- `figma-data/images/e3259f5725d0f82b2c13fbc2834b5168d6ea6a0d.svg`
- `figma-data/images/e42736a12e96eb5edebbf753f2aff54ddd168ffe.png`
- `figma-data/images/e483f25f305df6c5ed19d796a4383a8c4d065a5e.svg`
- `figma-data/images/e53e8aa05e85c7119ae54cc59d22181b86edf31c.png`
- `figma-data/images/e7b085644f66e1da62f459b92332b88381906831.svg`
- `figma-data/images/e92103a5556613d70a3fce1ce2bc70a941992334.svg`
- `figma-data/images/eb4d586b94d795d6d8f8fe4a7df6a9d21eceebbd.png`
- `figma-data/images/ebe0c86ed4fe8bd15ec2d460de04ed8a6eb11717.png`
- `figma-data/images/f239d9134ddbcd6f7466e3e96940be26c1032de8.png`
- `figma-data/images/f2cac708b01a10a5a8030bf1b245cfd475804695.png`
- `figma-data/images/f55d3900198c5b54ed0f2ba1429b19d06aada8ff.svg`
- `figma-data/images/f5c45bd9c73c997c9cc92a9b93e5866236fce89f.svg`
- `figma-data/images/f5d9e1a00617a5865ee4d20329b34f5d7f91cc0b.svg`
- `figma-data/images/f88729f12b979feb4e2c409022fdb62645fb2a70.svg`
- `figma-data/images/f8b462b365b14ac3389b47a9aa0dc258c611eca8.png`
- `figma-data/images/f98991ba1eb64adece1dbd602c85e810390959c4.png`
- `figma-data/images/f9b903ac6c5eacad86609b9c535c722c637349f2.svg`
- `figma-data/images/ffaf49af7683510d860f29cbc98f065245623239.svg`
- `figma-data/mobile-layout-raw.txt`
- `figma-data/qa-assets/dot-green.svg`
- `figma-data/qa-assets/dot-red.svg`
- `figma-data/qa-assets/person-icon.svg`
- `figma-data/qa-assets/quote-icon.svg`
- `figma-data/qa-management-context.txt`
- `figma-data/qa-management-mcp.txt`
- `figma-data/screenshot-response.json`
- `figma-data/screenshot.png`
- `figma-data/service-overview-409-45-context.txt`
- `figma-data/service-overview-409-45-screenshot.png`
- `figma-data/service-overview-context-response.json`
- `figma-data/service-overview-screenshot-response.json`
- `figma-data/service-overview-sse.txt`
- `figma-data/software-detail-context-raw.txt`
- `figma-data/software-detail-screenshot.png`
- `figma-data/software-overview-context.json`
- `figma-data/software-overview-design.json`
- `figma-data/software-overview-screenshot.json`
- `figma-data/workflow-assets/avatar.svg`
- `figma-data/workflow-assets/folder-icon.svg`
- `figma-data/workflow-assets/line-divider.svg`
- `figma-data/workflow-assets/progress-15.svg`
- `figma-data/workflow-assets/progress-65.svg`
- `figma-data/workflow-assets/status-active.svg`
- `figma-data/workflow-assets/status-onhold.svg`
- `figma-data/workflow-assets/tasks.svg`
- `figma-data/workflow-efficiency-mcp.txt`
- `services-images/ai-automation.png`
- `services-images/business-development.png`
- `services-images/callout-mockup.png`
- `services-images/custom-development.png`
- `services-images/data-analytics.png`
- `services-images/ellipse-40.svg`
- `services-images/ellipse-44.svg`
- `services-images/ellipse-45.svg`
- `services-images/figma-reference-8084-409.png`
- `services-images/mask-group.svg`
- `services-images/seminars-workshops.png`
- `services-images/tech-assessment.png`

## Coding checklist for AI tools
1. Inspect `index.html` and `DESIGN-MANIFEST.json` first and identify reusable components before coding.
2. Implement each user-facing screen file as its own route/surface; keep launcher, landing, app, platform, and OS widget files separate.
3. Extract design tokens into the target stack: colors, type scale, spacing, radius, shadows, and motion.
4. Implement layout with real 2025–2026 responsive breakpoints, fluid type/spacing, and container-query-aware component behavior; test with no horizontal overflow.
5. Preserve interactive controls, hover/focus/pressed states, form behavior, validation, and copy actions where present.
6. Implement domain-specific in-app modules with real states; do not flatten them into generic cards.
7. Keep landing page, product screens, and OS widget/quick-access surfaces separate when present.
8. Confirm the production result visually matches the exported design before refactoring internals.
9. Reject implementation shortcuts that flatten the design into generic cards, generic gradients, placeholder stats, or framework-default typography.
10. If a detail is ambiguous, keep the exported HTML/CSS/JS behavior rather than inventing a new pattern.
