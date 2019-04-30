---
title: 編譯器錯誤 C3484
ms.date: 11/04/2016
f1_keywords:
- C3484
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
ms.openlocfilehash: c4405eb81911b1081d19d25ba779d24bee8f6d37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381263"
---
# <a name="compiler-error-c3484"></a>編譯器錯誤 C3484

傳回類型的前面必須是 '->'

Lambda 運算式的傳回類型前面必須是 `->` 。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 傳回類型前面請提供 `->` 。

## <a name="example"></a>範例

下列範例會產生 C3484：

```
// C3484a.cpp

int main()
{
   return []() . int { return 42; }(); // C3484
}
```

## <a name="example"></a>範例

下例藉由在 Lambda 運算式的傳回類型前面提供 `->` 來解決 C3484：

```
// C3484b.cpp

int main()
{
   return []() -> int { return 42; }();
}
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)