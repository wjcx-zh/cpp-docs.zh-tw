---
title: 編譯器警告 (層級 4) C4434
ms.date: 11/04/2016
f1_keywords:
- C4434
helpviewer_keywords:
- C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
ms.openlocfilehash: 97a010bef151e97914d131b3a1fe2437a244e9c4
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683208"
---
# <a name="compiler-warning-level-4-c4434"></a>編譯器警告 (層級 4) C4434

類別的函式必須具有私用存取範圍;變更為私用存取

C4434 表示編譯器已變更靜態函式的存取範圍。 靜態的函式必須具有私用存取範圍，因為它們只適用于通用語言執行時間呼叫。 如需詳細資訊，請參閱[靜態](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors)的函式。

## <a name="example"></a>範例

下列範例會產生 C4434。

```cpp
// C4434.cpp
// compile with: /W4 /c /clr
public ref struct R {
   static R(){}   // C4434
};
```