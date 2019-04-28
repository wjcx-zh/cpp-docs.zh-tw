---
title: 編譯器錯誤 C3400
ms.date: 11/04/2016
f1_keywords:
- C3400
helpviewer_keywords:
- C3400
ms.assetid: d44169a8-73b6-4766-b406-b3a6c93f2a4d
ms.openlocfilehash: c4b4cb64da83115ab5b6a5234cda2ea3c7ba3a53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300371"
---
# <a name="compiler-error-c3400"></a>編譯器錯誤 C3400

循環條件約束相依性，涉及 'constraint_1' 和 'constraint_2'

編譯器偵測到循環條件約束。

如需詳細資訊，請參閱 <<c0> [ 泛型類型參數的條件約束 (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)。</c0>

## <a name="example"></a>範例

下列範例會產生 C3400。

```
// C3400.cpp
// compile with: /clr /c
generic<class T, class U>
where T : U
where U : T   // C3400
public ref struct R {};
```