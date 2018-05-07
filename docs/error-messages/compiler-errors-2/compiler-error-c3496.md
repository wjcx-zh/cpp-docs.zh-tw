---
title: 編譯器錯誤 C3496 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3496
dev_langs:
- C++
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dbc128c1e9a80c61ad42514827bbf8d47b693e84
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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