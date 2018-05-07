---
title: 編譯器錯誤 C2381 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2381
dev_langs:
- C++
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bd5f5edcf95144333524c41b803c24b728a621f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2381"></a>編譯器錯誤 C2381
'function': 重複定義;__declspec （noreturn） 不同  
  
 宣告函式，因此然後定義所使用的定義但[noreturn](../../cpp/noreturn.md) `__declspec`修飾詞。 使用`noreturn`構成函式的重複定義; 同意使用需要的宣告和定義`noreturn`。  
  
 下列範例會產生 C2381:  
  
```  
// C2381.cpp  
// compile with: /c  
void f1();  
void __declspec(noreturn) f1() {}   // C2381  
void __declspec(noreturn) f2() {}   // OK  
```