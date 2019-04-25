---
title: 內嵌組譯碼中的類型和變數大小
ms.date: 08/30/2018
ms.topic: reference
f1_keywords:
- length
- Type
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
ms.openlocfilehash: 36c97ee866ca449e9bbcf514e464a13f24f12cd9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166889"
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>內嵌組譯碼中的類型和變數大小

**Microsoft 專屬**

**長度**，**大小**，並**型別**運算子在內嵌組譯碼中具有受限的意義。 這些運算子完全無法搭配 `DUP` 運算子使用 (因為您無法使用 MASM 指示詞或運算子定義資料)。 但是，您可以使用這些運算子尋找 C 或 C++ 變數或類型的大小：

- **長度**運算子可以傳回陣列中的項目數目。 它會針對非陣列變數傳回數值 1。

- **大小**運算子可以傳回 C 的大小或C++變數。 變數的大小是乘積及其**長度**並**型別**。

- **型別**運算子可以傳回 C 的大小或C++類型或變數。 如果變數是陣列，**型別**傳回的單一元素陣列的大小。

例如，如果您的程式具有 8 個元素**int**陣列，

```cpp
int arr[8];
```

下列 C 和組譯碼運算式會產生 `arr` 及其元素的大小。

|__asm|C|大小|
|-------------|-------|----------|
|**長度**arr|`sizeof`(arr)/`sizeof`(arr[0])|8|
|**大小**arr|`sizeof`(arr)|32|
|**型別**arr|`sizeof`(arr[0])|4|

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>