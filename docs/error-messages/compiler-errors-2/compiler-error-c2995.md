---
title: 編譯器錯誤 C2995
ms.date: 11/04/2016
f1_keywords:
- C2995
helpviewer_keywords:
- C2995
ms.assetid: a57cdfe0-b40b-4a67-a95c-1a49ace4842b
ms.openlocfilehash: 56bd012457fe17cec7d46095ba7c98658d030b14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404269"
---
# <a name="compiler-error-c2995"></a>編譯器錯誤 C2995

'function': 函式樣板已經定義過了

請確定樣板類別的每個成員函式都只有一個定義。

下列範例會產生 C2995：

```
// C2995.cpp
// compile with: /c
template <class T>
void Test(T x){}

template <class T> void Test(T x){}   // C2995
template <class T> void Test2(T x){}   // OK
```