# N1ブロックチェーン概要

## N1とは

N1は、アプリケーションと水平スケーラビリティをサポートするために一から設計されたレイヤー1ブロックチェーンです。Ethereumのロードマップと同様の目標を持ちながら、従来の制約がありません。N1の重要な特徴は、ほとんどの場合でコンセンサスを避け、バリデータの数が増えるほどスケールが向上することです。すべてのアプリケーションのトランザクションを順序付けるためにコンセンサスを使用する代わりに、トランザクションはデフォルトで順序付けされておらず非同期です。コンセンサスはアプリ間のブリッジングにのみ導入されます。

## 主な特徴

### 水平スケーラビリティ
- シャーディングされたデータ可用性を内蔵
- 各アプリはブリッジング時を除き、他のアプリから独立して動作
- バリデータの数に応じてパフォーマンスが向上

### ネイティブな流動性
- SolanaやEthereumへのネイティブブリッジにより、トランザクションと資産の高い流動性とセキュリティを提供

### 仮想マシン非依存
- 実行環境に制約を設けない設計
- 検証手順が定義できるものなら何でも実行可能

### 輻輳（混雑）なし
- ボトルネックはデータ可用性のみ
- 各アプリは独自の環境で動作するため、状態の輻輳なし
- ガス最適化や状態肥大の問題がない

## 開発者にとってのメリット

- **共有コンピュートの問題解決**: 各アプリが専用環境で実行され、垂直スケーリングと状態競合の排除が可能
- **コンピュート制限の解消**: アプリごとにノードを追加することで実質無制限の水平スケールが可能
- **表現力と反復速度の向上**: TypeScriptなど一般的な言語を使用可能で、ブロックチェーン特有の概念学習の必要性が低下

## 最適なアプリケーション

N1は以下の2種類のアプリケーションに特に適しています：

1. **TypeScriptなど非Solidity言語で書かれたアプリ**
2. **計算集約型または低レイテンシが必要なアプリ**

## 技術アーキテクチャ

### 分離されたレイヤー
- **決済レイヤー**: プログラムを実行せず、軽量で効率的。データ可用性と証明検証を通じてセキュリティを提供
- **実行レイヤー**: 各アプリが専用環境で実行され、垂直スケーリングと完全なカスタマイズが可能

### 専用コンピュート環境（DCE）
- 各プログラムは分離された環境で実行
- アプリごとに垂直スケーリングとサーバーの計算リソースをフル活用
- 既存のツールを使用した簡単なデプロイが可能

### 瞬時通信
- プログラム間はポイントツーポイントの順序付けられたチャネルで通信
- メッセージは到着次第即座に実行される
- 他のブロックチェーンのブリッジングと異なり、検証待ちが不要

### SNARKフラウドプルーフ
- 計算の短い証明を使用
- 最終的にはSNARKによる完全検証モデルを目指すが、現在は最適化モデルを採用
- 非対話型フラウドプルーフにより、長い引き出し期間が不要

## サポートされる開発言語

- **TypeScript**: NTS (N1 TypeScript) 開発環境
- **Rust**: Wasmを使用した実行環境
- **Solidity**: EthereumのRPCインターフェースを提供

## 現在のステータス

N1は現在、**クローズドアーリーアクセス**段階にあり、選ばれた開発者のみが利用可能です。開発への参加に興味がある場合は、Priority Accessプログラムにサインアップすることをお勧めします。

## TypeScriptによるスマートコントラクト開発

N1ブロックチェーンは、TypeScriptを使用してスマートコントラクトを開発することをサポートしています。これにより、開発者は一般的なプログラミング言語であるTypeScriptを使用して、ブロックチェーンアプリケーションを構築できます。

### 特徴

- **親しみやすさ**: TypeScriptはJavaScriptのスーパーセットであり、多くの開発者にとって馴染みのある言語です。これにより、ブロックチェーン開発の敷居が下がります。
- **型安全性**: TypeScriptは静的型付けをサポートしており、コードの安全性と可読性が向上します。これにより、バグを早期に発見しやすくなります。
- **豊富なエコシステム**: TypeScriptは多くのライブラリやフレームワークと互換性があり、開発者は既存のツールを活用して効率的に開発できます。

---

# N1 Blockchain Overview

## What is N1?

N1 is a Layer 1 blockchain designed from the ground up to support applications and horizontal scalability. While it shares similar goals with Ethereum's roadmap, it does not have the traditional constraints. A key feature of N1 is that it avoids consensus in most cases, allowing scalability to improve as the number of validators increases. Instead of using consensus to order transactions for all applications, transactions are by default unordered and asynchronous. Consensus is only introduced for bridging between applications.

## Key Features

### Horizontal Scalability
- Built-in sharded data availability
- Each application operates independently from others, except during bridging
- Performance improves with the number of validators

### Native Liquidity
- Native bridges to Solana and Ethereum provide high liquidity and security for transactions and assets

### Virtual Machine Independence
- Designed without constraints on execution environments
- Anything that can define verification procedures can be executed

### No Congestion
- Bottlenecks are limited to data availability
- Each application operates in its own environment, avoiding state congestion
- No issues with gas optimization or state bloat

## Benefits for Developers

- **Solving Shared Compute Issues**: Each application runs in a dedicated environment, allowing for vertical scaling and elimination of state conflicts
- **Eliminating Compute Limits**: Adding nodes per application allows for virtually unlimited horizontal scaling
- **Increased Expressiveness and Iteration Speed**: Common languages like TypeScript can be used, reducing the need to learn blockchain-specific concepts

## Optimal Applications

N1 is particularly suited for the following two types of applications:

1. **Applications written in non-Solidity languages like TypeScript**
2. **Computationally intensive or low-latency applications**

## Technical Architecture

### Separated Layers
- **Settlement Layer**: Lightweight and efficient, providing security through data availability and proof verification without executing programs
- **Execution Layer**: Each application runs in a dedicated environment, allowing for vertical scaling and complete customization

### Dedicated Compute Environment (DCE)
- Each program runs in a separated environment
- Full utilization of server compute resources for vertical scaling per application
- Easy deployment using existing tools

### Instant Communication
- Programs communicate over point-to-point ordered channels
- Messages are executed immediately upon arrival
- Unlike bridging on other blockchains, no waiting for verification is required

### SNARK Fraud Proof
- Uses short proofs of computation
- Aims for a complete verification model using SNARKs in the long run, but currently adopts an optimized model
- Non-interactive fraud proofs eliminate the need for long withdrawal periods

## Supported Development Languages

- **TypeScript**: NTS (N1 TypeScript) development environment
- **Rust**: Execution environment using Wasm
- **Solidity**: Provides Ethereum's RPC interface

## Current Status

N1 is currently in a **closed early access** phase, available only to selected developers. If you are interested in participating in development, we recommend signing up for the Priority Access program.

## Smart Contract Development with TypeScript

The N1 blockchain supports the development of smart contracts using TypeScript. This allows developers to build blockchain applications using a widely known programming language.

### Features

- **Familiarity**: TypeScript is a superset of JavaScript, making it a familiar language for many developers. This lowers the barrier to entry for blockchain development.
- **Type Safety**: TypeScript supports static typing, enhancing code safety and readability. This makes it easier to catch bugs early in the development process.
- **Rich Ecosystem**: TypeScript is compatible with many libraries and frameworks, allowing developers to leverage existing tools for efficient development.
