# SB_MyGG

🌐 **サイトURL**  
[MyGG](https://mygg.lol)

## 📌 プロジェクト紹介
**MyGG** は、*League of Legends* の戦績検索および統計分析を提供するWebサービスです。  
Riot Games APIを活用し、ゲームデータを取得・提供します。

## 🛠 技術スタック
### Front-End  
![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=white) ![Styled-components](https://img.shields.io/badge/Styled--components-DB7093?style=for-the-badge&logo=styled-components&logoColor=white) ![Zustand](https://img.shields.io/badge/Zustand-000000?style=for-the-badge&logo=zustand&logoColor=white) ![React Router](https://img.shields.io/badge/React--Router--DOM-CA4245?style=for-the-badge&logo=react-router&logoColor=white)

### Back-End  
![Java](https://img.shields.io/badge/Java%2017-007396?style=for-the-badge&logo=openjdk&logoColor=white) ![Spring Boot](https://img.shields.io/badge/Spring%20Boot%203.x-6DB33F?style=for-the-badge&logo=springboot&logoColor=white) ![JPA](https://img.shields.io/badge/JPA%20/%20Hibernate-59666C?style=for-the-badge&logo=hibernate&logoColor=white)

### Database  
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white) ![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)

## 👥 担当範囲
- **フロントエンド (100%)**  
  - **プロジェクト全体のアーキテクチャ設計**  
    - フロントエンドのディレクトリ構成の策定と設計指針の確立  
    - 再利用性と拡張性を考慮したコンポーネント設計  
  - **API通信構造の設計と最適化**  
    - バックエンドとのインターフェース設計（エンドポイント定義、リクエスト/レスポンス仕様の整備）  
    - 非同期データ取得の最適化（ローディング管理）  
  - **ページおよびコンポーネントの開発**  
    - UI/UXを考慮したページレイアウトと動的コンポーネントの実装  
    - 状態管理（Zustand）の適用とパフォーマンス最適化  
  - **パフォーマンス最適化とユーザーエクスペリエンス向上**  
    - Lazy Loading（コード分割）を活用し、初回ロード時間の短縮  
    - useDebounce カスタムフックを活用した検索API通信の最適化

- **バックエンド(10%)**
  -  DB、API設計
  -  MongoDB導入推進

## 🎯 主な機能
- ユーザ戦績検索
- ユーザ戦績統計
- ゲームキャラクター情報検索
- ゲームアイテム情報検索


## 🚀 開発のポイント & 工夫した点

### ルーティングベースのレイジーローディング
React Router DOM のルートごとに `lazy` を用いたレイジーローディングを実装し、初回ビルド時のバンドルサイズを約 **100KB 削減** しました。
この最適化により、**FCP（First Contentful Paint）および LCP（Largest Contentful Paint）のスコアが 5〜10 ポイント程度向上** しました。

### ユーザーのニックネーム検索モーダルコンポーネント
検索パフォーマンスを向上させるために、`useDebounce` を利用した **カスタムフック** を作成しました。

通常、`onChange` イベントで検索 API をトリガーすると、ユーザーが入力するたびに API リクエストが発生し、無駄な通信が増加してしまいます。

これを防ぐために、一定時間内に連続して発生した入力イベントのうち、**最後のイベントのみ API を実行する仕組み** を導入し、無駄なリクエストを削減しました。

### 画像ホバー時のツールチップ表示コンポーネント
ゲーム内のキャラクターやアイテム画像にホバーすると、情報を表示する **ツールチップコンポーネント** を実装しました。

- `getBoundingClientRect()` を活用し、ホバー位置に応じて適切なツールチップの表示位置を計算。
- 画面上部では **下向きに表示**、画面下部では **上向きに表示** することで、レイアウト崩れを防止。
- イメージのローディング管理を取り入れ、スムーズな UX を実現。

### ゲーム API リクエストのグローバル状態管理
ゲーム内のキャラクターやアイテム情報は、サイト内の **複数のページで共通して使用** されるため、**グローバルステートで一元管理** しました。

- サイトのビルド時に初期データをロードし、グローバルステートに保存。
- **不要な再レンダリングを抑え、データフェッチの回数を最適化。**
- 一度取得したデータをメモリ上に保持し、全体的なパフォーマンスを向上。

これらの最適化により、**アプリケーションの処理効率が向上し、より快適なユーザー体験を実現** しました。

### Riot APIのマッチデータ保存における NoSQL 導入

Riot APIが提供するマッチの戦績データは約2,000行を超える巨大なJSON形式のデータであるため、MySQLなどのRDBで扱う場合、テーブル設計やデータの集計処理が複雑化する課題がありました。

そこで、スキーマレスで柔軟にJSONを扱えるMongoDBを導入しました。MongoDBを利用することでカラム設計の負担がなくなり、データ保存の効率化および集計処理（Aggregation Pipeline）による統計・分析も容易になりました。

また、本プロジェクトのデータは更新が不要で、Riot APIの構造をそのまま利用できるため、MongoDBが最適だと判断しました。

これらの経験を通して、プロジェクトに適したデータベースの選定方法についても理解を深めることができました。

## 📝 APIドキュメント
本プロジェクトでは、Riot Gamesが提供する **Data Dragon API** を使用しています。  
[API ドキュメントはこちら](https://developer.riotgames.com/docs/lol)

## 📜 ライセンス
このプロジェクトは **MITライセンス** に基づいています。

## 🤝 感謝
本プロジェクトはRiot GamesのAPIを利用しています。  
*League of Legends* はRiot Gamesの登録商標です。
