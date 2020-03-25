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
ms.openlocfilehash: 0051b16ddc19e233cfac2688c0b77e1e023f0833
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169262"
---
# <a name="optimizing-inline-assembly"></a>最佳化內嵌組譯碼

**Microsoft 專屬**

函式中若存在 `__asm` 區塊，則會透過多種方式影響最佳化。 首先，編譯器不會嘗試最佳化 `__asm` 區塊本身。 您在組合語言中撰寫的內容即會與取得的內容完全相同。 其次，`__asm` 區塊會影響暫存器變數儲存區。 如果 `__asm` 區塊可能會變更暫存器的內容，則編譯器會避免跨 `__asm` 區塊註冊這些變數。 最後，其他函式最佳化會受到函式中包含的組合語言所影響。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[內嵌組合語言](../../assembler/inline/inline-assembler.md)<br/>
