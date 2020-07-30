---
title: 編譯器錯誤 C3491
ms.date: 11/04/2016
f1_keywords:
- C3491
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
ms.openlocfilehash: f6f20d9af424fdd4254fc15e0580d62b9dfba144
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184471"
---
# <a name="compiler-error-c3491"></a>編譯器錯誤 C3491

'var': 無法在不可變的 Lambda 中修改傳值方式擷取

不可變的 Lambda 運算式不能修改以傳值方式擷取的變數的值。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 使用關鍵字宣告您的 lambda 運算式 **`mutable`** ，或

- 以傳址方式將變數傳遞到 Lambda 運算式的擷取清單。

## <a name="example"></a>範例

下列範例會產生 C3491，因為不可變的 Lambda 運算式主體修改了擷取變數 `m`：

```cpp
// C3491a.cpp

int main()
{
   int m = 55;
   [m](int n) { m = n; }(99); // C3491
}
```

## <a name="example"></a>範例

下列範例會藉由使用關鍵字宣告 lambda 運算式來解析 C3491 **`mutable`** ：

```cpp
// C3491b.cpp

int main()
{
   int m = 55;
   [m](int n) mutable { m = n; }(99);
}
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
