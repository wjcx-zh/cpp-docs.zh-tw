---
title: "編譯器錯誤 C2382 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2382
dev_langs:
- C++
helpviewer_keywords:
- C2382
ms.assetid: 4d4436f9-d0d6-4bd0-b8ec-767b89adfb2f
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 086a0675e877360d424346edfd2b32ea558514aa
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2382"></a>編譯器錯誤 C2382
'function'：重複定義; 不同的例外狀況規格  
  
 在 [/Za](../../build/reference/za-ze-disable-language-extensions.md)下，此錯誤表示嘗試只在 [例外狀況規格](../../cpp/exception-specifications-throw-cpp.md)執行函式多載。  
  
 下列範例會產生 C2382：  
  
```  
// C2382.cpp  
// compile with: /Za /c  
void f1(void) throw(int) {}  
void f1(void) throw(char) {}   // C2382  
void f2(void) throw(char) {}   // OK  
```
