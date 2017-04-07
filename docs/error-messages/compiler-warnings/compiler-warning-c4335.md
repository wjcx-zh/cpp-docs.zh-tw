---
title: "編譯器警告 C4335 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4335
dev_langs:
- C++
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: dc8436664038d3f53f3a01d5006c41c3d0e4c8f0
ms.lasthandoff: 04/01/2017

---
# <a name="compiler-warning-c4335"></a>編譯器警告 C4335
偵測到 Mac 檔案格式: 請將原始程式檔轉換為 DOS 或 UNIX 格式  
  
 原始程式檔的第一行的行結束字元是相對於 UNIX ('\n') 或 DOS ('\r\n') 的 Macintosh 樣式 ('\r')。  
  
 以錯誤發出永遠會發出這個警告。  請參閱[警告](../../preprocessor/warning.md)pragma，如需有關如何停用這個警告資訊。  此外，這個警告才會發出一次每個編譯。 因此，如果有多個`#include`Macintosh 格式來指定檔案的指示詞，C4335 將只會發出一次。  
  
 Macintosh 格式產生檔案的一個方式是使用**進階儲存選項**(上**檔案**功能表) 在 Visual Studio 中。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4335。  
  
```  
// C4335 expected  
#include "c4335.h"   // assume both include files are in Macintosh format  
#include "c4335_2.h"  
```
