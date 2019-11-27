---
title: EXTERN (MASM)
ms.date: 08/30/2018
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: fc66338d90b54ecb12ef3ab1aa56214fb445cb13
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397558"
---
# <a name="extern-masm"></a>EXTERN (MASM)

定義一或多*個名為 type 類型的外部*變數、標籤或*符號。*

## <a name="syntax"></a>語法

> **EXTERN** ⟦*language type*⟧ *name* ⟦ __（__ *altid* __）__ ⟧ __：__ *type* ⟦ __，__ ⟦*language-type*⟧ *name* ⟦ __（__ *altid* __）__ ⟧ __：__ *type* .。。⟧

## <a name="remarks"></a>備註

*類型*可以是[ABS](../../assembler/masm/operator-abs.md)，其會將*名稱*當做常數來匯入。 與[EXTRN](../../assembler/masm/extrn.md)相同。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)
