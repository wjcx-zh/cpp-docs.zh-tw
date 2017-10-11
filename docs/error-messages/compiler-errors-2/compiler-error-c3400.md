---
title: "編譯器錯誤 C3400 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3400
dev_langs:
- C++
helpviewer_keywords:
- C3400
ms.assetid: d44169a8-73b6-4766-b406-b3a6c93f2a4d
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 5eb0815c218fc018120f7502a4d1c081e98d6642
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3400"></a>編譯器錯誤 C3400
循環條件約束相依性，涉及 'constraint_1' 和 'constraint_2'  
  
 編譯器偵測到循環條件約束。  
  
 如需詳細資訊，請參閱[泛型型別參數的條件約束 (C + + /CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3400。  
  
```  
// C3400.cpp  
// compile with: /clr /c  
generic<class T, class U>  
where T : U  
where U : T   // C3400  
public ref struct R {};  
```
