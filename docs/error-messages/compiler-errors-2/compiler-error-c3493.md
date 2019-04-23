---
title: 編譯器錯誤 C3493
ms.date: 11/04/2016
f1_keywords:
- C3493
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
ms.openlocfilehash: 1bbf9b269075717ae397b7d29ee28c278b1e4ec8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034935"
---
# <a name="compiler-error-c3493"></a>編譯器錯誤 C3493

無法隱含擷取 'var'，因為未指定預設的擷取模式

空的 Lambda 運算式擷取 `[]`，指定 Lambda 運算式不明確或隱含擷取任何變數。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 提供預設的擷取模式，或

- 明確擷取一或多個變數。

## <a name="example"></a>範例

下例會產生 C3493，因為它會修改外部變數，但指定空白的擷取子句：

```
// C3493a.cpp

int main()
{
   int m = 55;
   [](int n) { m = n; }(99); // C3493
}
```

## <a name="example"></a>範例

下例會以依參考指定為預設擷取模式的方式解析 C3493。

```
// C3493b.cpp

int main()
{
   int m = 55;
   [&](int n) { m = n; }(99);
}
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)