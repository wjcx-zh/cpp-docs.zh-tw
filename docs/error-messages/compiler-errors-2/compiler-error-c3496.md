---
title: "編譯器錯誤 C3496 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3496
dev_langs: C++
helpviewer_keywords: C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 86c80c4b708bd4315b2ce2ceaf7b61e0629a8b2e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3496"></a>編譯器錯誤 C3496
'this' 一定以傳值方式擷取: 已忽略 '&'  
  
 您不能以傳址方式來擷取 `this` 指標。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請以傳值方式來擷取 `this` 指標。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3496，因為 `this` 指標的參考出現在 Lambda 運算式的擷取清單中：  
  
```  
// C3496.cpp  
// compile with: /c  
  
class C  
{  
   void f()  
   {  
      [&this] {}(); // C3496  
   }  
};  
```  
  
## <a name="see-also"></a>另請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)