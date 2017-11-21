---
title: "編譯器錯誤 C2619 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2619
dev_langs: C++
helpviewer_keywords: C2619
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a4ef72e986aae1746444b434997755a260d715ed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2619"></a>編譯器錯誤 C2619
'identifier'：匿名結構/等位不能有靜態資料成員  
  
 匿名結構或等位的成員會宣告成 `static`。  
  
 下列範例會產生 C2619，並示範如何修正藉由移除 static 關鍵字修正此問題。  
  
```  
// C2619.cpp  
int main() {  
   union { static int j; };  // C2619  
   union { int j; };  // OK  
}  
```