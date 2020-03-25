---
title: 編譯器錯誤 C2720
ms.date: 11/04/2016
f1_keywords:
- C2720
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
ms.openlocfilehash: 24f4329ee631eafc7c2670d9ebf28609c22e7592
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202126"
---
# <a name="compiler-error-c2720"></a>編譯器錯誤 C2720

> '*identifier*'： '*規範*' 儲存類別規範在成員上不合法

儲存類別不能在宣告之外的類別成員上使用。 若要修正這個錯誤，請從類別宣告之外的成員定義中移除不必要的[儲存類別](../../cpp/storage-classes-cpp.md)規範。

## <a name="example"></a>範例

下列範例會產生 C2720，並示範如何修正此問題：

```cpp
// C2720.cpp
struct S {
   static int i;
};
static S::i;   // C2720 - remove the unneeded 'static' to fix it
```
