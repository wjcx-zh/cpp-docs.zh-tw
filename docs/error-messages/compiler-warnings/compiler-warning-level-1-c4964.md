---
title: "編譯器警告 （層級 1） C4964 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4964
dev_langs: C++
helpviewer_keywords: C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b1c7483b82c363898bc16ed5fc7d48f9cf0b35c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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