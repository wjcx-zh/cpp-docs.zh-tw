---
title: 編譯器警告 （層級 4） C4932 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4932
dev_langs:
- C++
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d99fc58f9e6208db9aaeb8689e8be8b49f9aaea4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294111"
---
# <a name="compiler-warning-level-4-c4932"></a>編譯器警告 (層級 4) C4932
__identifier （identifier) 和\__identifier(identifier) 是否  
  
 編譯器無法區分作為參數傳遞給 **__identifier** 的 `__finally` _finally `__try` 與 **或** 與 [_try](../../windows/identifier-cpp-cli.md)。 您不應該嘗試同時使用它們作為相同程式中的識別項，因為它會導致 [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) 錯誤。  
  
 下列範例會產生 C4932：  
  
```  
// C4932.cpp  
// compile with: /clr /W4 /WX  
int main() {  
   int __identifier(_finally) = 245;   // C4932  
   int __identifier(__finally) = 25;   // C4932  
}  
```