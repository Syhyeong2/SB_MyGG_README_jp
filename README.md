# SB_MyGG

🌐 **サイトURL**  
[MyGG](https://mygg.lol)

## 📌 プロジェクト紹介
**MyGG** は、*League of Legends* の戦績検索および統計分析を提供するWebサービスです。  
Riot Games APIを活用し、ゲームデータを取得・提供します。

## 🛠 技術スタック
### **Backend**
- Java 17
- Spring Boot 3.x
- JPA / Hibernate
- MySQL
- MongoDB

### **Frontend**
- React
- Styled-components
- Zustand
- React-router-dom

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

-  **バックエンド(10%)**
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


## 📝 APIドキュメント
本プロジェクトでは、Riot Gamesが提供する **Data Dragon API** を使用しています。  
[API ドキュメントはこちら](https://developer.riotgames.com/docs/lol)

## 📜 ライセンス
このプロジェクトは **MITライセンス** に基づいています。

## 🤝 感謝
本プロジェクトはRiot GamesのAPIを利用しています。  
*League of Legends* はRiot Gamesの登録商標です。
