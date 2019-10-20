---
layout: post
title: perplexity
description: evaluation-perplexity
---

`Perplexity`是可以拿來衡量`語言模型(Language Model)`的一個方法，先來看一下他的數學定義

我們可以用以下的式子來表示一個句子的機率

$$ \prod_{i=1}^{m}p(w_{i}) $$

$$ p(w_{i}) $$ 為第i個字的機率，而怎麼計算這個機率就是不同語言模型的工作

例如`unigram`可以表示成 $$ p(w_{i}) $$ ，該字出現的機率跟其他字出現是獨立的

而`bigram`可以表示成 $$ p(w_{i})=p(w_{i} \mid w_{i-1}) $$ ，每個字的機率都依賴於前一個字

而`Perplexity`的公式為

$$ Perplexity = 2^{-l} \quad \textrm{where} \quad l = \frac{1}{M}\sum_{i=1}^{m}\log p(w_{i})  $$

我們可以把整個過程拆成幾個步驟來看

1. 整個句子的機率
2. 取`log`，因為`log`為嚴格遞增函數，所以不影響比較結果
3. 除以`M`做平均 
4. 取負號，所以會變成值越小原本的機率越大
5. 取`2的指數`，一樣為嚴格遞增函數，所以不影響比較結果

註：不影響比較結果的意思是，當今天有多個模型用`Perplexity`來進行比較時，取`對數`跟`指數`並不會影響原本的排名結果

所以我們可以推論，`Perplexity`越小才是越好的語言模型

