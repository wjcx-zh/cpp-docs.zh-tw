---
title: "編譯器錯誤 C2050 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2050
dev_langs: C++
helpviewer_keywords: C2050
ms.assetid: 66aaed7d-00db-4ce1-a9d6-4447c1cf07ce
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 72675e771dc67607119a663e9f21ad024d9ddb08
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2050"></a>編譯器錯誤 C2050
switch 運算式不是整數  
  
 `switch`運算式評估為非整數值。 若要解決錯誤，只使用整數值在 switch 陳述式。  
  
 下列範例會產生 C2050:  
  
```  
// C2050.cpp  
int main() {  
   int a = 1;  
   switch ("a") {   // C2050  
      case 1:  
         a = 0;  
      default:  
         a = 2;  
   }  
}  
```  
  
 可能的解決方式：  
  
```  
// C2050b.cpp  
int main() {  
   int a = 1;  
   switch (a) {  
      case 1:  
         a = 0;  
      default:  
         a = 2;  
   }  
}  
```