---
title: 編譯器警告 （層級 1） C4688 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4688
dev_langs:
- C++
helpviewer_keywords:
- C4688
ms.assetid: a027df3c-b2b8-4c49-8539-c2bc42db74e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aff10e34fd2dde20059ccbe2845b199486beb865
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027826"
---
# <a name="compiler-warning-level-1-c4688"></a>編譯器警告 (層級 1) C4688

'constraint': 條件約束清單含有組件私用類型 'type'，將無法由組件外部存取

條件約束清單具有組件的私用類型，這表示在組件外部存取類型時將無法使用它。 如需詳細資訊，請參閱[泛型](../../windows/generics-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C4688。

```
// C4688.cpp
// compile with: /clr /c /W1
ref struct A {};   // private type
public ref struct B {};

// Delete the following 3 lines to resolve.
generic <class T>
where T : A   // C4688
public ref struct M {};

generic <class T>
where T : B
public ref struct N {};
```