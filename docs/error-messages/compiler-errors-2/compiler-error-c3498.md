---
title: 編譯器錯誤 C3498 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C3498
dev_langs:
- C++
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6d895c0dc40d94d6a8fcd567173e2d596e68e333
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3498"></a>編譯器錯誤 C3498
'var': 您無法擷取的變數，其中包含 managed 或 WinRTtype  
  
 您無法擷取在 lambda 中有 managed 類型或 Windows 執行階段類型的變數。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   將 managed 或 Windows 執行階段變數傳遞至 Lambda 運算式的參數清單。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3498，因為具有 managed 類型的變數會出現在 Lambda 運算式的擷取清單中：  
  
```  
// C3498a.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String ^ s = "Hello";  
   [&s](String ^ r)   
      { return String::Concat(s, r); } (", World!"); // C3498  
}  
```  
  
## <a name="example"></a>範例  
 下列範例會藉由將傳遞 managed 變數 `s` 至 lambda 運算式的擷取清單中，以解析 C3498：  
  
```  
// C3498b.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String ^ s = "Hello";  
   [](String ^ s, String ^ r)   
      { return String::Concat(s, r); } (s, ", World!");  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)