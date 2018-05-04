---
title: auto 關鍵字 |Microsoft 文件
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
ms.openlocfilehash: 93b2f5e28dc0306a996b4c8bdb799122fe4646ab
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="auto-keyword"></a>auto 關鍵字
`auto` 關鍵字是一個宣告指定名稱。 不過，C++ 標準為此關鍵字定義了原始和修訂的意義。 Visual c + + 2010 之前,`auto`關鍵字會宣告中的變數*自動*儲存類別，也就是具有區域存留期的變數。 從 Visual c + + 2010，開始`auto`關鍵字宣告的型別推算其宣告中的初始化運算式的變數。 [/Zc: auto&#91;-&#93; ](../build/reference/zc-auto-deduce-variable-type.md)編譯器選項可控制的意義`auto`關鍵字。  
  
## <a name="syntax"></a>語法  
  
```cpp  
auto declarator ;  
auto declarator initializer;  
```  
  
## <a name="remarks"></a>備註  
 `auto` 關鍵字的定義在 C++ 程式語言中已經改變，但是，在 C 程式設計語言中則未改變。  
  
 下列主題描述 `auto` 關鍵字和對應的編譯器選項：  
  
-   [自動](../cpp/auto-cpp.md)說明的新定義`auto`關鍵字。  
  
  
-   [/Zc: auto （推算變數類型）](../build/reference/zc-auto-deduce-variable-type.md)描述編譯器選項會告訴編譯器的定義`auto`来使用的關鍵字。  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)