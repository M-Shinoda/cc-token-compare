# Headroom比較サマリ

費用はAPI換算の推定値です。サブスクリプションの実請求額ではありません。

総トークンは入力、キャッシュ書込、キャッシュ読取、出力の合計です。会話の再送分も毎回数えます。

| ケース | 試行 | テスト | 費用 | 総トークン | 入力 | キャッシュ書込 | キャッシュ読取 | 出力 | 初回読取 | ターン | Headroom圧縮前→後 | 共通/マージ済みファイル | 不足 | 余分 |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|---|
| case2 | A-1 | 成功 | 0.355 | 1001841 | 1499 | 46220 | 946594 | 7528 | 10637 | 29 | - | 6/14 | proto/api/v1/memo_service.proto, proto/gen/api/v1/apiv1connect/memo_service.connect.go, proto/gen/api/v1/memo_service_grpc.pb.go, proto/gen/openapi.yaml, server/api/v1/sse_service_test.go, store/db/mysql/memo_attachment.go, store/db/postgres/memo_attachment.go, web/src/types/proto/api/v1/memo_service_pb.ts | store/db/mysql/memo_comment_tree.go, store/db/postgres/memo_comment_tree.go, store/db/sqlite/memo_comment_tree.go |
| case2 | B-1 | 成功 | 0.325 | 566611 | 34 | 53233 | 507022 | 6322 | 0 | 17 | 350285→342389 | 7/14 | proto/api/v1/memo_service.proto, proto/gen/api/v1/apiv1connect/memo_service.connect.go, proto/gen/api/v1/memo_service_grpc.pb.go, proto/gen/openapi.yaml, store/db/mysql/memo_attachment.go, store/db/postgres/memo_attachment.go, web/src/types/proto/api/v1/memo_service_pb.ts | - |

## AとBの差（複数回なら中央値）

| ケース | テスト成功 A | テスト成功 B | A総トークン | B総トークン | Bの増減 | A費用 | B費用 | Bの増減 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| case2 | 1/1 | 1/1 | 1001841 | 566611 | -435230 (-43.4%) | 0.355 | 0.325 | -8.5% |
