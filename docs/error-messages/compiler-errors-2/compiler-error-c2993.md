---
title: "編譯器錯誤 C2993 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2993
dev_langs:
- C++
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3715e2183c8194fe7bcf2613cbee3a0052588385
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2993"></a>編譯器錯誤 C2993
'identifier': 非類型樣板參數 'parameter' 的類型不合法  
  
 您無法宣告結構或等位的引數的範本。 使用指標做為範本參數，傳遞結構和等位。  
  
 下列範例會產生 C2993:  
  
```  
// C2993.cpp  
// compile with: /c  
// C2993 expected  
struct MyStruct {  
   int a;char b;  
};  
  
template <class T, struct MyStruct S>   // C2993  
  
// try the following line instead  
// template <class T, struct MyStruct * S>  
class CMyClass {};  
```  
  
 在 Visual Studio.NET 2003年所完成之編譯器一致性工作也會產生此錯誤： 浮點非類型樣板參數不能再使用。 C + + 標準不允許浮點非類型樣板參數。  
  
 如果函式樣板，傳入浮點函式引數使用點 （此程式碼是有效的 Visual Studio.NET 2003年和 Visual Studio.NET 版本的 Visual c + + 中） 的非類型樣板參數。 如果是類別樣板，沒有簡單的解決方法。  
  
```  
// C2993b.cpp  
// compile with: /c  
template<class T, float f> void func(T) {}   // C2993  
  
// OK  
template<class T>   void func2(T, float) {}  
```