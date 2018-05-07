---
title: 編譯器錯誤 C2373 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2373
dev_langs:
- C++
helpviewer_keywords:
- C2373
ms.assetid: 7a08bf0b-852d-48be-ba75-70df9f4b5951
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af66418c98bd70dbf9e9c9cf378fed21dc4352ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2373"></a>編譯器錯誤 C2373
'identifier' : 重複定義; 類型修飾詞不相同  
  
 已使用不同的類型修飾詞定義識別項。  
  
 下列範例會產生 C2373：  
  
```  
// C2373.h  
void __clrcall func( void );  
const int i = 20;  
```  
  
 然後：  
  
```  
// C2373.cpp  
// compile with: /c  
#include "C2373.h"  
extern void __cdecl func( void );   // C2373  
extern void __clrcall func( void );   // OK  
  
extern int i;   // C2373  
extern const int i;   // OK  
```