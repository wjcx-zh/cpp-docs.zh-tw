---
title: "編譯器警告 （層級 3） C4646 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4646
dev_langs: C++
helpviewer_keywords: C4646
ms.assetid: 23677e8e-603e-40e0-b99a-2e4894a1278e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9b44b85fc8834dcc262b10ee26f34752f8eeb429
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4646"></a>編譯器警告 (層級 3) C4646
使用 __declspec(noreturn) 宣告的函式有非 void 的傳回類型  
  
 標記為 [noreturn](../../cpp/noreturn.md) `__declspec` 修飾詞的函式應該有 [void](../../cpp/void-cpp.md) 傳回類型。  
  
 下列範例會產生 C4646：  
  
```  
// C4646.cpp  
// compile with: /W3 /WX  
int __declspec(noreturn) TestFunction()  
{   // C4646  make return type void  
}  
```