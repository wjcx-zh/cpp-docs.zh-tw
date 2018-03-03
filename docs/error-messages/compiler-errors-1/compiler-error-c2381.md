---
title: "編譯器錯誤 C2381 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2381
dev_langs:
- C++
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5871a20eb09b11d47200575033f3a67b98864369
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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