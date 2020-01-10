---
title: ALIGN (MASM)
ms.date: 12/17/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: 700721768deaf92e88b32a97e68c6e017219d19d
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316586"
---
# <a name="align"></a>ALIGN

**ALIGN**指示詞會將下一個資料元素或指示對齊其參數的倍數的位址。 參數必須是小於或等於區段對齊的2（例如，1、2、4等等）的乘冪。

## <a name="syntax"></a>語法

> **ALIGN** ⟦*constantExpression*⟧

## <a name="remarks"></a>備註

**ALIGN**指示詞可讓您指定資料元素或指令的開始位移。 對齊的資料可以改善效能，代價是在資料元素之間浪費空間。 當資料存取位於符合快取行的界限時，可能會出現大量效能改進。 針對原生類型的自然界限存取，表示在內部硬體校準微碼中花費的時間較少。

在使用一般定址模型的新式處理器上，不太需要對齊的指示，但可能需要在較舊的程式碼中針對其他定址模型進行跳躍目標。

當資料對齊時，略過的空間會以零填補。 當指示對齊時，略過的空間會填入適當大小的 NOP 指示。

## <a name="see-also"></a>請參閱

[甚至](even.md)\
指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
