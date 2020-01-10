---
title: conform pragma
ms.date: 08/29/2019
f1_keywords:
- conform_CPP
- vc-pragma.conform
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
ms.openlocfilehash: 816ff85bb19f549c6ea072073bd89fcd503545f2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220494"
---
# <a name="conform-pragma"></a>conform pragma

**C++特殊**

指定[/zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)編譯器選項的執行時間行為。

## <a name="syntax"></a>語法

> **#pragma 符合 (** *name* [ **, show** ] [ **,** { **on**  |  **off** }] [[ **,** { **push**  |  **pop** }] [ **,** *identifier* [ **,** { **on** **off}** ]  | ] ] **)**

### <a name="parameters"></a>參數

*檔案名*\
指定要修改的編譯器選項名稱。 唯一有效的*名稱*是`forScope`。

**出現**\
選擇性導致在編譯期間以警告訊息來顯示*名稱*(true 或 false) 的目前設定。 例如： `#pragma conform(forScope, show)` 。

**開啟**、**關閉**\
選擇性將 [*名稱*] 設定為**on 時**, 會啟用[/zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)編譯器選項。 預設值為**off**。

**式**\
選擇性將*名稱*的目前值推送至內部編譯器堆疊。 如果您指定 [*識別碼*], 您可以指定 [開啟] 或 [**關閉**] 值, 以將其推送到堆疊**上**。 例如： `#pragma conform(forScope, push, myname, on)` 。

**提示**\
選擇性將 [*名稱*] 的值設定為內部編譯器堆疊頂端的值, 然後彈出堆疊。 如果指定了識別碼與**pop**, 堆疊就會快顯回來, 直到找到具有*識別碼*的記錄 (也會將它快顯) 為止。堆疊上下一筆記錄中的 [*名稱*] 目前值會變成 [*名稱*] 的新值。 如果您指定的**pop** *識別碼*不在堆疊的記錄中, 則會忽略**pop** 。

*標識*\
選擇性可以包含在**push**或**pop**命令中。 如果使用了*identifier* , 則也可以使用**on**或**off**規範。

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

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
