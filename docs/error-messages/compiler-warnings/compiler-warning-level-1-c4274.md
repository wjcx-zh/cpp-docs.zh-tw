---
title: 編譯器警告 （層級 1） C4274 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4274
dev_langs:
- C++
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39b941fc0cb32e268e33d3b0e1ae66079e8decaf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4274"></a>編譯器警告 （層級 1） C4274
\#ident 忽略;請參閱 #pragma 註解 （exestr，'string'） 的文件  
  
 `#ident`插入物件或可執行檔中的使用者指定的字串，指示詞已被取代。 因此，編譯器會忽略指示詞。  
  
> [!CAUTION]
>  警告 C4274 會提示您使用[#pragma 註解 （exestr，'string'）](../../preprocessor/comment-c-cpp.md)指示詞。 不過，這項建議已被取代，而且將修訂編譯器的未來版本中。 如果您使用`#pragma`指示詞，連結器工具 (LINK.exe) 會忽略指示詞所產生的註解記錄，並且會發出警告[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)。 而不是`#ident`指示詞，我們建議您在應用程式中使用檔案版本資源字串。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移除`#ident "`*字串*`"`指示詞。  
  
## <a name="see-also"></a>另請參閱  
 [註解 （C/c + +）](../../preprocessor/comment-c-cpp.md)   
 [連結器工具警告 LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)   
 [使用資源檔](../../windows/working-with-resource-files.md)