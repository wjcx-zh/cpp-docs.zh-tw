---
title: 編譯器錯誤 C3461 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3461
dev_langs:
- C++
helpviewer_keywords:
- C3461
ms.assetid: bd66833a-545d-445a-bdfe-dee771a450a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a0b9349ed9450c6d74a9311d5b9265f57cc37b81
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255976"
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