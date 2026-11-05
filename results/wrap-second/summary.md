# Headroom比較サマリ

費用はAPI換算の推定値です。サブスクリプションの実請求額ではありません。

総トークンは入力、キャッシュ書込、キャッシュ読取、出力の合計です。会話の再送分も毎回数えます。

| ケース | 試行 | テスト | 費用 | 総トークン | 入力 | キャッシュ書込 | キャッシュ読取 | 出力 | 初回読取 | ターン | Headroom圧縮前→後 | 共通/マージ済みファイル | 不足 | 余分 |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|---|
| case1 | A-1 | 成功 | 0.320 | 766641 | 2350 | 40604 | 714815 | 8872 | 11122 | 24 | - | 5/7 | web/tests/space-switcher.test.tsx, web/tests/user-menu.test.tsx | web/tests/sidebar-popup-positioning.test.tsx |
| case1 | A-2 | 成功 | 0.355 | 820411 | 2348 | 47920 | 761159 | 8984 | 11122 | 25 | - | 5/7 | web/tests/space-switcher.test.tsx, web/tests/user-menu.test.tsx | web/tests/fixed-sidebar-popups.test.tsx |
| case1 | A-3 | 成功 | 0.269 | 535552 | 2338 | 41799 | 485886 | 5529 | 11122 | 19 | - | 7/7 | - | - |
| case1 | B-1 | 成功 | 0.311 | 698716 | 40 | 43516 | 647651 | 7509 | 10779 | 20 | 430778→420149 | 7/7 | - | - |
| case1 | B-2 | 成功 | 0.271 | 521168 | 30 | 41971 | 473612 | 5555 | 10779 | 19 | 325048→308978 | 7/7 | - | - |
| case1 | B-3 | 成功 | 0.298 | 605621 | 32 | 46993 | 552742 | 5854 | 10779 | 21 | 367586→359841 | 7/7 | - | - |
| case2 | A-1 | 成功 | 0.304 | 742338 | 1491 | 40984 | 692755 | 7108 | 11122 | 24 | - | 7/14 | proto/api/v1/memo_service.proto, proto/gen/api/v1/apiv1connect/memo_service.connect.go, proto/gen/api/v1/memo_service_grpc.pb.go, proto/gen/openapi.yaml, store/db/mysql/memo_attachment.go, store/db/postgres/memo_attachment.go, web/src/types/proto/api/v1/memo_service_pb.ts | store/db/mysql/memo_delete_comments.go, store/db/postgres/memo_delete_comments.go, store/db/sqlite/memo_delete_comments.go |
| case2 | A-2 | 成功 | 0.251 | 499642 | 1483 | 34748 | 456759 | 6652 | 11122 | 20 | - | 7/14 | proto/api/v1/memo_service.proto, proto/gen/api/v1/apiv1connect/memo_service.connect.go, proto/gen/api/v1/memo_service_grpc.pb.go, proto/gen/openapi.yaml, store/db/mysql/memo_attachment.go, store/db/postgres/memo_attachment.go, web/src/types/proto/api/v1/memo_service_pb.ts | - |
| case2 | A-3 | 成功 | 0.272 | 670650 | 1489 | 37173 | 625936 | 6052 | 11122 | 19 | - | 2/14 | proto/api/v1/memo_service.proto, proto/gen/api/v1/apiv1connect/memo_service.connect.go, proto/gen/api/v1/memo_service_grpc.pb.go, proto/gen/openapi.yaml, server/api/v1/sse_service_test.go, store/db/mysql/memo_attachment.go, store/db/mysql/memo_delete_policy.go, store/db/postgres/memo_attachment.go, store/db/postgres/memo_delete_policy.go, store/db/sqlite/memo_delete_policy.go, store/memo_delete_policy.go, web/src/types/proto/api/v1/memo_service_pb.ts | store/db/mysql/space_delete.go, store/db/postgres/space_delete.go, store/db/sqlite/space_delete.go |
| case2 | B-1 | 成功 | 0.281 | 662563 | 40 | 39783 | 616504 | 6236 | 10779 | 20 | 410026→393986 | 6/14 | proto/api/v1/memo_service.proto, proto/gen/api/v1/apiv1connect/memo_service.connect.go, proto/gen/api/v1/memo_service_grpc.pb.go, proto/gen/openapi.yaml, store/db/mysql/memo_attachment.go, store/db/postgres/memo_attachment.go, store/memo_delete_policy.go, web/src/types/proto/api/v1/memo_service_pb.ts | - |
| case2 | B-2 | 成功 | 0.271 | 472645 | 28 | 42525 | 424056 | 6036 | 10779 | 17 | 288295→281519 | 7/14 | proto/api/v1/memo_service.proto, proto/gen/api/v1/apiv1connect/memo_service.connect.go, proto/gen/api/v1/memo_service_grpc.pb.go, proto/gen/openapi.yaml, store/db/mysql/memo_attachment.go, store/db/postgres/memo_attachment.go, web/src/types/proto/api/v1/memo_service_pb.ts | - |
| case2 | B-3 | 成功 | 0.287 | 707395 | 44 | 36906 | 662978 | 7467 | 10779 | 25 | 439764→423393 | 7/14 | proto/api/v1/memo_service.proto, proto/gen/api/v1/apiv1connect/memo_service.connect.go, proto/gen/api/v1/memo_service_grpc.pb.go, proto/gen/openapi.yaml, store/db/mysql/memo_attachment.go, store/db/postgres/memo_attachment.go, web/src/types/proto/api/v1/memo_service_pb.ts | - |

## AとBの差（複数回なら中央値）

| ケース | テスト成功 A | テスト成功 B | A総トークン | B総トークン | Bの増減 | A費用 | B費用 | Bの増減 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| case1 | 3/3 | 3/3 | 766641 | 605621 | -161020 (-21.0%) | 0.320 | 0.298 | -6.8% |
| case2 | 3/3 | 3/3 | 670650 | 662563 | -8087 (-1.2%) | 0.272 | 0.281 | +3.4% |

## ツール呼び出し

| ケース | 試行 | Serena | headroom_retrieve | Read | Edit | Bash |
|---|---|---:|---:|---:|---:|---:|
| case1 | A-1 | 0 | 0 | 4 | 0 | 16 |
| case1 | A-2 | 0 | 0 | 5 | 0 | 16 |
| case1 | A-3 | 0 | 0 | 6 | 0 | 10 |
| case1 | B-1 | 0 | 0 | 3 | 0 | 15 |
| case1 | B-2 | 0 | 0 | 7 | 0 | 8 |
| case1 | B-3 | 0 | 0 | 7 | 0 | 10 |
| case2 | A-1 | 0 | 0 | 7 | 0 | 12 |
| case2 | A-2 | 0 | 0 | 8 | 0 | 6 |
| case2 | A-3 | 0 | 0 | 3 | 0 | 12 |
| case2 | B-1 | 0 | 0 | 6 | 0 | 9 |
| case2 | B-2 | 0 | 0 | 7 | 0 | 4 |
| case2 | B-3 | 0 | 0 | 6 | 1 | 12 |
