---
title: "編譯器錯誤 C2867 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2867
dev_langs:
- C++
helpviewer_keywords:
- C2867
ms.assetid: 63be26b2-d9ab-4f3d-a8b7-981ce3e4d6b9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d49fdc3a9e78e6b3903d8ea0015e03f8a1a24e65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2867"></a>編譯器錯誤 C2867
'identifier': 不是命名空間  
  
 A`using`指示詞會套用至命名空間以外的項目。  
  
 下列範例會產生 C2867:  
  
```  
// C2867.cpp  
// compile with: /c  
namespace N {  
   class X {};  
}  
using namespace N::X;   // C2867  
```