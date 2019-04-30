---
title: 編譯器警告 (層級 4) C4434
ms.date: 11/04/2016
f1_keywords:
- C4434
helpviewer_keywords:
- C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
ms.openlocfilehash: 6a7d760a7d192c7e0a7bd5e16f77efe1a4099c31
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391487"
---
# <a name="compiler-warning-level-4-c4434"></a>編譯器警告 (層級 4) C4434

類別建構函式必須有私用存取範圍;變更為私用存取

C4434 會指示編譯器變更的靜態建構函式的存取範圍。 靜態建構函式必須有私用存取範圍，因為它們只是由通用語言執行平台呼叫。 如需詳細資訊，請參閱 <<c0> [ 靜態建構函式](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors)。

## <a name="example"></a>範例

下列範例會產生 C4434。

```
// C4434.cpp
// compile with: /W4 /c /clr
public ref struct R {
   static R(){}   // C4434
};
```