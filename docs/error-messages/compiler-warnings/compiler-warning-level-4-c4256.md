---
title: 編譯器警告 (層級 4) C4256
ms.date: 11/04/2016
f1_keywords:
- C4256
helpviewer_keywords:
- C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
ms.openlocfilehash: b1f7534098a04c7c65a380d302999260c960f284
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400952"
---
# <a name="compiler-warning-level-4-c4256"></a>編譯器警告 (層級 4) C4256

'function': 具有虛擬基底類別建構函式有 '...';呼叫可能不相容於舊版的視覺效果C++

可能的不相容。

請參考下列程式碼範例。 如果定義的建構函式 S2::S2 (int i，...) 所使用的視覺效果版本編譯C++之前版本 7，但下列範例中的編譯器編譯使用目前的版本，適用於 S3 建構函式的呼叫就無法正確運作因為特殊案例的呼叫慣例改變。 如果兩個都是以 Visual C++ 6.0 編譯的，呼叫也不會正常運作，除非沒有傳遞省略符號參數。

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