---
title: "編譯器錯誤 C3076 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3076
dev_langs:
- C++
helpviewer_keywords:
- C3076
ms.assetid: 8a87b3e4-2c17-4b87-9622-ef0962d6a34e
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: eb4668f69ca7d8680620c85b7a37b70c2c58c96b
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3076"></a>編譯器錯誤 C3076
'instance': 您無法在原生類型中內嵌執行個體的參考型別 'type'，  
  
 原生類型不能包含 CLR 型別的執行個體。  
  
 如需詳細資訊，請參閱[參考類型的 c + + 堆疊語意](../../dotnet/cpp-stack-semantics-for-reference-types.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3076。  
  
```  
// C3076.cpp  
// compile with: /clr /c  
ref struct U {};  
  
struct V {  
   U y;   // C3076  
};  
  
ref struct W {  
   U y;   // OK  
};  
```
