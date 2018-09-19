---
title: 編譯器錯誤 C3480 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3480
dev_langs:
- C++
helpviewer_keywords:
- C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fd58a8c38ee6dc5f77ef280ba3b7a546a666cd6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107853"
---
# <a name="compiler-error-c3480"></a>編譯器錯誤 C3480

'var': Lambda 擷取變數必須來自封入函式範圍

Lambda 擷取變數不是來自封入函式範圍。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 請從 Lambda 運算式的擷取清單移除變數。

## <a name="example"></a>範例

下列範例會產生 C3480，因為變數 `global` 不是來自封入函式範圍：

```
// C3480a.cpp

int global = 0;
int main()
{
   [&global] { global = 5; }(); // C3480
}
```

## <a name="example"></a>範例

下列範例會藉由從 Lambda 運算式的擷取清單移除變數 `global` 而解決 C3480：

```
// C3480b.cpp

int global = 0;
int main()
{
   [] { global = 5; }();
}
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)