---
title: 編譯器錯誤 C2585
ms.date: 11/04/2016
f1_keywords:
- C2585
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
ms.openlocfilehash: 812ab15aacd1f6a215c6a5beb7781983859fe858
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593254"
---
# <a name="compiler-error-c2585"></a>編譯器錯誤 C2585

明確轉換成 'type' 模稜兩可

類型轉換可能會產生一個以上的結果。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 從多個繼承的類別或結構類型的轉換。 如果型別繼承一次以上相同的基底類別，運算子的轉換函式必須使用範圍解析 (`::`) 以指定的轉換中要使用繼承的類別。

1. 轉換運算子和建構函式已經定義產生相同的轉換。