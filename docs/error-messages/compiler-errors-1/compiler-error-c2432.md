---
title: 編譯器錯誤 C2432 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2432
dev_langs:
- C++
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8dfbadf2c7d53cce799efbd5f10286b31bb3cd3b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2432"></a>編譯器錯誤 C2432
'identifier' 中的 16 位元資料的參考不合法  
  
 16 位元暫存器做為索引或基底暫存器。 編譯器不支援參考 16 位元的資料。 16 位元暫存器不能做為索引或基底暫存器中針對 32 位元程式碼進行編譯。  
  
 下列範例會產生 C2432:  
  
```  
// C2432.cpp  
// processor: x86  
int main() {  
   _asm mov eax, DWORD PTR [bx]   // C2432  
}  
```