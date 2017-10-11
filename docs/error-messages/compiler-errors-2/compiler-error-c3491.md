---
title: "編譯器錯誤 C3491 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3491
dev_langs:
- C++
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 58458a1ab0b67eb4fa6d38d0be2fb38f6d7496eb
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3491"></a>編譯器錯誤 C3491
'var': 無法在不可變的 Lambda 中修改傳值方式擷取  
  
 不可變的 Lambda 運算式不能修改以傳值方式擷取的變數的值。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請使用 `mutable` 關鍵字宣告 Lambda 運算式，或  
  
-   以傳址方式將變數傳遞到 Lambda 運算式的擷取清單。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3491，因為不可變的 Lambda 運算式主體修改了擷取變數 `m`：  
  
```  
// C3491a.cpp  
  
int main()  
{  
   int m = 55;  
   [m](int n) { m = n; }(99); // C3491  
}  
```  
  
## <a name="example"></a>範例  
 下列範例藉由使用 `mutable` 關鍵字宣告 Lambda 運算式，解決了 C3491：  
  
```  
// C3491b.cpp  
  
int main()  
{  
   int m = 55;  
   [m](int n) mutable { m = n; }(99);  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
