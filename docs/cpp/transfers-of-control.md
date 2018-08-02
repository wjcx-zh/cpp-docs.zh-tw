---
title: 控制權轉移 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e773a0188eb3450ab1a13a24fc556fa8e8c4f874
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464265"
---
# <a name="transfers-of-control"></a>控制權轉移
您可以使用**goto**陳述式或**案例**標示**切換**陳述式來指定分支延伸超過初始設定式的程式。 除非包含初始設定式的宣告所在區塊是由跳躍陳述式發生的區塊所包圍，否則這類程式碼是不合法的。  
  
 下列範例將示範宣告和初始化 `total`、`ch` 和 `i` 物件的迴圈。 另外還有一個錯誤**goto**控制權轉移過去的初始設定式的陳述式。  
  
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
  
 在上述範例中， **goto**陳述式會嘗試將控制項的初始化超過`i`。 不過，如果 `i` 已宣告但尚未初始化，則這項傳送是合法的。  
  
 物件`total`及`ch`做為區塊中宣告*陳述式*的**雖然**陳述式，該區塊結束使用時，會終結**中斷**陳述式。  