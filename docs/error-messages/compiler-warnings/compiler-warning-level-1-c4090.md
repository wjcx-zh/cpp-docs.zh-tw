---
title: "編譯器警告 （層級 1） C4090 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4090
dev_langs:
- C++
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 81506e59243cd8ec17087af6a06391ff097ab05d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4090"></a>編譯器警告 （層級 1） C4090
'operation': 不同 '修飾詞' 限定詞  
  
 以指定的修飾詞，避免被偵測未修改由編譯器所定義的作業中所使用的變數。 運算式會編譯而不需修改。  
  
 指標時，可能造成這項警告**const**或`volatile`項目指派給未宣告為指向的指標**const**或`volatile`。  
  
 C 程式會發出這個警告。 在 c + + 程式中，編譯器會發出錯誤： [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md)。  
  
 下列範例會產生 C4090:  
  
```  
// C4090.c  
// compile with: /W1  
int *volatile *p;  
int *const *q;  
int **r;  
  
int main() {  
   p = q;   // C4090  
   p = r;  
   q = p;   // C4090  
   q = r;  
   r = p;   // C4090  
   r = q;   // C4090  
}  
```