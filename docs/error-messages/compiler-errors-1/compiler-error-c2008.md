---
title: 編譯器錯誤 C2008 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2008
dev_langs:
- C++
helpviewer_keywords:
- C2008
ms.assetid: e748ccbe-ffd4-4008-aca7-e53c25225209
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88dcbc88b50ee46b406d383ec36e1fed167eca05
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2008"></a>編譯器錯誤 C2008
'character'：未預期會出現在巨集定義中  
  
 字元會緊接著巨集名稱。 若要解決錯誤，必須有一個空格巨集名稱後面。  
  
 下列範例會產生 C2008:  
  
```  
// C2008.cpp  
#define TEST1"mytest1"    // C2008  
```  
  
 可能的解決方式：  
  
```  
// C2008b.cpp  
// compile with: /c  
#define TEST2 "mytest2"  
```