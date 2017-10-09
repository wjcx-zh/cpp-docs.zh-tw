---
title: "編譯器錯誤 C2087 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2087
dev_langs:
- C++
helpviewer_keywords:
- C2087
ms.assetid: 89761e83-415a-4468-a4c6-b6dedfd1dd6a
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 047c58d495233ba69d8d688696b80aa756bb9462
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2087"></a>編譯器錯誤 C2087
'identifier': 遺漏註標  
  
 具有多個註標的陣列定義遺漏註標的值，高於一個維度。  
  
 下列範例會產生 C2087:  
  
```  
// C2087.cpp  
int main() {  
   char a[10][];   // C2087  
}  
```  
  
 可能的解決方式：  
  
```  
// C2087b.cpp  
int main() {  
   char b[4][5];  
}  
```
