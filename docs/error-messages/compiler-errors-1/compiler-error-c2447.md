---
title: 編譯器錯誤 C2447
ms.date: 11/04/2016
f1_keywords:
- C2447
helpviewer_keywords:
- C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
ms.openlocfilehash: 64dca8313af8b640b7b03c1ab27a1a31fa90de09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301964"
---
# <a name="compiler-error-c2447"></a>編譯器錯誤 C2447

'{' : 遺漏函式標頭 (舊樣式型式清單？)

編譯器在全域範圍遇到未預期的左大括號。 大部分情況下，這是由格式錯誤的函式標頭、錯置的宣告或分號分隔群組所造成。 若要解決這個問題，請確認左大括號後面的正確格式的函式標頭，而且之後沒有宣告或分號分隔群組。

這項錯誤也可能是因舊式 C 語言格式引數清單而造成。 若要解決此問題，請重構引數清單以使用現代樣式，也就是用括號括住。

下列範例會產生 C2447:

```
// C2447.cpp
int c;
{}       // C2447
```