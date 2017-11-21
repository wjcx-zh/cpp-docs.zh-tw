---
title: "編譯器錯誤 C2511 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2511
dev_langs: C++
helpviewer_keywords: C2511
ms.assetid: df999efe-fe2b-418b-bb55-4af6a0592631
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1ba01f808fb4dd618291777c1da7490b3b95af3c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2511"></a>編譯器錯誤 C2511
'identifier': 多載 'class' 中找不到的成員函式  
  
 使用指定的參數宣告的函式沒有版本。  可能的原因：  
  
1.  錯誤的參數傳遞至函式。  
  
2.  傳遞的參數順序錯誤。  
  
3.  參數名稱的拼字錯誤。  
  
 下列範例會產生 C2511:  
  
```  
// C2511.cpp  
// compile with: /c  
class C {  
   int c_2;  
   int Func(char *, char *);  
};  
  
int C::Func(char *, char *, int i) {   // C2511  
// try the following line instead  
// int C::Func(char *, char *) {  
   return 0;  
}  
```