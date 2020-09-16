---
title: 編譯器錯誤 C3480
ms.date: 11/04/2016
f1_keywords:
- C3480
helpviewer_keywords:
- C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
ms.openlocfilehash: a2fa1a8b02cf05d332210f359ae3ff33ed7d6e35
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686302"
---
# <a name="compiler-error-c3480"></a>編譯器錯誤 C3480

'var': Lambda 擷取變數必須來自封入函式範圍

Lambda 擷取變數不是來自封入函式範圍。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 請從 Lambda 運算式的擷取清單移除變數。

## <a name="examples"></a>範例

下列範例會產生 C3480，因為變數 `global` 不是來自封入函式範圍：

```cpp
// C3480a.cpp

int global = 0;
int main()
{
   [&global] { global = 5; }(); // C3480
}
```

下列範例會藉由從 Lambda 運算式的擷取清單移除變數 `global` 而解決 C3480：

```cpp
// C3480b.cpp

int global = 0;
int main()
{
   [] { global = 5; }();
}
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
