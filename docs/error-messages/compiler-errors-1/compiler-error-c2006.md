---
title: 編譯器錯誤 C2006 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2006
dev_langs:
- C++
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 93880e7d767de3101cd7a292af5fa2874cae86bf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2006"></a>編譯器錯誤 C2006
'directive' 必須是檔名，找到 'token'  
  
 指示詞，例如[#include](../../preprocessor/hash-include-directive-c-cpp.md)或[#import](../../preprocessor/hash-import-directive-cpp.md)需要檔名。 若要解決此錯誤，請確定*語彙基元*是有效的檔名。 此外，將檔案名稱放在雙引號或角括弧。  
  
 下列範例會產生 C2006:  
  
```  
// C2006.cpp  
#include stdio.h   // C2006  
```  
  
 可能的解決方式：  
  
```  
// C2006b.cpp  
// compile with: /c  
#include <stdio.h>  
```