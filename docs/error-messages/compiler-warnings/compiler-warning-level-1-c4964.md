---
title: 編譯器警告 （層級 1） C4964 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4964
dev_langs:
- C++
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98226b2da465d2301356939273d370d76edcb64e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290312"
---
# <a name="compiler-warning-level-1-c4964"></a>編譯器警告 (層級 1) C4964
不指定任何最佳化選項;將不會收集設定檔資訊  
  
 [/GL](../../build/reference/gl-whole-program-optimization.md)和[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)已指定，但沒有最佳化所要求，所以將產生的.pgc 檔案，因此沒有特性指引最佳化會有可能。  
  
 如果您想要執行您的應用程式時產生的.pgc 檔案，請指定其中一個[/O](../../build/reference/o-options-optimize-code.md)編譯器選項。  
  
 下列範例會產生 C4964:  
  
```  
// C4964.cpp  
// compile with: /W1 /GL /link /ltcg:pgi  
// C4964 expected  
// Add /O2, for example, to the command line to resolve this warning.  
int main() {  
   int i;  
}  
```