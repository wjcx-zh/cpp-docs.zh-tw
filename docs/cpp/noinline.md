---
title: noinline |Microsoft Docs
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
ms.openlocfilehash: 37098e904402a42f6ff28e594db265fc07b4d458
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942907"
---
# <a name="noinline"></a>noinline
## <a name="microsoft-specific"></a>Microsoft 特定的  
 **__declspec （noinline)** 會告知編譯器永遠不要內嵌特定成員函式 （在類別中的函式）。  
  
 如果函式不大，而且對程式碼的效能不重要，建議不要內嵌函式。 也就是，如果函式不大且可能不常被呼叫，例如處理錯誤條件的函式。  
  
 請記住，如果函式標示**noinline**，呼叫的函式會較小，因此，本身為編譯器的內嵌的候選項目。  
  
```cpp 
class X {  
   __declspec(noinline) int mbrfunc() {  
      return 0;   
   }   // will not inline  
};  
```  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [__declspec](../cpp/declspec.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [inline、__inline、\__forceinline](inline-functions-cpp.md)

