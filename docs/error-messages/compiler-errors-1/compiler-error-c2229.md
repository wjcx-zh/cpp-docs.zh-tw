---
title: "編譯器錯誤 C2229 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2229
dev_langs: C++
helpviewer_keywords: C2229
ms.assetid: 933c7cf2-a463-4e74-b0b4-59dedad987fb
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c54e3affb39cb396df1caaafe6450d5c6ac80f6e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2229"></a>編譯器錯誤 C2229
類型 'identifier' 具有不正確的大小為零的陣列  
  
 結構或位元欄位的成員包含不是最後一個成員的大小為零的陣列。  
  
 您可以有零大小的陣列做為結構的最後一個成員，因為您必須指定其大小時配置結構。  
  
 如果為零可調整大小的陣列不是結構的最後一個成員，編譯器就無法計算其餘欄位的位移。  
  
 下列範例會產生 C2229:  
  
```  
// C2229.cpp  
struct S {  
   int a[0];  // C2229  zero-sized array  
   int b[1];  
};  
  
struct S2 {  
   int a;  
   int b[0];  
};  
  
int main() {  
   // allocate 7 elements for b field  
   S2* s2 = (S2*)new int[sizeof(S2) + 7*sizeof(int)];  
   s2->b[6] = 100;  
}  
```