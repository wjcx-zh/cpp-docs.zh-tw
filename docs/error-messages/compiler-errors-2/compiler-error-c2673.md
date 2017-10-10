---
title: "編譯器錯誤 C2673 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2673
dev_langs:
- C++
helpviewer_keywords:
- C2673
ms.assetid: 780230c0-619b-4a78-b01d-ff5886306741
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 551801e5d13f18335d30fb1ea37ad29ca27aa777
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2673"></a>編譯器錯誤 C2673
'function': 全域函式沒有 'this' 指標  
  
 全域函式嘗試存取`this`。  
  
 下列範例會產生 C2673:  
  
```  
// C2673.cpp  
int main() {  
   this = 0;   // C2673  
}  
```
