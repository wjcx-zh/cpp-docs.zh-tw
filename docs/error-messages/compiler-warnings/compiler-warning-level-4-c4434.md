---
title: "編譯器警告 （層級 4） C4434 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4434
dev_langs:
- C++
helpviewer_keywords:
- C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a9499d145263c3bbb1bd5aac948c6be9e4db48d2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4434"></a>編譯器警告 (層級 4) C4434
類別建構函式必須具有私用存取範圍;變更為私用存取  
  
 C4434 表示編譯器變更的靜態建構函式的存取範圍。 靜態建構函式必須具有私用存取範圍，因為它們只是在 common language runtime 所呼叫。 如需詳細資訊，請參閱[靜態建構函式](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4434。  
  
```  
// C4434.cpp  
// compile with: /W4 /c /clr  
public ref struct R {  
   static R(){}   // C4434  
};  
```