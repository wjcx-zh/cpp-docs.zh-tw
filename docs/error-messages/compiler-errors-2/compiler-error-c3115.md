---
title: 編譯器錯誤 C3115
ms.date: 11/04/2016
f1_keywords:
- C3115
helpviewer_keywords:
- C3115
ms.assetid: 51726145-9782-4ec9-84b9-286f366d9cbd
ms.openlocfilehash: e334836986548d4f854dd9a5760bd8315b769d03
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520493"
---
# <a name="compiler-error-c3115"></a>編譯器錯誤 C3115

'attribute': 'construct' 上不允許此屬性

已套用到未預期的建構函式。  請參閱[屬性的用法](../../windows/attributes/attributes-by-usage.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C3115。

```
// C3115.cpp
// compile with: /c
#include <unknwn.h>
[module(name="xx")];

[object, helpstringdll(xx.dll), uuid("00000000-0000-0000-0000-000000000001")]   // C3115
// try the following line instead
// [object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI {
   HRESULT xx();
};
```