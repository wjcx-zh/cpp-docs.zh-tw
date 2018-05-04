---
title: noinline |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noinline_cpp
dev_langs:
- C++
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f81ab892fd7f406292925f424bebc7514fd7ea0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="noinline"></a>noinline
## <a name="microsoft-specific"></a>Microsoft 特定的  
 **__declspec （noinline)** 告知編譯器永遠不要內嵌特定成員函式 （在類別中的函式）。  
  
 如果函式不大，而且對程式碼的效能不重要，建議不要內嵌函式。 也就是，如果函式不大且可能不常被呼叫，例如處理錯誤條件的函式。  
  
 請記住，如果函式已標記為 `noinline`，呼叫函式會較小，因而本身即為編譯器的內嵌候選項。  
  
```  
class X {  
   __declspec(noinline) int mbrfunc() {  
      return 0;   
   }   // will not inline  
};  
```  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [__declspec](../cpp/declspec.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [inline、__inline、\__forceinline](inline-functions-cpp.md)

