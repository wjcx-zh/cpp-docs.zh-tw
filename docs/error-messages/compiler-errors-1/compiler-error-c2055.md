---
title: 編譯器錯誤 C2055 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2055
dev_langs:
- C++
helpviewer_keywords:
- C2055
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f16d9c3948c0211da69142f1b9c7c1a6a32d8c37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169328"
---
# <a name="compiler-error-c2055"></a>編譯器錯誤 C2055
預期的型式參數清單中，不是類型的清單  
  
 函式定義包含參數的型別清單，而不是型式參數清單。 ANSI C 要求的型式參數命名為，除非它們是 void 或省略符號 (`...`)。  
  
 下列範例會產生 C2055:  
  
```  
// C2055.c  
// compile with: /c  
void func(int, char) {}  // C2055  
void func (int i, char c) {}   // OK  
```