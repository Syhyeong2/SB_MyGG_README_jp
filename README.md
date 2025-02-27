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
  - **DB、API設計**
- **DB、API設計**
  - **MongoDB導入推進**

## 🎯 主な機能
- ユーザ戦績検索
- ユーザ戦績統計
- ゲームキャラクター情報検索
- ゲームアイテム情報検索


## 🚀 開発のポイント & 工夫した点




## 📝 APIドキュメント
本プロジェクトでは、Riot Gamesが提供する **Data Dragon API** を使用しています。  
[API ドキュメントはこちら](https://developer.riotgames.com/docs/lol)

## 📜 ライセンス
このプロジェクトは **MITライセンス** に基づいています。

## 🤝 感謝
本プロジェクトはRiot GamesのAPIを利用しています。  
*League of Legends* はRiot Gamesの登録商標です。
