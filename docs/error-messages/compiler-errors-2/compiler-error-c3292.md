---
title: 編譯器錯誤 C3292 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3292
dev_langs:
- C++
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55a7f91bb9d47f2675525cf17096deddae30be71
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3292"></a>編譯器錯誤 C3292
無法重新開啟 cli 命名空間  
  
 無法在程式碼中宣告 cli 命名空間。  如需詳細資訊，請參閱[平台、 default 和 cli 命名空間](../../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3292：  
  
```  
// C3292.cpp  
// compile with: /clr /c  
namespace cli {};   // C3292  
```