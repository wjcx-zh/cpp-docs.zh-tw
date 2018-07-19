---
title: auto 關鍵字 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9b4b9e2526d621e9e9fee1d1f8c05c5a05d3312
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941674"
---
# <a name="auto-keyword"></a>auto 關鍵字
**自動**關鍵字是宣告指定名稱。 不過，C++ 標準為此關鍵字定義了原始和修訂的意義。 Visual c + + 2010 中前,**自動**關鍵字會宣告中的變數*自動*儲存類別，也就是具有區域存留期的變數。 Visual c + + 2010 中，為起**自動**關鍵字會宣告從其宣告中的初始化運算式推算類型的變數。 [/Zc: auto&#91;-&#93; ](../build/reference/zc-auto-deduce-variable-type.md)編譯器選項可控制的意義**自動**關鍵字。  
  
## <a name="syntax"></a>語法  
  
```cpp  
auto declarator ;  
auto declarator initializer;  
```  
  
## <a name="remarks"></a>備註  
 定義**自動**關鍵字在 c + + 程式設計語言中，但不是以 C 程式設計語言的變更。  
  
 下列主題將描述**自動**關鍵字和對應的編譯器選項：  
  
-   [自動](../cpp/auto-cpp.md)描述的新定義**自動**關鍵字。  
  
  
-   [/Zc: auto （推算變數類型）](../build/reference/zc-auto-deduce-variable-type.md)描述編譯器選項會告訴編譯器的定義**自動**關鍵字，才能使用。  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)