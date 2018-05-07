---
title: 編譯器警告 （層級 1） C4965 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4965
dev_langs:
- C++
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b731393471097fd3ba02979a48cd59513eaea9fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4965"></a>編譯器警告 (層級 1) C4965
隱含 box 的整數 0;請使用 nullptr 或明確轉換  
  
 Visual c + + 功能隱含 boxing 實值類型。 在 null 指派現在使用 Managed Extensions for c + + 中產生的指令會變成指派至 boxed int。  
  
 如需詳細資訊，請參閱[Boxing](../../windows/boxing-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4965。  
  
```  
// C4965.cpp  
// compile with: /clr /W1  
int main() {  
   System::Object ^o = 0;   // C4965  
  
   // the previous line is the same as the following line  
   // using Managed Extensions for C++  
   // System::Object *o = __box(0);  
  
   // OK  
   System::Object ^o2 = nullptr;  
   System::Object ^o3 = safe_cast<System::Object^>(0);  
}  
```