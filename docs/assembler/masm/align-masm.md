---
title: ALIGN (MASM)
ms.date: 01/02/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: eb42b1952b3fd59438f0dd4c29d48c91c4d8864d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166473"
---
# <a name="align-masm"></a>ALIGN (MASM)

**對齊**下一步 的資料元素或其參數的多個位址上的指示，指示詞對齊。 參數必須是 2 的乘冪 （例如 1、 2、 4 和等等） 也就是小於或等於區段的對齊方式。

## <a name="syntax"></a>語法

> 對齊 [[*數字*]]

## <a name="remarks"></a>備註

**對齊**指示詞可讓您指定的資料元素或指令的開始位移。 對齊的資料可以改善效能，但代價是浪費掉的空間資料的項目之間。 資料存取時放入快取行內的界限上可以看到效能大幅提升。 原生類型的自然界限存取表示花費在記憶體內部硬體重新對齊微碼較少時間。

如需對齊的指示需要很少會在新型處理器使用一般的定址模型時，但在較舊程式碼中其他定址模型可能需要針對跳躍的目標上。

當資料對齊時，略過的空間將填滿零。 當指示對齊時，略過的空間填滿適當地調整大小 NOP 指示。

## <a name="see-also"></a>另請參閱

[EVEN](even.md)<br/>
[指示詞參考](../../assembler/masm/directives-reference.md)<br/>