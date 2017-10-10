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
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0442b94b1151dbee006a0d3ee71b1076d7afe7df
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

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
