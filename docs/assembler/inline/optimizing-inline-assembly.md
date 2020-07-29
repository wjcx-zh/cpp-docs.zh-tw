---
title: 最佳化內嵌組譯碼
ms.date: 08/30/2018
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
ms.openlocfilehash: a558761ff49c2b508a5bad6172cda2283801e30e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191725"
---
# <a name="optimizing-inline-assembly"></a>最佳化內嵌組譯碼

**Microsoft 特定的**

函式中的 **`__asm`** 區塊存在會以數種方式影響優化。 首先，編譯器不會嘗試將 **`__asm`** 區塊本身優化。 您在組合語言中撰寫的內容即會與取得的內容完全相同。 第二，區塊的存在 **`__asm`** 會影響暫存器變數存放裝置。 如果區塊會變更暫存器的內容，則編譯器會避免在區塊間 enregistering 變數 **`__asm`** **`__asm`** 。 最後，其他函式最佳化會受到函式中包含的組合語言所影響。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[內嵌組譯工具](../../assembler/inline/inline-assembler.md)<br/>
