---
title: 編譯器錯誤 C3645 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3645
dev_langs:
- C++
helpviewer_keywords:
- C3645
ms.assetid: 346da528-ae86-4cd0-9654-f41bee26ac0d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a711f37e3ab54de5e3cfad77b82fbd603edfaf6e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263823"
---
# <a name="compiler-error-c3645"></a>編譯器錯誤 C3645
'function': __clrcall 不可使用於編譯為原生程式碼的函式  
  
 函式中的某些關鍵字會導致編譯為原生函式。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3645。  
  
```  
// C3645.cpp  
// compile with: /clr /c  
#pragma unmanaged   
int __clrcall dog() {}   // C3645  
```