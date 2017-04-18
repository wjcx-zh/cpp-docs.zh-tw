---
title: "編譯器警告 （層級 4） C4670 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4670
dev_langs:
- C++
helpviewer_keywords:
- C4670
ms.assetid: e172b134-b1fb-4dfe-8e9d-209ea08b73c7
caps.latest.revision: 6
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
ms.openlocfilehash: caf1f918b04596c741761a5e316f5911e3053a87
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-4-c4670"></a>編譯器警告 (層級 4) C4670
'identifier': 此基底類別無法存取  
  
 無法存取要在 **try** 區塊中擲回之物件的指定基底類別。 如果擲回物件，則無法具現化物件。 請檢查使用正確的存取規範來繼承基底類別。  
  
 下列範例會產生 C4670：  
  
```  
// C4670.cpp  
// compile with: /EHsc /W4  
class A  
{  
};  
  
class B : /* public */ A  
{  
} b;   // inherits A with private access by default  
  
int main()  
{  
    try  
    {  
       throw b;   // C4670  
    }  
    catch( B )  
    {  
    }  
}  
```
