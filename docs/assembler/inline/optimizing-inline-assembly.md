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
ms.openlocfilehash: d4956ba12e0bc268d78a895e6cb1ec6e2059262a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538862"
---
# <a name="optimizing-inline-assembly"></a>最佳化內嵌組譯碼

**Microsoft 專屬**

函式中若存在 `__asm` 區塊，則會透過多種方式影響最佳化。 首先，編譯器不會嘗試最佳化 `__asm` 區塊本身。 您在組合語言中撰寫的內容即會與取得的內容完全相同。 其次，`__asm` 區塊會影響暫存器變數儲存區。 如果 `__asm` 區塊可能會變更暫存器的內容，則編譯器會避免跨 `__asm` 區塊註冊這些變數。 最後，其他函式最佳化會受到函式中包含的組合語言所影響。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[內嵌組合語言](../../assembler/inline/inline-assembler.md)<br/>