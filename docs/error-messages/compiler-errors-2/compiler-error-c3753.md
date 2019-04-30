---
title: 編譯器錯誤 C3753
ms.date: 11/04/2016
f1_keywords:
- C3753
helpviewer_keywords:
- C3753
ms.assetid: a5b99e28-796c-4107-a673-97c2ae3bb2b9
ms.openlocfilehash: 7c9c078e72babc85dc7092b8d6414625e9c0db7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410469"
---
# <a name="compiler-error-c3753"></a>編譯器錯誤 C3753

不允許泛型屬性

泛型參數清單只能出現在受管理的類別、 結構或函式。

如需詳細資訊，請參閱 <<c0> [ 泛型](../../extensions/generics-cpp-component-extensions.md)並[屬性](../../extensions/property-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3753。

```
// C3753.cpp
// compile with: /clr /c
ref struct A {
   generic <typename T>
   property int i;   // C3753 error
};
```