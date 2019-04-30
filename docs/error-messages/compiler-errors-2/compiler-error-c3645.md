---
title: 編譯器錯誤 C3645
ms.date: 11/04/2016
f1_keywords:
- C3645
helpviewer_keywords:
- C3645
ms.assetid: 346da528-ae86-4cd0-9654-f41bee26ac0d
ms.openlocfilehash: f733de6920e00f1f53c87884a7a334e575bceb06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385780"
---
# <a name="compiler-error-c3645"></a>編譯器錯誤 C3645

'function': __clrcall 不可使用於編譯為原生程式碼的函式

函式中的某些關鍵字將導致編譯成原生函式。

## <a name="example"></a>範例

下列範例會產生 C3645。

```
// C3645.cpp
// compile with: /clr /c
#pragma unmanaged
int __clrcall dog() {}   // C3645
```