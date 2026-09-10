# akashic-external-protocol

[Akashic Engine](https://akashic-games.github.io/) のコンテンツ拡張と、それを受け入れるコンテンツ実行基盤との間の**通信仕様**を定めるリポジトリ。

仕様だけを持ち、npm には公開しない。実装は拡張ごとの別リポジトリにある。

- 仕様本体 → **[PROTOCOL.md](./PROTOCOL.md)**
- 名前空間 → `:multi-indiegame`

## これは何を解く仕様か

Akashic のコンテンツ拡張は `g.game.external` にオブジェクトが生えることで機能を受け取る。呼び出し（コンテンツ → 実行基盤）はそれで足りるが、 **結果の通知（実行基盤 → 全インスタンス）** には口がない。

マルチプレイのコンテンツでは、通知が全インスタンスに同一 tick で同一内容で届かないとゲーム状態がずれる。この仕様は、実行基盤が playlog へ MessageEvent を注入することでその通知経路を定め、複数の拡張がひとつの名前空間を共有できるようにする。

## 実装されている拡張

| type                                  | リポジトリ                                                                  | 内容                           |
| ------------------------------------- | --------------------------------------------------------------------------- | ------------------------------ |
| `@multi-indiegame/akashic-player-ban` | [akashic-player-ban](https://github.com/multi-indiegame/akashic-player-ban) | ゲーム進行からのプレイヤー追放 |

新しい拡張を足すときは、PROTOCOL.md の「拡張レジストリ」に 1 行足す。

## ライセンス

MIT
