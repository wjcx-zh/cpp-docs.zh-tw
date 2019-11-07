---
title: .REPEAT
ms.date: 11/05/2019
f1_keywords:
- .REPEAT
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
ms.openlocfilehash: 0533397c60c83f22b10c84ec72aa6eb65a71e4c0
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703562"
---
# <a name="repeat-32-bit-masm"></a>.重複（32位 MASM）

產生會重複執行*語句*區塊的程式碼，直到 `condition` 變成 true 為止。 [.UNTILCXZ](../../assembler/masm/dot-untilcxz.md)，如果 CX 為零，則可替代[。直到](../../assembler/masm/dot-until.md)。 `condition` 在中是選擇性的 **.UNTILCXZ**。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> .REPEAT<br/>
> 陳述式<br/>
> .UNTIL 條件

## <a name="see-also"></a>請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>