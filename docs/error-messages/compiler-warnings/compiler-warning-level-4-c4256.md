---
title: 編譯器警告 (層級 4) C4256
ms.date: 11/04/2016
f1_keywords:
- C4256
helpviewer_keywords:
- C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
ms.openlocfilehash: 1ec3e64548cead53cea906cdf2abd3dd25ee06d4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991392"
---
# <a name="compiler-warning-level-4-c4256"></a>編譯器警告 (層級 4) C4256

' function '：具有虛擬基底之類別的函式具有 ' ... ';呼叫可能與較舊版本的視覺效果不相容C++

可能的不相容。

請考慮下列程式碼範例。 如果在第7版之前使用 Microsoft C++編譯器的版本編譯了「函式 S2：： S2 （int，...）」的定義，但使用目前的版本來編譯下列範例，則對 S3 的「處理常式」呼叫將無法正確運作，因為特殊案例的呼叫慣例變更。 如果兩個都是以 Visual C++ 6.0 編譯的，呼叫也不會正常運作，除非沒有傳遞省略符號參數。

若要修正這個警告，

1. 請勿在函數中使用省略號。

1. 請確定專案中的所有元件都是以目前的版本（包括任何可能定義或參考此類別的程式庫）建立，然後使用[warning](../../preprocessor/warning.md) pragma 來停用此警告。

下列範例會產生 C4256：

```cpp
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
