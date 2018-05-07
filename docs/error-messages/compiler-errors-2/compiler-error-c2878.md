---
title: 編譯器錯誤 C2878 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2878
dev_langs:
- C++
helpviewer_keywords:
- C2878
ms.assetid: 83ee3de1-f554-49e8-a840-1f550cee7f69
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67da9f25adfa99cf385eeb7795559102ca56b9d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2878"></a>編譯器錯誤 C2878
'name': 命名空間或類別，此名稱不存在  
  
 您所做的命名空間或未定義的類別的參考。  
  
 下列範例會產生 C2878:  
  
```  
// C2878.cpp  
// compile with: /c  
namespace A {}  
namespace B = C;   // C2878 namespace C doesn't exist  
namespace B = A;   
```