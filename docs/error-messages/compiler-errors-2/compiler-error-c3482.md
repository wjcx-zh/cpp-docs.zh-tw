---
title: "編譯器錯誤 C3482 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3482
dev_langs:
- C++
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
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
ms.openlocfilehash: ca80df6224311db87c4c5f1425d825cbada2116c
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3482"></a>編譯器錯誤 C3482
'this' 在非靜態成員函式內只能做為 Lambda 擷取  
  
 您無法將 `this` 傳遞給靜態方法或全域函式中所宣告之 Lambda 運算式的擷取清單。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   將封入函式轉換成非靜態方法，或  
  
-   從 Lambda 運算式的擷取清單中移除 `this` 指標。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3482：  
  
```  
// C3482.cpp  
// compile with: /c  
  
class C  
{  
public:  
   static void staticMethod()  
   {  
      [this] {}(); // C3482  
   }  
};  
```  
  
## <a name="see-also"></a>另請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
