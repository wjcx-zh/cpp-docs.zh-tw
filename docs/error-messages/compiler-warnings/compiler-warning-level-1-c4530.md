---
title: "編譯器警告 （層級 1） C4530 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4530
dev_langs:
- C++
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: adfa006e3b84517601237bbd844ac983115e74ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4530"></a>編譯器警告 (層級 1) C4530
C + + 例外狀況處理常式使用，但回溯語意不會啟用。 指定 /EHsc  
  
 已在使用 c + + 例外狀況處理，但[/EHsc](../../build/reference/eh-exception-handling-model.md)未選取。  
  
 /EHsc 選項尚未啟用，都不會終結在框架中，函式擲出與攔截擲回，此函式之間的自動儲存的物件。 不過，在具有自動儲存的物件建立**再試一次**或**攔截**區塊將被終結。  
  
 下列範例會產生 C4530:  
  
```  
// C4530.cpp  
// compile with: /W1  
int main() {  
   try{} catch(int*) {}   // C4530  
}  
```  
  
 編譯此範例使用 /EHsc 才能解決這個警告。