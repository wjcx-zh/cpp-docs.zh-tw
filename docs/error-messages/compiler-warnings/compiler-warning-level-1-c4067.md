---
title: 編譯器警告 （層級 1） C4067 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4067
dev_langs:
- C++
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4eccec985e6a9e652f18c6513542942351ff6efc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4067"></a>編譯器警告 （層級 1） C4067
未預期的語彙基元下列前置處理器指示詞-必須是新行  
  
 編譯器發現，並忽略多餘的字元，前置處理器指示詞後面。 在 ANSI 相容性只會出現這個警告 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。  
  
```  
// C4067a.cpp  
// compile with: /DX /Za /W1  
#pragma warning(default:4067)  
#if defined(X)  
#else  
#endif v   // C4067  
int main()  
{  
}  
```  
  
### <a name="to-resolve-this-warning-try-the-following"></a>若要解決這個警告，請嘗試下列各項：  
  
1.  編譯與 **/Ze**。  
  
2.  使用註解分隔符號：  
  
```  
// C4067b.cpp  
// compile with: /DX /Za /W1  
#if defined(X)  
#else  
#endif  
int main()  
{  
}  
```