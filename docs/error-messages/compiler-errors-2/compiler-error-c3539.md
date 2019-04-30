---
title: 編譯器錯誤 C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: be1051859ebbcbdc22a9b71f8c5adba2e75c4e92
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344653"
---
# <a name="compiler-error-c3539"></a>編譯器錯誤 C3539

'type': 樣板引數不能包含 'auto' 的類型

指定的範本引數類型不能包含的使用方式的`auto`關鍵字。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 未指定樣板引數與`auto`關鍵字。

## <a name="example"></a>範例

下列範例會產生 C3539。

```
// C3539.cpp
// Compile with /Zc:auto
template<class T> class C{};
int main()
{
   C<auto> c;   // C3539
   return 0;
}
```

## <a name="see-also"></a>另請參閱

[auto 關鍵字](../../cpp/auto-keyword.md)