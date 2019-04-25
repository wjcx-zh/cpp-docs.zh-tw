---
title: 編譯器錯誤 C2720
ms.date: 11/04/2016
f1_keywords:
- C2720
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
ms.openlocfilehash: c6499fd3f279099ea7c5b31860e70bdaa285e3f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383044"
---
# <a name="compiler-error-c2720"></a>編譯器錯誤 C2720

> '*識別碼*':'*規範*' 儲存類別規範不合法成員上

儲存類別不能在宣告之外的類別成員上使用。 若要修正這個錯誤，請移除不需要[儲存類別](../../cpp/storage-classes-cpp.md)規範定義中的類別宣告之外的成員。

## <a name="example"></a>範例

下列範例會產生 C2720，並示範如何修正此問題：

```cpp
// C2720.cpp
struct S {
   static int i;
};
static S::i;   // C2720 - remove the unneeded 'static' to fix it
```