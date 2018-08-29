---
title: constexpr lambda 運算式，在 c + + |Microsoft Docs
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
ms.openlocfilehash: 1b4636333861cc853130a777956ca4b88114f3c6
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131395"
---
# <a name="constexpr-lambda-expressions-in-c"></a>在 c + + 的 constexpr lambda 運算式
**Visual Studio 2017 版本 15.3 和更新版本**(適用於[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)): lambda 運算式可宣告為**constexpr**或常數運算式中使用時的每個初始設定它會擷取或導入的資料成員是常數運算式內允許的。  

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
Lambda 會以隱含方式**constexpr**如果結果符合需求**constexpr**函式：
```cpp
    auto answer = [](int n) 
    {
        return 32 + n; 
    };

    constexpr int response = answer(10);
``` 
如果 lambda 是隱含或明確**constexpr**，並將它轉換成函式指標，產生的函數也**constexpr**:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```
  
## <a name="see-also"></a>另請參閱  
 [C++ 語言參考](../cpp/cpp-language-reference.md)   
 [C + + 標準程式庫中的函式物件](../standard-library/function-objects-in-the-stl.md)   
 [函式呼叫](../cpp/function-call-cpp.md)   
 [for_each](../standard-library/algorithm-functions.md#for_each)