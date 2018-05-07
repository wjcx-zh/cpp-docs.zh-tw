---
title: 編譯器錯誤 C2871 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2871
dev_langs:
- C++
helpviewer_keywords:
- C2871
ms.assetid: 44aeb84d-61f0-45e0-8dad-22a3cd46b7f8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3aae5cc8200599b5f6b0643f07cbd342ec7d47c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2871"></a>編譯器錯誤 C2871
'name': 具有此名稱的命名空間不存在  
  
當您傳遞不是命名空間，以識別項時，會發生這個錯誤[使用](../../cpp/namespaces-cpp.md#using_directives)指示詞。  
  
## <a name="example"></a>範例  
下列範例會產生 C2871:  
  
```cpp  
// C2871.cpp  
// compile with: /c
namespace a {
   int fn(int i) { return i; }
} 
namespace b { 
   using namespace d;   // C2871 because d is not a namespace  
   using namespace a;   // OK
}  
```