---
title: "編譯器錯誤 C3488 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3488
dev_langs:
- C++
helpviewer_keywords:
- C3488
ms.assetid: 0a6fcd76-dd3b-48d7-abb3-22eccda96034
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4db52fac476d227bd1dc0f9bf32fd3f9ee550c79
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3488"></a>編譯器錯誤 C3488
預設擷取模式為傳址方式時不允許 'var'  
  
 當您指定 Lambda 運算式的預設擷取模式是透過傳址方式時，無法透過傳址方式將變數傳遞給該運算式的 Capture 子句。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   不要將變數明確地傳遞給 Capture 子句，或  
  
-   不要透過傳址方式指定為預設擷取模式，或  
  
-   透過傳值方式指定為預設擷取模式，或  
  
-   透過傳值方式將變數傳遞給 Capture 子句 (這可能會變更 Lambda 運算式的行為)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3488，因為變數 `n` 的參考出現在其預設模式是透過傳址方式之 Lambda 運算式的 Capture 子句：  
  
```  
// C3488a.cpp  
  
int main()  
{  
   int n = 5;  
   [&, &n]() { return n; } (); // C3488  
}  
```  
  
## <a name="example"></a>範例  
 下列範例顯示 C3488 的四種可能解決方式：  
  
```  
// C3488b.cpp  
  
int main()  
{  
   int n = 5;  
  
   // Possible resolution 1:  
   // Do not explicitly pass &n to the capture clause.  
   [&]() { return n; } ();  
  
   // Possible resolution 2:  
   // Do not specify by-reference as the default capture mode.  
   [&n]() { return n; } ();  
  
   // Possible resolution 3:  
   // Specify by-value as the default capture mode.  
   [=, &n]() { return n; } ();  
  
   // Possible resolution 4:  
   // Pass n by value to the capture clause.  
   [n]() { return n; } ();  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)