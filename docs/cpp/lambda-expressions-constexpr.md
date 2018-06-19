---
title: constexpr c + + 中的 Lambda 運算式 |Microsoft 文件
ms.custom: ''
ms.date: 07/19/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e01f41aaf8b761020f57625e7cbf06f8fba2659
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418896"
---
# <a name="constexpr-lambda-expressions-in-c"></a>constexpr c + + 中的 Lambda 運算式
**Visual Studio 2017 15.3 和更新版本**(適用於[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)): 可能會做為宣告的 lambda 運算式`constexpr`或 contant 運算式中使用時的每個資料成員初始設定它擷取或導入了常數運算式中允許使用。  

```cpp
    int y = 32;
    auto answer = [y]() constexpr 
    {
        int x = 10;
        return y + x; 
    };

    constexpr int Increment(int n) 
    {
        return [n] { return n + 1; }();
    }

``` 
Lambda 會隱含地`constexpr`如果它的結果符合需求的`constexpr`函式：
```cpp
    auto answer = [](int n) 
    {
        return 32 + n; 
    };

    constexpr int response = answer(10);
``` 
如果 lambda 是隱含或明確地`constexpr`，並將它轉換成函式指標、 產生的函數也是`constexpr`:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```
  
## <a name="see-also"></a>另請參閱  
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [C + + 標準程式庫中的函式物件](../standard-library/function-objects-in-the-stl.md)   
 [函式呼叫](../cpp/function-call-cpp.md)   
 [for_each](../standard-library/algorithm-functions.md#for_each)