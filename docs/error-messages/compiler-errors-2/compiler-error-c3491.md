---
title: 編譯器錯誤 C3491 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3491
dev_langs:
- C++
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 64d7b2e4bd602a53afeba2f77293c31bb28902d3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068763"
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