---
title: "編譯器錯誤 C2513 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2513
dev_langs:
- C++
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 62c55a1a6eb093d4ef6921f6d0f8b7c50683ff8d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2513"></a>編譯器錯誤 C2513
'type': '=' 之前沒有宣告變數  
  
 類型規範會出現在沒有變數識別項的宣告。  
  
 下列範例會產生 C2513:  
  
```  
// C2513.cpp  
int main() {  
   int = 9;   // C2513  
   int i = 9;   // OK  
}  
```  
  
 也因為 Visual Studio.NET 2003年所進行的編譯器一致性處理而產生這個錯誤： typedef，不再允許初始化。 Typedef 的初始化不允許的標準，而且現在會產生編譯器錯誤。  
  
```  
// C2513b.cpp  
// compile with: /c  
typedef struct S {  
   int m_i;  
} S = { 1 };   // C2513  
// try the following line instead  
// } S;  
```  
  
 另外也可以刪除`typedef`來定義彙總初始設定式清單中，但此變數不建議，因為它會建立具有相同名稱做為類型的變數和隱藏的類型名稱。