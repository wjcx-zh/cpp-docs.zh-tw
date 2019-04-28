---
title: 編譯器錯誤 C3388
ms.date: 11/04/2016
f1_keywords:
- C3388
helpviewer_keywords:
- C3388
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
ms.openlocfilehash: 3b56aae115b1a1721f3f8a8688e36b25edc7f33f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328727"
---
# <a name="compiler-error-c3388"></a>編譯器錯誤 C3388

'type': 不允許作為條件約束，假設是 'ref class' 以繼續剖析

已在泛型類型上指定條件約束，但未正確地指定條件約束。 請參閱[泛型類型參數的條件約束 (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C3388。

```
// C3388.cpp
// compile with: /clr /c
interface class AA {};

generic <class T>
where T : interface class   // C3388
ref class C {};

// OK
generic <class T>
where T : AA
ref class D {};
```