---
title: EXTERN (MASM)
ms.date: 12/06/2019
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 38ea50e75f2a8e19a7a99860f691904053b6739a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987849"
---
# <a name="extern-masm"></a>EXTERN (MASM)

定義一或多*個名為 type 類型的外部*變數、標籤或*符號。*

## <a name="syntax"></a>語法

> **EXTERN** ⟦*language type*⟧ *name* ⟦ __（__ *altid* __）__ ⟧ __：__ *type* ⟦ __，__ ⟦*language-type*⟧ *name* ⟦ __（__ *altid* __）__ ⟧ __：__ *type* .。。⟧

## <a name="remarks"></a>備註

*Language 類型*引數只在32位 MASM 中有效。

*類型*可以是[ABS](../../assembler/masm/operator-abs.md)，其會將*名稱*當做常數來匯入。 與[EXTRN](../../assembler/masm/extrn.md)相同。

## <a name="see-also"></a>請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)
