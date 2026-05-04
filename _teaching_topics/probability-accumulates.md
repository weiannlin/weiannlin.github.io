---
title: "從 PMF、PDF 到混合型：機率是怎麼累積的"
subtitle: "From PMF and PDF to Mixed Distributions: How Probability Accumulates"
layout: topic
collection: teaching_topics
category: "隨機變數"
chapter: 1
permalink: /teaching-topics/probability-accumulates/
date: 2026-05-04
published: false
excerpt: "離散、連續、混合三種隨機變數其實共用同一個第一級物件 ── CDF。PMF 與 PDF 不過是讀取 CDF 的兩種方式。"
related_demos:
  - title: "From PMF to CDF"
    url: /demos/pmf-cdf/
    note: "一點一點編輯離散分布，看 CDF 一階一階累積"
  - title: "From PDF to CDF"
    url: /demos/pdf-cdf/
    note: "六種連續家族；拉動 $x$，看積分如何把 $F$ 一塊一塊建起來"
  - title: "Mixed distributions"
    url: /demos/mixed/
    note: "連續家族外加自訂的單點質量，CDF 在每一個點正好跳 $w_i$"
---

{% include related-demos.html %}

每一份初等機率的教材都會把隨機變數分成三類：**離散型**、**連續型**、**混合型**。標準的講法從各自的「分布」切入 ── 離散用 PMF、連續用 PDF、混合是兩者的拼貼 ── 然後幾乎是順帶一提地引入累積分布函數 (CDF)。

這篇短文把順序倒過來。CDF 才是第一級的物件，PMF 與 PDF 只是從 CDF 讀取資訊的兩種方式。一旦這個順序顛倒過來，混合型就不再像是被特別構造出來的奇案。

## CDF 到底是什麼

對任一實值隨機變數 $X$，它的 **CDF** 定義為

$$ F(x) = P(X \leq x), \qquad x \in \mathbb{R}. $$

整個定義就只有這一行。從這行可以直接推出三個性質：

- $F$ **單調不減**：當 $x$ 變大時，事件 $\\{X \leq x\\}$ 只會多納入結果，不會少。
- $F$ 介於 $0$ 與 $1$ 之間，而 $F(-\infty) = 0$、$F(+\infty) = 1$。
- $F$ **右連續**。

這三個性質不論 $X$ 是離散、連續、還是介於中間的型態都成立。本文後續用到的所有物件 ── PMF、PDF、單點質量 ── 都不過是 $F$ 在某種意義下的導數。

## 離散型：跳躍與棒棒糖

若 $X$ 只取有限或可數個值 $x\_1, x\_2, \dots$，對應權重為 $p\_i = P(X = x\_i)$，則

$$ F(x) = \sum_{x_i \leq x} p_i. $$

CDF 是一個**階梯函數**，在每一個 $x\_i$ 跳躍 $p\_i$，跳躍之間維持水平。PMF 就是**每個跳躍的高度** ── 在離散意義下相當於 CDF 的「導數」。

把 PMF 畫成棒棒糖圖時，每一根棒子都是該點的跳躍量，CDF 則從 $0$ 一階一階爬升至 $1$，每一階都是右半開的。右連續這件事在這裡有實際意義：CDF 在跳躍點的值是該階梯的**頂端**，不是底端。

&rarr; 互動範例：**[From PMF to CDF](/demos/pmf-cdf/)**。

## 連續型：斜率與面積

若 $F$ 可微，定義

$$ f(x) = F'(x). $$

則 $f$ 就是 **PDF**，而機率變成 PDF 曲線下的面積：

$$ P(a < X \leq b) = F(b) - F(a) = \int_a^b f(x)\, dx. $$

兩個值得留意的後果：

1. $f(x)$ **不是**機率，是機率**密度**。$f(x)$ 的值可以大於 $1$ 而毫無矛盾。只有 $f(x)\, dx$ 的單位才是機率。
2. 對任一單獨的點 $x$，皆有 $P(X = x) = 0$。連續型的機率住在有正寬度的區間裡。

&rarr; 互動範例：**[From PDF to CDF](/demos/pdf-cdf/)**。

## 混合型：能平滑就平滑、該跳躍就跳躍

混合型在教科書中常被當成奇例，但在實務上其實最常見。一段含有「正機率正好為零」的等待時間；一個被感測器飽和值截斷的量測；一筆消費金額，未消費者集中在 $0$、消費者則服從某連續分布。

CDF 讓這個建構變得自然。挑一個連續家族 $G$ 當作平滑的部分，再列出有限個單點質量 $(x\_i, w\_i)$，每個 $w\_i > 0$。將**連續部分的權重**設為

$$ w_c = 1 - \sum_i w_i, $$

並要求 $w\_c \geq 0$。則

$$ F(x) = w_c \cdot G(x) + \sum_{x_i \leq x} w_i. $$

這個 $F$ 單調不減、介於 $0$ 與 $1$ 之間、且右連續，因此是一個合法的 CDF。它沿著 $w\_c \cdot G$ 平滑爬升，並在每一個 $x\_i$ **正好跳 $w\_i$**。兩個極限狀況可以還原已知情形：

- $w\_c = 1$ 且沒有任何單點：純粹連續型。
- $w\_c = 0$ 且所有 $w\_i$ 加總為 $1$：純粹離散型。

兩者之間的所有設定都是混合型。視覺特徵很清楚：CDF 同時擁有平滑的段落，與肉眼可見的垂直跳躍。

&rarr; 互動範例：**[Mixed distributions](/demos/mixed/)**。

## 整體看一遍

同一個 $F$ 就足以生成上面三種情形：

| | PMF / 單點 | PDF |
| --- | --- | --- |
| **離散** | $F$ 的跳躍 | &mdash; |
| **連續** | &mdash; | $F'$ |
| **混合** | $F$ 的跳躍 | 平滑段上的 $F'$ |

把 $F$ 當作主角後，混合型就不再像是獨立的物種，它就是「同時帶有平滑段與跳躍段」的 CDF。而這正好是現實過程同時擁有「連續模式」與「在特定值上集中機率」時必然出現的型態。

上面三個 demo 讓你從零開始、一根拉桿一根拉桿地組，看著 CDF 慢慢長出來。
