---
title: "控制權轉移 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控制流程, 分支處理"
  - "控制流程, 轉移控制權"
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 控制權轉移
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用 `goto` 陳述式或  **陳述式中的 `switch`case** 標籤，指定分支延伸超過初始設定式的程式。  除非包含初始設定式的宣告所在區塊是由跳躍陳述式發生的區塊所包圍，否則這類程式碼是不合法的。  
  
 下列範例將示範宣告和初始化 `total`、`ch` 和 `i` 物件的迴圈。  其中也有一個錯誤的 `goto` 陳述式，會將控制項傳送至超出初始設定式的位置。  
  
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
  
 在前述範例中，`goto` 陳述式會嘗試將控制項傳遞至超出 `i` 初始化的位置。  不過，如果 `i` 已宣告但尚未初始化，則這項傳送是合法的。  
  
 在做為 `total` 陳述式的 `ch`statement 區塊中宣告的  *和 `while` 物件，會在區塊使用 `break` 陳述式結束時終結。*  
  
## 請參閱  
 [\(NOTINBUILD\) Declaration of Automatic Objects](http://msdn.microsoft.com/zh-tw/81f941e9-c1b1-4d1c-a28d-70b6ee9765db)