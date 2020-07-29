---
title: 控制權轉移
ms.date: 11/04/2016
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
ms.openlocfilehash: ef437d0a691ceff72485be1ff9584052f540031a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232179"
---
# <a name="transfers-of-control"></a>控制權轉移

您可以 **`goto`** **`case`** 在語句中使用語句或標籤 **`switch`** ，來指定分支超過初始化運算式的程式。 除非包含初始設定式的宣告所在區塊是由跳躍陳述式發生的區塊所包圍，否則這類程式碼是不合法的。

下列範例將示範宣告和初始化 `total`、`ch` 和 `i` 物件的迴圈。 另外還有錯誤 **`goto`** 的語句，它會將控制權轉移到初始化運算式之後。

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

在上述範例中， **`goto`** 語句會嘗試將控制項傳送到超過的初始化 `i` 。 不過，如果 `i` 已宣告但尚未初始化，則這項傳送是合法的。

`total` `ch` *statement* **`while`** 當使用語句結束區塊時，會終結在區塊中宣告做為語句之語句的物件和 **`break`** 。
