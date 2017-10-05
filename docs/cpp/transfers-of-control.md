---
title: "控制權轉移 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: a604c95bb21ad0098a3d4563738971791fc94a07
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="transfers-of-control"></a>控制權轉移
您可以使用`goto`陳述式或**案例**中加上標籤`switch`陳述式來指定分支過去的初始設定式的程式。 除非包含初始設定式的宣告所在區塊是由跳躍陳述式發生的區塊所包圍，否則這類程式碼是不合法的。  
  
 下列範例將示範宣告和初始化 `total`、`ch` 和 `i` 物件的迴圈。 其中也有一個錯誤的 `goto` 陳述式，會將控制項傳送至超出初始設定式的位置。  
  
```  
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
  
 在前述範例中，`goto` 陳述式會嘗試將控制項傳遞至超出 `i` 初始化的位置。 不過，如果 `i` 已宣告但尚未初始化，則這項傳送是合法的。  
  
 物件`total`和`ch`做為區塊中宣告*陳述式*的`while`陳述式中，使用結束該區塊時，會終結`break`陳述式。  
  

