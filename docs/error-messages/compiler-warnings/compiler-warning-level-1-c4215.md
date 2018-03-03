---
title: "編譯器警告 （層級 1） C4215 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4215
dev_langs:
- C++
helpviewer_keywords:
- C4215
ms.assetid: f2aab64d-1bab-4f75-95ee-89e1263047b1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 900b27141f6e74760dd80f76ebf4e12c1368603f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4215"></a>編譯器警告 (層級 1) C4215
使用非標準擴充： long float  
  
 預設的 Microsoft 擴充功能 (/Ze) 視為**long float**為**double**。 ANSI 相容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 並不會。 使用**double**維護相容性。  
  
 下列範例會產生 C4215:  
  
```  
// C4215.cpp  
// compile with: /W1 /LD  
long float a;   // C4215  
  
// use the line below to resolve the warning  
// double a;  
```