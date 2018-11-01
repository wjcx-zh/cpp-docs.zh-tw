---
title: EXTERN (MASM)
ms.date: 08/30/2018
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 30d1b3ae7c6676aeb97b91c7627da859525b9ce1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497353"
---
# <a name="extern-masm"></a>EXTERN (MASM)

定義一或多個外部變數、 標籤或呼叫的符號*名稱*其型別的*型別*。

## <a name="syntax"></a>語法

> EXTERN [[*langtype*]]*名稱*[[(*altid*)]]:*類型*[[，[[*langtype*]] *名稱*[[(*altid*)]]:*類型*]]...

## <a name="remarks"></a>備註

*型別*可以是[ABS](../../assembler/masm/operator-abs.md)，會匯入*名稱*做為常數。 與相同[EXTRN](../../assembler/masm/extrn.md)。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>