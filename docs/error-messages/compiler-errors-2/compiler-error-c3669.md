---
title: 編譯器錯誤 C3669
ms.date: 11/04/2016
f1_keywords:
- C3669
helpviewer_keywords:
- C3669
ms.assetid: be9c7ae4-e96f-47ab-922a-39a3537d5ca6
ms.openlocfilehash: 3b0ad3aa7395f5f423c8c36f547d4a0e2ad792c1
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58777099"
---
# <a name="compiler-error-c3669"></a>編譯器錯誤 C3669

'member': 覆寫的規範 'override' 不允許靜態成員函式或建構函式

覆寫指定不正確。 如需詳細資訊，請參閱 <<c0> [ 明確覆寫](../../extensions/explicit-overrides-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3669。

```
// C3669.cpp
// compile with: /clr
public ref struct R {
   R() override {}   // C3669
};
```