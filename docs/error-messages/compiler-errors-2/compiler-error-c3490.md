---
title: 編譯器錯誤 C3490
ms.date: 11/04/2016
f1_keywords:
- C3490
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
ms.openlocfilehash: 76729f49358e2a05b425730517e88ba14f2909c6
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685720"
---
# <a name="compiler-error-c3490"></a>編譯器錯誤 C3490

無法修改 'var'，因為正由常數物件存取中

在方法中宣告的 lambda 運算式 **`const`** 不能修改非可變成員資料。

### <a name="to-correct-this-error"></a>更正這個錯誤

- **`const`** 從方法宣告中移除修飾詞。

## <a name="examples"></a>範例

下列範例會產生 C3490，因為它會修改方法中的成員變數 `_i` **`const`** ：

```cpp
// C3490a.cpp
// compile with: /c

class C
{
   void f() const
   {
      auto x = [=]() { _i = 20; }; // C3490
   }

   int _i;
};
```

下列範例會藉由從方法宣告中移除修飾詞來解析 C3490 **`const`** ：

```cpp
// C3490b.cpp
// compile with: /c

class C
{
   void f()
   {
      auto x = [=]() { _i = 20; };
   }

   int _i;
};
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
