---
title: 編譯器錯誤 C3484 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3484
dev_langs:
- C++
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19a79574f85d05c6b1ac32416509ba1f8c05e26b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019182"
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