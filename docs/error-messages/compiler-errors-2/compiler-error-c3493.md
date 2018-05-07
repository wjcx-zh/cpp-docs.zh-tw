---
title: 編譯器錯誤 C3493 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3493
dev_langs:
- C++
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3aec62bfff59396ec73141746193e4e3f16d84fa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3493"></a>編譯器錯誤 C3493
無法隱含擷取 'var'，因為未指定預設的擷取模式  
  
 空的 Lambda 運算式擷取 `[]`，指定 Lambda 運算式不明確或隱含擷取任何變數。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   提供預設的擷取模式，或  
  
-   明確擷取一或多個變數。  
  
## <a name="example"></a>範例  
 下例會產生 C3493，因為它會修改外部變數，但指定空白的擷取子句：  
  
```  
// C3493a.cpp  
  
int main()  
{  
   int m = 55;  
   [](int n) { m = n; }(99); // C3493  
}  
```  
  
## <a name="example"></a>範例  
 下例會以依參考指定為預設擷取模式的方式解析 C3493。  
  
```  
// C3493b.cpp  
  
int main()  
{  
   int m = 55;  
   [&](int n) { m = n; }(99);  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)