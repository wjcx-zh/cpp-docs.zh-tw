---
title: 編譯器錯誤 C2585
ms.date: 11/04/2016
f1_keywords:
- C2585
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
ms.openlocfilehash: 57a0cd7a200c5bbb875821eb9e10314d98e58185
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177387"
---
# <a name="compiler-error-c2585"></a>編譯器錯誤 C2585

明確轉換成 ' type ' 是不明確的

類型轉換可能會產生一個以上的結果。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 根據多個繼承，從類別或結構型別轉換。 如果類型繼承相同的基類多次，轉換函式或運算子必須使用範圍解析（`::`）來指定要在轉換中使用的繼承類別。

1. 轉換運算子和函式已定義為進行相同的轉換。
