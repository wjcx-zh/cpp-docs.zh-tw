---
title: 編譯器錯誤 C3490
ms.date: 11/04/2016
f1_keywords:
- C3490
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
ms.openlocfilehash: 940eae39222548ec74bda8ccb38e669748ffa74f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738397"
---
# <a name="compiler-error-c3490"></a>編譯器錯誤 C3490

無法修改 'var'，因為正由常數物件存取中

在 `const` 方法中宣告的 Lambda 運算式不能修改不可變動的成員資料。

### <a name="to-correct-this-error"></a>若要改正這項錯誤

- 移除方法宣告的 `const` 修飾詞。

## <a name="example"></a>範例

下列範例會產生 C3490，因為它修改了 `_i` 方法中的成員變數 `const` ：

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

下例會藉由移除方法宣告的 `const` 修飾詞來解析 C3490：

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

## <a name="see-also"></a>請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
