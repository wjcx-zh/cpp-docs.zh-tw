---
title: 編譯器錯誤 C3480
ms.date: 11/04/2016
f1_keywords:
- C3480
helpviewer_keywords:
- C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
ms.openlocfilehash: 255fb12d587a94aac798814736f0b26770f608b0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760474"
---
# <a name="compiler-error-c3480"></a>編譯器錯誤 C3480

'var': Lambda 擷取變數必須來自封入函式範圍

Lambda 擷取變數不是來自封入函式範圍。

### <a name="to-correct-this-error"></a>若要改正這項錯誤

- 請從 Lambda 運算式的擷取清單移除變數。

## <a name="example"></a>範例

下列範例會產生 C3480，因為變數 `global` 不是來自封入函式範圍：

```cpp
// C3480a.cpp

int global = 0;
int main()
{
   [&global] { global = 5; }(); // C3480
}
```

## <a name="example"></a>範例

下列範例會藉由從 Lambda 運算式的擷取清單移除變數 `global` 而解決 C3480：

```cpp
// C3480b.cpp

int global = 0;
int main()
{
   [] { global = 5; }();
}
```

## <a name="see-also"></a>請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
