---
title: 編譯器錯誤 C3084
ms.date: 11/04/2016
f1_keywords:
- C3084
helpviewer_keywords:
- C3084
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
ms.openlocfilehash: 337cd7f37bf94c7a3d5cffe6b167d4661e3b0a81
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751452"
---
# <a name="compiler-error-c3084"></a>編譯器錯誤 C3084

'function': 完成項/解構函式不能是 'keyword'

不正確地宣告完成項或解構函式。

例如，解構函式不應該標示為密封。  衍生類型將無法存取解構函式。  如需詳細資訊，請參閱[如何：定義和使用類別和結構（C++/cli）中](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)的[明確覆寫](../../extensions/explicit-overrides-cpp-component-extensions.md)和析構函式和完成項。

## <a name="example"></a>範例

下列範例會產生 C3084。

```cpp
// C3084.cpp
// compile with: /clr /c
ref struct R {
protected:
   !R() sealed;   // C3084
   !R() abstract;   // C3084
   !R();
};
```
