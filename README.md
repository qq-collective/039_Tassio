# 🏺 #039 TASSIO

> *Transcribe & Archive System for Strategic Information Organization*
> 「耳から入れて、頭で整理する。」

---

## 概要

ポッドキャストのエピソードを理解するための支援ツールです。

音声ファイルのリアルタイム文字起こしと、Apple PodcastページのHTMファイルや目次テキストからの解析、2つのモードでClaude APIが要約・概念図・専門用語解説を生成します。

「耳と頭がついていかない」というモヤモヤを、TASSIOが結晶化します。

---

## 2つのモード

### MODE I — 目次・テキスト解析
音声ファイルがなくても使えます。Apple PodcastページをHTMとして保存してドロップするか、エピソードの目次・説明文をペーストするだけで解析が始まります。

**できること**
- エピソード目次の整理（タイムスタンプ付き）
- 内容の要約・まとめ（400〜600文字）
- 概念図の自動生成（Mermaid記法）
- 専門用語の解説（最大8語）

### MODE II — 音声文字起こし
音声ファイルをアップロードして再生しながら、ブラウザ内蔵のWeb Speech APIでリアルタイムに文字起こしします。文字起こし完了後にMODE Iと同じ分析を実行できます。

---

## 使い方

### 事前準備
- **ブラウザ**: Chrome を使用してください（MODE IIのWeb Speech API依存）
- **APIキー**: Anthropic の Claude APIキー（`sk-ant-...`）が必要です

### MODE I の手順

1. Claude APIキーを入力
2. Apple PodcastページをMacのSafariなどで「ページを保存」→ `.htm` として保存
3. HTMファイルをドロップ、または目次テキストをペースト
4. 「TASSIOで解析」ボタンを押す

### MODE II の手順

1. Claude APIキーを入力
2. 音声ファイルをドロップ（mp3 / m4a / wav / ogg / aac）
3. 「文字起こし開始」→ 音声が自動再生されリアルタイムでテキスト化
4. 「停止」→「TASSIOで解析」で分析を実行

---

## 技術スタック

- **MODE I解析 / MODE II分析**: Anthropic Claude API（`claude-sonnet-4-20250514`）
- **文字起こし**: Web Speech API（ブラウザ内蔵・Chrome限定・APIキー不要）
- **概念図描画**: Mermaid.js v10
- **構成**: Vanilla JS / シングルHTMLファイル / GitHub Pages

---

## 注意事項

- MODE IIのWeb Speech APIは **Chrome専用** です
- Claude APIキーはページを閉じると再入力が必要です（localStorage非保存）
- HTMファイルはApple Podcastページを「Webアーカイブ」ではなく **「ページのソース（.htm）」** として保存してください
- エピソードの音声データそのものは取得しません。公開されている説明文・目次テキストのみを対象とします

---

## 名前の由来

**TASSIO** は筒井康隆『旅のラゴス』に登場する記憶者の少年へのオマージュです。耳から聞いた物語を正確に再現する能力を持つ彼のように、TASSIOは音声・テキストから情報の骨格を取り出し、理解可能な形に再構築します。

バクロニムとして：
> **T**ranscribe & **A**rchive **S**ystem for **S**trategic **I**nformation **O**rganization

---

## 開発メモ

- **前身**: `mimikara.fm`（音声文字起こし単機能、開発時間5分・QQシリーズ過去最短記録）
- **リニューアル契機**: Apple PodcastページのHTMから目次・説明文が取得可能と判明。音声なしでも理解支援できると確認。
- **設計思想**: 「ポッドキャスト視聴の代替」ではなく「視聴の前後を補完する理解の補助」。コンテンツ運営の邪魔をしない友軍として設計。

---

## QQ Series

**QuestQueries (QQ Series)** — 日常のモヤモヤをAI対話でアプリに結晶化するプロジェクト  
Senari Gakuin / qq-collective
