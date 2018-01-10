---
title: "編譯器警告 （層級 3） C4102 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4102
dev_langs: C++
helpviewer_keywords: C4102
ms.assetid: 349f308a-daf3-48c6-bd53-6c38b73f8880
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 92161f1c1b6d4a11babfeda11b23c9c71cad3398
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4102"></a>編譯器警告 (層級 3) C4102
'label': 未參考的標籤  
  
 標籤已定義但從未參考。 編譯器會忽略標籤。  
  
 下列範例會產生 C4102：  
  
```  
// C4102.cpp  
// compile with: /W3  
int main() {  
   int a;  
  
   test:   // C4102, remove the unreferenced label to resolve  
  
   a = 1;  
}  
```