---
title: 編譯器錯誤 C3483 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3483
dev_langs:
- C++
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: decc04f25689b24c560f59a71fd22a9708754352
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091682"
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