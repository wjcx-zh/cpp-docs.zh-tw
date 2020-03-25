---
title: 編譯器警告 (層級 1) C4688
ms.date: 11/04/2016
f1_keywords:
- C4688
helpviewer_keywords:
- C4688
ms.assetid: a027df3c-b2b8-4c49-8539-c2bc42db74e8
ms.openlocfilehash: e7aebfa3ae602aa45c02897711cd94520a876cca
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175398"
---
# <a name="compiler-warning-level-1-c4688"></a>編譯器警告 (層級 1) C4688

'constraint': 條件約束清單含有組件私用類型 'type'，將無法由組件外部存取

條件約束清單具有組件的私用類型，這表示在組件外部存取類型時將無法使用它。 如需詳細資訊，請參閱[泛型](../../extensions/generics-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C4688。

```cpp
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
