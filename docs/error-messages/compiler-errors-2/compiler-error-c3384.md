---
title: "編譯器錯誤 C3384 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3384
dev_langs:
- C++
helpviewer_keywords:
- C3384
ms.assetid: c9f92c6a-62a9-4333-b2b1-bc55c7f288b6
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: ce70a37639288bce3244f48635ae4b756bb98cad
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3384"></a>編譯器錯誤 C3384
'type_parameter': 數值條件約束和 ref 條件約束互斥  
  
 您不能將泛型類型限制為 `value class` 和 `ref class`。  
  
 請參閱[泛型型別參數的條件約束 (C + + /CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)如需詳細資訊。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3384。  
  
```  
// C3384.cpp  
// compile with: /c /clr  
generic <typename T>  
where T : ref class  
where T : value class   // C3384  
ref class List {};  
```
