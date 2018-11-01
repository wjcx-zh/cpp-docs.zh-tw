---
title: 編譯器錯誤 C3483
ms.date: 11/04/2016
f1_keywords:
- C3483
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
ms.openlocfilehash: c958eee234d25b008eb8cb03f40b45b8aaba81a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573455"
---
# <a name="compiler-error-c3483"></a>編譯器錯誤 C3483

'var' 已是 Lambda 擷取清單的一部分

您已多次傳遞相同的變數給 Lambda 運算式的擷取清單。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 請從擷取清單移除變數的所有其他執行個體。

## <a name="example"></a>範例

下列範例會產生 C3483，因為 `n` 變數多次出現在 Lambda 運算式的擷取清單中：

```
// C3483.cpp

int main()
{
   int m = 6, n = 5;
   [m,n,n] { return n + m; }(); // C3483
}
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)