---
title: "編譯器錯誤 C3482 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
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
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: b19769a8a326613401263fa7700b85c36a9dbbe1
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

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
