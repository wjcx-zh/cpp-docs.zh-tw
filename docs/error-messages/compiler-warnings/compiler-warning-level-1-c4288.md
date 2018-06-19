---
title: 編譯器警告 （層級 1） C4288 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4288
dev_langs:
- C++
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2c51bdc201b364d76f1692db8ee14973c90923f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276626"
---
# <a name="compiler-warning-level-1-c4288"></a>編譯器警告 (層級 1) C4288
使用非標準擴充: 'var': 在 for 迴圈中宣告的迴圈控制變數範圍外使用 for 迴圈 」。它與外部範圍中宣告衝突  
  
 編譯時[/Ze](../../build/reference/za-ze-disable-language-extensions.md)和 **/zc: forscope-**，在宣告的變數**的**之後已使用迴圈[的](../../cpp/for-statement-cpp.md)-迴圈範圍。 C + + 語言的 Microsoft 擴充功能可讓這個變數，以保持在範圍內，而 C4288 提醒您，不會使用第一個宣告的變數。  
  
 請參閱[/zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)如需有關如何指定中的 Microsoft 擴充功能資訊**如**使用 /Ze 迴圈。  
  
 下列範例會產生 C4288:  
  
```  
// C4288.cpp  
// compile with: /W1 /c /Zc:forScope-  
int main() {  
   int i = 0;    // not used in this program  
   for (int i = 0 ; ; ) ;  
   i++;   // C4288 using for-loop declaration of i  
}  
```