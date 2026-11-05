# Headroom比較サマリ

費用はAPI換算の推定値です。サブスクリプションの実請求額ではありません。

総トークンは入力、キャッシュ書込、キャッシュ読取、出力の合計です。会話の再送分も毎回数えます。

| ケース | 試行 | テスト | 費用 | 総トークン | 入力 | キャッシュ書込 | キャッシュ読取 | 出力 | 初回読取 | ターン | Headroom圧縮前→後 | 共通/マージ済みファイル | 不足 | 余分 |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|---|
| case1 | A-1 | 成功 | 0.320 | 766641 | 2350 | 40604 | 714815 | 8872 | 11122 | 24 | - | 5/7 | web/tests/space-switcher.test.tsx, web/tests/user-menu.test.tsx | web/tests/sidebar-popup-positioning.test.tsx |
| case1 | B-1 | 成功 | 0.293 | 603068 | 32 | 46282 | 551175 | 5579 | 12117 | 14 | 370038→363008 | 7/7 | - | - |
| case2 | A-1 | 成功 | 0.304 | 742338 | 1491 | 40984 | 692755 | 7108 | 11122 | 24 | - | 7/14 | proto/api/v1/memo_service.proto, proto/gen/api/v1/apiv1connect/memo_service.connect.go, proto/gen/api/v1/memo_service_grpc.pb.go, proto/gen/openapi.yaml, store/db/mysql/memo_attachment.go, store/db/postgres/memo_attachment.go, web/src/types/proto/api/v1/memo_service_pb.ts | store/db/mysql/memo_delete_comments.go, store/db/postgres/memo_delete_comments.go, store/db/sqlite/memo_delete_comments.go |
| case2 | B-1 | 成功 | 0.215 | 477223 | 34 | 29934 | 441897 | 5358 | 12117 | 15 | 300649→291733 | 6/14 | proto/api/v1/memo_service.proto, proto/gen/api/v1/apiv1connect/memo_service.connect.go, proto/gen/api/v1/memo_service_grpc.pb.go, proto/gen/openapi.yaml, server/api/v1/sse_service_test.go, store/db/mysql/memo_attachment.go, store/db/postgres/memo_attachment.go, web/src/types/proto/api/v1/memo_service_pb.ts | - |

## AとBの差（複数回なら中央値）

| ケース | テスト成功 A | テスト成功 B | A総トークン | B総トークン | Bの増減 | A費用 | B費用 | Bの増減 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| case1 | 1/1 | 1/1 | 766641 | 603068 | -163573 (-21.3%) | 0.320 | 0.293 | -8.6% |
| case2 | 1/1 | 1/1 | 742338 | 477223 | -265115 (-35.7%) | 0.304 | 0.215 | -29.2% |

## ツール呼び出し

| ケース | 試行 | Serena | headroom_retrieve | Read | Edit | Bash |
|---|---|---:|---:|---:|---:|---:|
| case1 | A-1 | 0 | 0 | 4 | 0 | 16 |
| case1 | B-1 | 0 | 0 | 0 | 0 | 13 |
| case2 | A-1 | 0 | 0 | 7 | 0 | 12 |
| case2 | B-1 | 0 | 0 | 0 | 0 | 14 |
