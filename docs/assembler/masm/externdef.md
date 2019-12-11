---
title: EXTERNDEF
ms.date: 12/06/2019
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: e757781151bd1bb57940e5c54f7333a5daa93c74
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987891"
---
# <a name="externdef"></a>EXTERNDEF

定義一或多*個名為 type 類型的外部*變數、標籤或*符號。*

## <a name="syntax"></a>語法

> **EXTERNDEF** ⟦*language-類型*⟧*名稱* __：__ *類型*⟦ __，__ ⟦*語言類型*⟧*名稱* __：__ *類型*.。。⟧

## <a name="remarks"></a>備註

*Language 類型*引數只在32位 MASM 中有效。

如果*名稱*是在模組中定義，則會被視為[公用](../../assembler/masm/public-masm.md)。 如果在模組中參考*名稱*，則會將它視為[EXTERN](../../assembler/masm/extern-masm.md)。 如果未參考*name* ，則會忽略它。 *類型*可以是[ABS](../../assembler/masm/operator-abs.md)，其會將*名稱*當做常數來匯入。 通常用於 include 檔案中。

## <a name="see-also"></a>請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)
