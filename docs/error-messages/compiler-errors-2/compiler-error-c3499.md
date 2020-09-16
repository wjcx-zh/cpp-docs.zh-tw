---
title: 編譯器錯誤 C3499
ms.date: 11/04/2016
f1_keywords:
- C3499
helpviewer_keywords:
- C3499
ms.assetid: 6717de5c-ae0f-4024-bdf2-b5598009e7b6
ms.openlocfilehash: b49c868b696df75a5b5148d32fb286019c6293e4
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686132"
---
# <a name="compiler-error-c3499"></a>編譯器錯誤 C3499

已被指定為具有 void 傳回類型的 Lambda 無法傳回值

當指定為傳回類型的 lambda 運算式傳回值時， **`void`** 或當 lambda 運算式包含一個以上的語句並傳回值，但未指定其傳回型別時，編譯器會產生這個錯誤。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 不要從 Lambda 運算式傳回值，或者，

- 提供 Lambda 運算式的傳回類型，或者，

- 將組成 Lambda 運算式主體的多個陳述式合併為單一陳述式。

## <a name="examples"></a>範例

下列範例會產生 C3499，因為 Lambda 運算式的主體包含多個陳述式並傳回值，但 Lambda 運算式未指定傳回類型：

```cpp
// C3499a.cpp

int main()
{
   [](int x) { int n = x * 2; return n; } (5); // C3499
}
```

下列範例顯示 C3499 的兩種可能解決方式。 第一個解決方式是提供 Lambda 運算式的傳回類型。 第二個解決方式是將組成 Lambda 運算式主體的多個陳述式合併為單一陳述式。

```cpp
// C3499b.cpp

int main()
{
   // Possible resolution 1:
   // Provide the return type of the lambda expression.
   [](int x) -> int { int n = x * 2; return n; } (5);

   // Possible resolution 2:
   // Combine the statements that make up the body of
   // the lambda expression into a single statement.
   [](int x) { return x * 2; } (5);
}
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
