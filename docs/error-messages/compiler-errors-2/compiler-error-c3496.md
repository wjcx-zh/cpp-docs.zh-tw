---
title: "編譯器錯誤 C3496 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3496
dev_langs:
- C++
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e8e5e441011c69e2b50b4565981d89a7730d542f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)