---
title: 編譯器錯誤 C3255 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3255
dev_langs:
- C++
helpviewer_keywords:
- C3255
ms.assetid: 877ffca2-fd92-44b6-9060-6091b928b1c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 740deb9a2981839a12d2570328369daf741a8da9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33251591"
---
# <a name="compiler-error-c3255"></a>編譯器錯誤 C3255
'實值類型': 無法以動態方式配置這個實值類型物件，在原生堆積上  
  
 實值類型的執行個體 (請參閱[類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md))，其中包含受管理的成員可以在堆疊上，但不是在堆積上建立。  
  
 下列範例會產生 C3255:  
  
```  
// C3255.cpp  
// compile with: /clr  
using namespace System;  
value struct V {  
   Object^ o;  
};  
  
value struct V2 {  
   int i;  
};  
  
int main() {  
   V* pv = new V;   // C3255  
   V2* pv2 = new V2;  
   V v2;  
}  
```  
