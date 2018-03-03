---
title: "編譯器錯誤 C2571 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2571
dev_langs:
- C++
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7e760c9e9445339b47dc8f27e2ea5f2561b54af5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2571"></a>編譯器錯誤 C2571
'function': 虛擬函式不能在等位 'union' 中  
  
 等位是以虛擬函式宣告。 您可以宣告只能在類別或結構中的虛擬函式。  可能的解決方式：  
  
1.  變更類別或結構的聯集。  
  
2.  進行非虛擬函式。  
  
 下列範例會產生 C2571:  
  
```  
// C2571.cpp  
// compile with: /c  
union A {  
   virtual void func1();   // C2571  
   void func2();   // OK  
};  
```