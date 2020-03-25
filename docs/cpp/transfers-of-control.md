---
title: 控制權轉移
ms.date: 11/04/2016
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
ms.openlocfilehash: c9a46ccb1cf519080c5105855e41ecd3ebc23f77
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188047"
---
# <a name="transfers-of-control"></a>控制權轉移

您可以在**switch**語句中使用**goto**語句或**case**標籤，來指定分支超過初始化運算式的程式。 除非包含初始設定式的宣告所在區塊是由跳躍陳述式發生的區塊所包圍，否則這類程式碼是不合法的。

下列範例將示範宣告和初始化 `total`、`ch` 和 `i` 物件的迴圈。 還有一個錯誤的**goto**語句，它會將控制權轉移到初始化運算式之後。

```cpp
// transfers_of_control.cpp
// compile with: /W1
// Read input until a nonnumeric character is entered.
int main()
{
   char MyArray[5] = {'2','2','a','c'};
   int i = 0;
   while( 1 )
   {
      int total = 0;

      char ch = MyArray[i++];

      if ( ch >= '0' && ch <= '9' )
      {
         goto Label1;

         int i = ch - '0';
      Label1:
         total += i;   // C4700: transfers past initialization of i.
      } // i would be destroyed here if  goto error were not present
   else
      // Break statement transfers control out of loop,
      //  destroying total and ch.
      break;
   }
}
```

在上述範例中， **goto**語句會嘗試將控制權轉移到 `i`的初始化之後。 不過，如果 `i` 已宣告但尚未初始化，則這項傳送是合法的。

當使用**break**語句結束區塊時，會終結在區塊中宣告做為**while**語句之*語句*的物件 `total` 和 `ch`。
