---
title: 編譯器錯誤 C3490 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3490
dev_langs:
- C++
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 593e5509ada926f27243a761da3470eb2d846a22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258746"
---
# <a name="compiler-error-c3490"></a>編譯器錯誤 C3490
無法修改 'var'，因為正由常數物件存取中  
  
 在 `const` 方法中宣告的 Lambda 運算式不能修改不可變動的成員資料。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移除方法宣告的 `const` 修飾詞。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3490，因為它修改了 `_i` 方法中的成員變數 `const` ：  
  
```  
// C3490a.cpp  
// compile with: /c  
  
class C  
{  
   void f() const   
   {  
      auto x = [=]() { _i = 20; }; // C3490  
   }  
  
   int _i;  
};  
```  
  
## <a name="example"></a>範例  
 下例會藉由移除方法宣告的 `const` 修飾詞來解析 C3490：  
  
```  
// C3490b.cpp  
// compile with: /c  
  
class C  
{  
   void f()  
   {  
      auto x = [=]() { _i = 20; };  
   }  
  
   int _i;  
};  
```  
  
## <a name="see-also"></a>另請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)