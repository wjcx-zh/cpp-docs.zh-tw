---
title: "編譯器錯誤 C3460 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3460
dev_langs:
- C++
helpviewer_keywords:
- C3460
ms.assetid: adbf8775-10ca-4654-acdf-58dd765351cd
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d0c56650c58849088c030adbe8edf9222cb2ace0
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3460"></a>編譯器錯誤 C3460
'type': 只能轉送使用者定義的類型  
  
 如需詳細資訊，請參閱[類型轉送 (C + + /CLI)](../../windows/type-forwarding-cpp-cli.md)。  
  
## <a name="example"></a>範例  
 下列範例會建立元件。  
  
```  
// C3460.cpp  
// compile with: /LD /clr  
public ref class R {};  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C3460。  
  
```  
// C3460_b.cpp  
// compile with: /clr /c  
#using "C3460.dll"  
[assembly:TypeForwardedTo(int::typeid)];   // C3460  
[assembly:TypeForwardedTo(R::typeid)];  
```
