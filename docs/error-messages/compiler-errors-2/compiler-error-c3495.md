---
title: 編譯器錯誤 C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: a67d4d859e3a9dd2241f14a476492df0fd3e6b8d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223417"
---
# <a name="compiler-error-c3495"></a>編譯器錯誤 C3495

'var': Lambda 擷取必須有自動儲存期

您無法捕捉不具有自動儲存期的變數，例如標示為或的變數 **`static`** **`extern`** 。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 請勿將 **`static`** 或變數傳遞 **`extern`** 至 lambda 運算式的 capture 清單。

## <a name="example"></a>範例

下列範例會產生 C3495，因為 **`static`** 變數 `n` 會出現在 lambda 運算式的 capture 清單中：

```cpp
// C3495.cpp

int main()
{
   static int n = 66;
   [&n]() { return n; }(); // C3495
}
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
