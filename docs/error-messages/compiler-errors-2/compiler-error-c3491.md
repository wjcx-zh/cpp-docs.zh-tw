---
title: 編譯器錯誤 C3491
ms.date: 11/04/2016
f1_keywords:
- C3491
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
ms.openlocfilehash: d0440e05970c344da22d3322bcb587714b41614d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537913"
---
# <a name="compiler-error-c3491"></a>編譯器錯誤 C3491

'var': 無法在不可變的 Lambda 中修改傳值方式擷取

不可變的 Lambda 運算式不能修改以傳值方式擷取的變數的值。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 請使用 `mutable` 關鍵字宣告 Lambda 運算式，或

- 以傳址方式將變數傳遞到 Lambda 運算式的擷取清單。

## <a name="example"></a>範例

下列範例會產生 C3491，因為不可變的 Lambda 運算式主體修改了擷取變數 `m`：

```
// C3491a.cpp

int main()
{
   int m = 55;
   [m](int n) { m = n; }(99); // C3491
}
```

## <a name="example"></a>範例

下列範例藉由使用 `mutable` 關鍵字宣告 Lambda 運算式，解決了 C3491：

```
// C3491b.cpp

int main()
{
   int m = 55;
   [m](int n) mutable { m = n; }(99);
}
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)