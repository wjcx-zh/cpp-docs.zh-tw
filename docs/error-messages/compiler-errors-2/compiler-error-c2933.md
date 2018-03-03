---
title: "編譯器錯誤 C2933 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2933
dev_langs:
- C++
helpviewer_keywords:
- C2933
ms.assetid: 394891e3-6b52-4b61-83d2-a1c5125d9bd5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 13d35ac5c6a5929b0049bce5b70a61b799a65022
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2933"></a>編譯器錯誤 C2933
'class': type-class-id 重複定義為 'identifier' 的 typedef 成員  
  
 您無法使用泛型或樣板類別作為 `typedef` 成員。  
  
 下列範例會產生 C2933：  
  
```  
// C2933.cpp  
// compile with: /c  
template<class T> struct TC { };   
struct MyStruct {  
   typedef int TC<int>;   // C2933  
};  
  
struct TC2 { };   
struct MyStruct2 {  
   typedef int TC2;  
};  
```  
  
 使用泛型時，也會發生 C2933：  
  
```  
// C2933b.cpp  
// compile with: /clr /c  
generic<class T> ref struct GC { };  
struct MyStruct {  
   typedef int GC<int>;   // C2933  
};  
  
ref struct GC2 { };  
struct MyStruct2 {  
   typedef int GC2;  
};  
```