---
title: "編譯器錯誤 C3351 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3351
dev_langs:
- C++
helpviewer_keywords:
- C3351
ms.assetid: c021bbbe-1067-4f51-af4f-940d2b792eb5
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: c6a449d904e0b5122ec1a8d2ae9734a6dd3f8b00
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3351"></a>編譯器錯誤 C3351
'object': 委派建構函式：第二個引數必須是靜態成員函式或全域函式的位址  
  
 編譯器必須有宣告為 `static`之函式的位址。  
  
 下列範例會產生 C3351：  
  
```  
// C3351a.cpp  
// compile with: /clr  
delegate int D(int, int);  
  
ref class C {  
public:  
   int mf(int, int) {  
      return 1;  
   }  
  
   static int mf2(int, int) {  
      return 1;  
   }  
};  
  
int main() {  
   System::Delegate ^pD = gcnew D(nullptr, &C::mf);   // C3351  
   System::Delegate ^pD2 = gcnew D(&C::mf2);  
}  
```  

