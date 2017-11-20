---
title: "編譯器錯誤 C3254 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3254
dev_langs: C++
helpviewer_keywords: C3254
ms.assetid: 93427b10-fa72-4e43-80d1-1a6e122f9f40
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 104ee89c45d8a1134611535ab6aa9c62f09e139c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3254"></a>編譯器錯誤 C3254
'明確覆寫': 類別包含明確覆寫 'override'，但不是衍生自包含函式宣告的介面  
  
 當您[明確覆寫](../../cpp/explicit-overrides-cpp.md)方法，包含覆寫的類別必須衍生，直接或間接、 包含函式的型別從您正在覆寫。  
  
 下列範例會產生 C3254:  
  
```  
// C3254.cpp  
__interface I  
{  
   void f();  
};  
  
__interface I1 : I  
{  
};  
  
struct A /* : I1 */  
{  
   void I1::f()  
   {   // C3254, uncomment : I1 to resolve this C3254  
   }  
};  
  
int main()  
{  
}  
```