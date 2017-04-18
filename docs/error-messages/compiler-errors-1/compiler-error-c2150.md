---
title: "編譯器錯誤 C2150 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2150
dev_langs:
- C++
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 16e080e549ce436573a5d73d743ed6ac771223c2
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2150"></a>編譯器錯誤 C2150
'identifier' : 位元欄位必須是 'int'、'signed int' 或 'unsigned int' 類型  
  
 位元欄位必須是`int`， `signed``int`，或`unsigned``int`。  
  
 下列範例會產生 C2150：  
  
```  
// C2150.cpp  
// compile with: /c  
struct A {  
   float a : 8;    // C2150  
   int i : 8;   // OK  
};  
```
