---
title: "noinline |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- noinline
- noinline_cpp
dev_langs:
- C++
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 2ba1e7f6563b480cadc171bd6cea6e5fb4cb9839
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="noinline"></a>noinline
## <a name="microsoft-specific"></a>Microsoft 特定的  
 **__declspec （noinline)**告知編譯器永遠不要內嵌特定成員函式 （在類別中的函式）。  
  
 如果函式不大，而且對程式碼的效能不重要，建議不要內嵌函式。 也就是，如果函式不大且可能不常被呼叫，例如處理錯誤條件的函式。  
  
 請記住，如果函式已標記為 `noinline`，呼叫函式會較小，因而本身即為編譯器的內嵌候選項。  
  
```  
class X {  
   __declspec(noinline) int mbrfunc() {  
      return 0;   
   }   // will not inline  
};  
```  
  
**END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [__declspec](../cpp/declspec.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [inline、__inline、\__forceinline](inline-functions-cpp.md)


