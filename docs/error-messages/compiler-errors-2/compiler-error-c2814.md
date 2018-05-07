---
title: 編譯器錯誤 C2814 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2814
dev_langs:
- C++
helpviewer_keywords:
- C2814
ms.assetid: 7d165136-a08b-4497-a76d-60a21bb19404
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75215a0df53606c8807cc275e86616c1ae8c6b42
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2814"></a>編譯器錯誤 C2814
'member'：原生類型不可以巢狀方式置於 Managed 或 WinRT 類型 'type' 中  
  
## <a name="example"></a>範例  
 原生類型不可以巢狀方式置於 CLR 或 WinRT 類型中。 下列範例會產生 C2814，並示範如何修正此問題。  
  
```  
// C2814.cpp  
// compile with: /clr /c  
ref class A {  
   class B {};   // C2814  
   ref class C {};   // OK  
};  
```  
