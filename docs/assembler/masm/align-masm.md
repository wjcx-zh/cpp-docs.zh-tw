---
title: ALIGN (MASM)
ms.date: 01/02/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: 22b18f2e238c780377b84fc2be3eb6678686bb73
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399278"
---
# <a name="align-masm"></a>ALIGN (MASM)

**ALIGN**指示詞會將下一個資料元素或指示對齊其參數的倍數的位址。 參數必須是小於或等於區段對齊的2（例如，1、2、4等等）的乘冪。

## <a name="syntax"></a>語法

> **對齊**⟦*數位*⟧

## <a name="remarks"></a>備註

**ALIGN**指示詞可讓您指定資料元素或指令的開始位移。 對齊的資料可以改善效能，代價是在資料元素之間浪費空間。 當資料存取位於符合快取行的界限時，可能會出現大量效能改進。 針對原生類型的自然界限存取，表示在內部硬體校準微碼中花費的時間較少。

在使用一般定址模型的新式處理器上，不太需要對齊的指示，但可能需要在較舊的程式碼中針對其他定址模型進行跳躍目標。

當資料對齊時，略過的空間會以零填補。 當指示對齊時，略過的空間會填入適當大小的 NOP 指示。

## <a name="see-also"></a>另請參閱

[甚至](even.md)\
[指示詞參考](directives-reference.md)
