---
title: "編譯器錯誤 C2006 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2006
dev_langs:
- C++
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 8d182e7a98d01dee4047defa5adb5ccc2dc7cde5
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

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
