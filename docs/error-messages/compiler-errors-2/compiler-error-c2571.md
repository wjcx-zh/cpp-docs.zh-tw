---
title: 編譯器錯誤 C2571 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2571
dev_langs:
- C++
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96dea582cf5d1211d57eac94a7f70458a51542ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230763"
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