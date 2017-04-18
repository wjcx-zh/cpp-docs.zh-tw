---
title: "編譯器錯誤 C3483 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3483
dev_langs:
- C++
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
caps.latest.revision: 7
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
ms.openlocfilehash: f0bef8bd1a49eb6be611421ebbbd8364032f747a
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3483"></a>編譯器錯誤 C3483
'var' 已是 Lambda 擷取清單的一部分  
  
 您已多次傳遞相同的變數給 Lambda 運算式的擷取清單。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請從擷取清單移除變數的所有其他執行個體。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3483，因為 `n` 變數多次出現在 Lambda 運算式的擷取清單中：  
  
```  
// C3483.cpp  
  
int main()  
{  
   int m = 6, n = 5;  
   [m,n,n] { return n + m; }(); // C3483  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
