---
title: conform
ms.date: 11/04/2016
f1_keywords:
- conform_CPP
- vc-pragma.conform
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
ms.openlocfilehash: 35c3b06106779a9056f682ff76c6ed4b4ab1ab41
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366755"
---
# <a name="conform"></a>conform
**C++特定**

指定的執行階段行為[/zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)編譯器選項。

## <a name="syntax"></a>語法

> **#pragma conform(** *name* [**, show** ] [**,** { **on** | **off** } ] [ [**,** { **push** | **pop** } ] [**,** *identifier* ] ] **)**

### <a name="parameters"></a>參數

*name*<br/>
指定要修改的編譯器選項名稱。 唯一有效*名稱*是`forScope`。

**show**<br/>
（選擇性）導致目前的設定*名稱*（true 或 false），在編譯期間透過警告訊息顯示。 例如， `#pragma conform(forScope, show)` 。

**在 **，**關閉**<br/>
（選擇性）設定*名稱*要**上**讓[/zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)編譯器選項。 預設值是**關閉**。

**push**<br/>
（選擇性）將推入的目前值*名稱*至內部編譯器堆疊。 如果您指定*識別碼*，您可以指定**上**或是**關閉**值*名稱*推送至堆疊。 例如， `#pragma conform(forScope, push, myname, on)` 。

**pop**<br/>
（選擇性）設定的值*名稱*頂端的內部編譯器堆疊，然後從堆疊中推出的值。 如果指定的識別項，但**pop**，將會推出堆疊，直到它找到的記錄*識別項*，這也會從; 的目前值*名稱*中在堆疊上的下一筆記錄會變成的新值*名稱*。 如果您指定**pop**具有*識別項*不在堆疊上，記錄**pop**會被忽略。

*identifier*<br/>
（選擇性）可以是隨附**推播**或是**pop**命令。 如果*識別碼*使用時，則**上**或是**關閉**規範也可以使用。

## <a name="example"></a>範例

```cpp
// pragma_directive_conform.cpp
// compile with: /W1
// C4811 expected
#pragma conform(forScope, show)
#pragma conform(forScope, push, x, on)
#pragma conform(forScope, push, x1, off)
#pragma conform(forScope, push, x2, off)
#pragma conform(forScope, push, x3, off)
#pragma conform(forScope, show)
#pragma conform(forScope, pop, x1)
#pragma conform(forScope, show)

int main() {}
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)