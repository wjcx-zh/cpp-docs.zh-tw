---
title: "編譯器錯誤 C2432 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2432
dev_langs:
- C++
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e921fa0cd2a9c56b6449b554fcee307c1121c598
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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