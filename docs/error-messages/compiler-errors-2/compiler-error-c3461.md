---
title: "編譯器錯誤 C3461 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3461
dev_langs:
- C++
helpviewer_keywords:
- C3461
ms.assetid: bd66833a-545d-445a-bdfe-dee771a450a4
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 27cc201ff7b11b5a44179d5a678bee42d0b21609
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3461"></a>編譯器錯誤 C3461
'type': 只能轉送 Managed 類型  
  
 類型轉送只能在 CLR 類型上執行。  請參閱[類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md)如需詳細資訊。  
  
 如需詳細資訊，請參閱[類型轉送 (C + + /CLI)](../../windows/type-forwarding-cpp-cli.md)。  
  
## <a name="example"></a>範例  
 下列範例會建立元件。  
  
```  
// C3461.cpp  
// compile with: /clr /LD  
public ref class R {};  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C3461。  
  
```  
// C3461b.cpp  
// compile with: /clr /c  
#using "C3461.dll"  
class N {};  
[assembly:TypeForwardedTo(N::typeid)];   // C3461  
[assembly:TypeForwardedTo(R::typeid)];   // OK  
```
