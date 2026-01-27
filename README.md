# 設計・デザイン検討資料 / Engineering Design Notes

[日本語版はこちら](#japanese) | [English README](#english)

<a name="japanese"></a>

# 設計・デザイン検討資料
---

## 概要
このリポジトリは、実際の開発プロジェクトで作成された設計メモと図（ダイアグラム）をまとめたものです。複雑なビジネスロジックやシステムアーキテクチャを、視覚的なモデリングと反復的な設計探求を通じて整理するためのリファレンスとして機能します。

**目的:**
- 図を通じて複雑なドメインルールとシステムアーキテクチャを明確化する
- 設計判断を検証し、トレードオフを探る
- 不確実または複雑性の高い状況での実装をサポートする
- 技術的な詳細について共通の理解を形成する

---

## 主な成果物（画像ファイル）
- [AIコーディング活用](https://github.com/y-ikenuma/engineering-design-notes/blob/main/architecture/AI-coding/AIコーディング活用.png)
- [シャーディングとスループット](https://github.com/y-ikenuma/engineering-design-notes/blob/main/architecture/scalability/sharding-and-throughput.png)
- [Lambdaストリームアーキテクチャ](https://github.com/y-ikenuma/engineering-design-notes/blob/main/architecture/streaming/lambda-stream-architecture.png)
- [ストリームオプションの検討](https://github.com/y-ikenuma/engineering-design-notes/blob/main/architecture/streaming/stream-options-notes.png)
- [勤怠・労働時間計算](https://github.com/y-ikenuma/engineering-design-notes/blob/main/domain/attendance/attendance-worktime-calculation.png)

---

## リポジトリ構造
このリポジトリは、ドメイン理解からシステムアーキテクチャへと移行する**設計視点**によって意図的に構成されています。

### [`domain/`](domain/README.md) - ドメイン設計
ビジネスルール、ドメインの概念、複雑な計算ロジックに焦点を当てています。
- **対象読者:** ビジネス要件やドメイン固有のルールを理解する必要があるすべての人
- **例:** 労働規制に基づく労働時間の計算、勤怠ポリシー
- **目標:** ドメインロジックを外部化することで、実装中の認知負荷を軽減する

### [`architecture/`](architecture/README.md) - システムアーキテクチャ
システム設計、スケーラビリティ、ストリームベースの処理パターンに焦点を当てています。
- **対象読者:** システム設計者、アーキテクチャの意思決定を行うエンジニア
- **例:** ストリーム処理アーキテクチャ、スループット最適化、分散システム設計
- **目標:** 実装前にトレードオフ、制約、実現可能性について検討する

---

## クイックナビゲーション
| セクション | 説明 | 主なコンテンツ |
|---|---|---|
| **スケーラビリティ** | スループットとシャーディング戦略 | [`sharding-and-throughput.png`](architecture/scalability/sharding-and-throughput.png), [`company-sharding-strategy.md`](architecture/scalability/company-sharding-strategy.md) |
| **ストリーミング** | イベント駆動およびストリーム処理アーキテクチャ | [`lambda-stream-architecture.png`](architecture/streaming/lambda-stream-architecture.png), [`stream-options-notes.png`](architecture/streaming/stream-options-notes.png) |
| **フロントエンド** | 複雑なDOM/iframe間のインタラクションパターン | [`dom-overlay-iframe-interaction.md`](architecture/frontend/dom-overlay-iframe-interaction.md) |
| **勤怠** | 労働時間計算とビジネスルール | [`attendance-worktime-calculation.png`](domain/attendance/attendance-worktime-calculation.png) |

---

## 設計パターンと実装例
このリポジトリには、実際の世界での設計パターンと実装戦略が含まれています。

### ドメイン設計
- **勤怠・給与ドメイン**: 複雑な労働法に基づく計算ロジック
  - 複数レイヤーの労働時間ルール（通常勤務、時間外、深夜シフトなど）
  - 税金および控除の計算パターン

### アーキテクチャとスケーラビリティ
- **シャーディング戦略**: VIP企業専用シャードとハッシュベース分散を組み合わせたハイブリッドアプローチ
  - シャードごとのリソース割り当て（Aurora Serverless v2、0.5-128 ACUスケーリング）
  - 企業分離のための実装上の考慮事項

### フロントエンド実装パターン
- **iframe同期によるDOMオーバーレイ**:
  - コンソール調査によるフレームワークのプロパティのリバースエンジニアリング
  - iframe境界を越えたスクロール、行の高さ、クリックイベントの同期
  - リファレンスが限られたフレームワーク向けの実践的な解決策

### ストリーム処理
- **ラムダアーキテクチャ**: 高スループットシステム向けのイベント駆動処理パターン

---

## ワークフロー
すべての図は、編集可能な`.drawio`形式で管理されています。
- 設計の意図と理論的根拠を保持する
- 反復と改良を可能にする
- 協力的な設計議論をサポートする

`.drawio`ファイルが更新されると、**GitHub Actions経由でPNGエクスポートが自動的に生成**され、リポジトリで図を簡単に表示できます。

---

## 注記
- すべての資料は、機密情報や専有情報を避けるために一般化および抽出されています
- 図は思考ツールとして機能し、必ずしも最終仕様ではありません
- 焦点は、規範的なドキュメントを作成するのではなく、理解を明確にすることです

<br><hr><br>

<a name="english"></a>

# Engineering Design Notes
---

## 📋 Overview
This repository contains design notes and diagrams created during real-world development projects. It serves as a reference for structuring complex business logic and system architecture through visual modeling and iterative design exploration.

**Purpose:**
- Clarify complex domain rules and system architecture through diagrams
- Validate design decisions and explore trade-offs
- Support implementation in uncertain or high-complexity situations
- Create a shared understanding across technical details

---

## 🏗️ Repository Structure
This repository is intentionally organized by **design perspective**, moving from domain understanding to system architecture:

### [`domain/`](domain/README.md) - Domain Design
Focuses on business rules, domain concepts, and complex calculation logic.
- **Audience:** Anyone needing to understand business requirements and domain-specific rules
- **Examples:** Work-time calculation based on labor regulations, attendance policies
- **Goal:** Reduce cognitive load during implementation by externalizing domain logic

### [`architecture/`](architecture/README.md) - System Architecture
Focuses on system design, scalability, and stream-based processing patterns.
- **Audience:** System designers, engineers making architectural decisions
- **Examples:** Stream processing architectures, throughput optimization, distributed system design
- **Goal:** Reason about trade-offs, constraints, and feasibility before implementation

---

## 📊 Quick Navigation
| Section | Description | Key Content |
|---------|-------------|---------------|
| **Scalability** | Throughput and sharding strategies | [`sharding-and-throughput.png`](architecture/scalability/sharding-and-throughput.png), [`company-sharding-strategy.md`](architecture/scalability/company-sharding-strategy.md) |
| **Streaming** | Event-driven and stream processing architectures | [`lambda-stream-architecture.png`](architecture/streaming/lambda-stream-architecture.png), [`stream-options-notes.png`](architecture/streaming/stream-options-notes.png) |
| **Frontend** | Complex DOM/iframe interaction patterns | [`dom-overlay-iframe-interaction.md`](architecture/frontend/dom-overlay-iframe-interaction.md) |
| **Attendance** | Work-time calculation and business rules | [`attendance-worktime-calculation.png`](domain/attendance/attendance-worktime-calculation.png) |

---

## 📚 Design Patterns & Implementation Examples
This repository includes real-world design patterns and implementation strategies:

### Domain Design
- **Attendance / Payroll Domain**: Complex labor law-based calculation logic
  - Multi-layered work-time rules (regular time, overtime, night shift, etc.)
  - Tax and deduction calculation patterns

### Architecture & Scalability
- **Sharding Strategy**: Hybrid approach with VIP-company dedicated shards and hash-based distribution
  - Resource allocation per shard (Aurora Serverless v2 with 0.5-128 ACU scaling)
  - Implementation considerations for company isolation

### Frontend Implementation Patterns
- **DOM Overlay with iframe Synchronization**: 
  - Reverse-engineered framework properties through console inspection
  - Scroll, line-height, and click-event synchronization across iframe boundaries
  - Practical solution for limited-reference frameworks

### Stream Processing
- **Lambda Architecture**: Event-driven processing patterns for high-throughput systems

---

## 🔄 Workflow
All diagrams are managed in editable `.drawio` format to:
- Preserve design intent and reasoning
- Allow iteration and refinement
- Support collaborative design discussions

**PNG exports are automatically generated** when `.drawio` files are updated via GitHub Actions, making diagrams easily viewable in the repository.

---

## 📝 Notes
- All materials are generalized and extracted to avoid confidential or proprietary information
- Diagrams serve as thinking tools, not necessarily as final specifications
- The focus is on clarifying understanding rather than creating prescriptive documentation