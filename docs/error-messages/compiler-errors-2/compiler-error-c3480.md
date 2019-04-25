---
title: 編譯器錯誤 C3480
ms.date: 11/04/2016
f1_keywords:
- C3480
helpviewer_keywords:
- C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
ms.openlocfilehash: 2ebcce496fd06c30420558d80cc0a0c9318d4376
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173412"
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