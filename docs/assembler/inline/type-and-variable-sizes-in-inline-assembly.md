---
title: 內嵌組譯碼中的類型和變數大小
ms.date: 08/30/2018
ms.topic: reference
helpviewer_keywords:
- variables, length
- size, getting in inline assembly
- size
- LENGTH operator
- TYPE operator
- SIZE operator
- inline assembly, operators
- variables, type
- variables, size
ms.assetid: b62c2f2b-a7ad-4145-bae4-d890db86d348
ms.openlocfilehash: 3e244aaa8ea849b558b77c3f1569820079f6f76c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191608"
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>內嵌組譯碼中的類型和變數大小

**Microsoft 特定的**

[**長度**]、[**大小**] 和 [**類型**] 運算子在內嵌組解碼中具有有限的意義。 這些運算子完全無法搭配 `DUP` 運算子使用 (因為您無法使用 MASM 指示詞或運算子定義資料)。 但是，您可以使用這些運算子尋找 C 或 C++ 變數或類型的大小：

- **LENGTH**運算子可以傳回陣列中的元素數目。 它會針對非陣列變數傳回數值 1。

- **Size**運算子可以傳回 C 或 c + + 變數的大小。 變數的大小是其**長度**和**類型**的乘積。

- **Type**運算子可以傳回 C 或 c + + 類型或變數的大小。 如果變數是陣列，則**類型**會傳回陣列中單一元素的大小。

例如，如果您的程式具有8個元素的 **`int`** 陣列，

```cpp
int arr[8];
```

下列 C 和組譯碼運算式會產生 `arr` 及其元素的大小。

|__asm|C|大小|
|-------------|-------|----------|
|**長度**arr|`sizeof(arr)/sizeof(arr[0])`|8|
|**大小**arr|`sizeof(arr)`|32|
|**輸入**arr|`sizeof(arr[0])`|4|

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用元件語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
