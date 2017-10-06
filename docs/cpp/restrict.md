---
title: "限制 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- restrict_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
caps.latest.revision: 9
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
ms.openlocfilehash: 2d1cdbff84966e7926b30ef70c40581cc3801a93
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="restrict"></a>restrict
**Microsoft 特定的**  
  
 套用至會傳回指標類型的函式宣告或定義，並告知編譯器該函式會傳回物件，且該物件不具有任何其他指標的別名。  
  
## <a name="syntax"></a>語法  
  
```  
__declspec(restrict) return_type f();  
```  
  
## <a name="remarks"></a>備註  
 編譯器會散佈 `__declspec(restrict)`。 例如，CRT `malloc` 函式會以 `__declspec(restrict)` 裝飾，因此，以 `malloc` 初始化至記憶體位置的指標也是隱含不具別名。  
  
 編譯器不會檢查指標實際上有沒有別名。 開發人員必須負責確保程式不會對以 `restrict __declspec` 修飾詞標記的指標使用別名。  
  
 在變數上的語意很類似，請參閱[__restrict](../cpp/extension-restrict.md)。  
  
## <a name="example"></a>範例  
 請參閱[noalias](../cpp/noalias.md)的使用範例`restrict`。  
  
 屬於 c + + AMP 限制關鍵字的相關資訊，請參閱[限制 (c + + AMP)](../cpp/restrict-cpp-amp.md)。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [__declspec](../cpp/declspec.md)   
 [關鍵字](../cpp/keywords-cpp.md)
