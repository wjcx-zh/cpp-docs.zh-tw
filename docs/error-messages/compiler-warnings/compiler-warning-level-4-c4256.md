---
title: 編譯器警告 （層級 4） C4256 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4256
dev_langs:
- C++
helpviewer_keywords:
- C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6112a541f4bc7efc0ab36feb14f285cf132b08e8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075357"
---
# <a name="compiler-warning-level-4-c4256"></a>編譯器警告 (層級 4) C4256

'function': 具有虛擬基底類別建構函式有 '...';呼叫可能不相容於舊版的 Visual c + +

可能的不相容。

請參考下列程式碼範例。 如果定義的建構函式 S2::S2 (int i，...) 使用第 7 版之前的 Visual c + + 編譯器版本所編譯，但下列範例會使用目前的版本編譯，S3 建構函式的呼叫就無法因為正確運作特殊案例的呼叫慣例改變。 如果兩個都是以 Visual C++ 6.0 編譯的，呼叫也不會正常運作，除非沒有傳遞省略符號參數。

若要修正這個警告，

1. 請勿使用建構函式中的省略符號。

1. 請確定專案中的所有元件都建置與目前的版本 （包括任何可能定義或參考此類別的程式庫），然後停用警告 using[警告](../../preprocessor/warning.md)pragma。

下列範例會產生 C4256:

```
// C4256.cpp
// compile with: /W4
// #pragma warning(disable : 4256)
struct S1
{
};

struct S2: virtual public S1
{
   S2( int i, ... )    // C4256
   {
      i = 0;
   }
   /*
   // try the following line instead
   S2( int i)
   {
      i = 0;
   }
   */
};

void func1()
{
   S2 S3( 2, 1, 2 );   // C4256
   // try the following line instead
   // S2 S3( 2 );
}

int main()
{
}
```