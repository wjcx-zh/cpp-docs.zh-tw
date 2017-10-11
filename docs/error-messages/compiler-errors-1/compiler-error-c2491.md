---
title: "編譯器錯誤 C2491 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2491
dev_langs:
- C++
helpviewer_keywords:
- C2491
ms.assetid: 4e5a8f81-124e-402c-a5ec-d35a89b5469e
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 83b369d72b4d2ed296f6abeb68cc69b8c233326e
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2491"></a>編譯器錯誤 C2491
'identifier': 不允許定義 dllimport 函式  
  
 資料、靜態資料成員和函式可以宣告為 `dllimport`，但不可定義為 `dllimport`。  
  
 若要修正這個問題，請從函式定義移除 `__declspec(dllimport)` 規範。  
  
 下列範例會產生 C2491：  
  
```  
// C2491.cpp  
// compile with: /c  
// function definition  
void __declspec(dllimport) funcB() {}   // C2491  
  
// function declaration  
void __declspec(dllimport) funcB();   // OK  
```
