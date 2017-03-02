---
title: "編譯器錯誤 C2441 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2441
dev_langs:
- C++
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
caps.latest.revision: 6
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
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 1b98c85df0db4e947ceb5722715f5d020e1ecbec
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2441"></a>編譯器錯誤 C2441
'variable': __declspec(process) 以宣告的符號都必須是在 /clr: pure 模式  
  
 **/Clr: pure**和**/clr: safe** Visual Studio 2015 中的編譯器選項已被取代。  
  
 根據預設，變數會以每個在應用程式定義域**/clr: pure**。 變數標示`__declspec(process)`下**/clr: pure**容易發生錯誤，如果一個應用程式定義域中進行修改，但在另一個讀取。  
  
 因此，編譯器會強制每個處理序變數是`const`下**/clr︰ 純**，使它們讀取只在所有應用程式定義域中的。  
  
 如需詳細資訊，請參閱[程序](../../cpp/process.md)和[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2441。  
  
```  
// C2441.cpp  
// compile with: /clr:pure /c  
__declspec(process) int i;   // C2441  
__declspec(process) const int j = 0;   // OK  
```
