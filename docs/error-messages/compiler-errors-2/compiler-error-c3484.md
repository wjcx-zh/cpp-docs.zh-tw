---
title: 編譯器錯誤 C3484
ms.date: 11/04/2016
f1_keywords:
- C3484
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
ms.openlocfilehash: ded4a183f69e4903afb4c9dfeae22f7751ef76ad
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686276"
---
# <a name="compiler-error-c3484"></a>編譯器錯誤 C3484

傳回類型的前面必須是 '->'

Lambda 運算式的傳回類型前面必須是 `->` 。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 傳回類型前面請提供 `->` 。

## <a name="examples"></a>範例

下列範例會產生 C3484：

```cpp
// C3484a.cpp

int main()
{
   return []() . int { return 42; }(); // C3484
}
```

下例藉由在 Lambda 運算式的傳回類型前面提供 `->` 來解決 C3484：

```cpp
// C3484b.cpp

int main()
{
   return []() -> int { return 42; }();
}
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
