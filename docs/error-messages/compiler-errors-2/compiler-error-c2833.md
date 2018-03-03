---
title: "編譯器錯誤 C2833 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2833
dev_langs:
- C++
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 019fa3cb0b36d9062bc972b01d434afe6e3848aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2833"></a>編譯器錯誤 C2833
'operator operator' 不是可辨認的運算子或類型  
  
 Word`operator`後面必須接著您要覆寫的運算子或您想要轉換的類型。  
  
 如需您可以在 managed 類型中定義的運算子，請參閱[使用者定義運算子](../../dotnet/user-defined-operators-cpp-cli.md)。  
  
 下列範例會產生 C2833:  
  
```  
// C2833.cpp  
// compile with: /c  
class A {};  
  
void operator ::* ();   // C2833  
void operator :: ();   // OK  
```