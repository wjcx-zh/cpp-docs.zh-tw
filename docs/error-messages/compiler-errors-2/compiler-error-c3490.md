---
title: 編譯器錯誤 C3490
ms.date: 11/04/2016
f1_keywords:
- C3490
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
ms.openlocfilehash: ea7341b9c587a764c7366fa7b7c89e4fc67bc7d8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230853"
---
# <a name="compiler-error-c3490"></a>編譯器錯誤 C3490

無法修改 'var'，因為正由常數物件存取中

在方法中宣告的 lambda 運算式 **`const`** 無法修改不可變動的成員資料。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 請 **`const`** 從方法宣告中移除修飾詞。

## <a name="example"></a>範例

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

## <a name="example"></a>範例

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
