---
title: "編譯器警告 （層級 1） C4272 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4272
dev_langs: C++
helpviewer_keywords: C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8d5709ec229ea3e1bfbb985fa35937c7c26b7646
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4272"></a>編譯器警告 (層級 1) C4272
'function': __declspec （dllimport）; 標示為匯入函式時，必須指定原生呼叫慣例。  
  
 它是匯出函式標記為錯誤[__clrcall](../../cpp/clrcall.md)呼叫慣例和編譯器發出這個警告，如果您嘗試匯入函式標示為`__clrcall`。  
  
 下列範例會產生 C4272:  
  
```  
// C4272.cpp  
// compile with: /c /W1 /clr  
__declspec(dllimport) void __clrcall Test();   // C4272  
__declspec(dllimport) void Test2();   // OK  
```