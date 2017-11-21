---
title: "編譯器錯誤 C2725 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2725
dev_langs: C++
helpviewer_keywords: C2725
ms.assetid: 13cd5b1b-e906-4cd8-9b2b-510d587c665a
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dbf3a0e84f3cdf6b2ab9e42690cb8bc80f3d2201
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2725"></a>編譯器錯誤 C2725
'exception'：無法以值或參考擲回或攔截 managed 或 WinRT 物件  
  
 managed 或 WinRT 例外狀況的類型不正確。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2725，並顯示如何修正此問題。  
  
```  
// C2725.cpp  
// compile with: /clr  
ref class R {  
public:  
   int i;  
};  
  
int main() {  
   R % r1 = *gcnew R;  
   throw r1;   // C2725  
  
   R ^ r2 = gcnew R;  
   throw r2;   // OK     
}  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C2725，並顯示如何修正此問題。  
  
```  
// C2725b.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   try {}  
   catch( System::Exception%) {}   // C2725  
   // try the following line instead  
   // catch( System::Exception ^e) {}  
}  
```  
