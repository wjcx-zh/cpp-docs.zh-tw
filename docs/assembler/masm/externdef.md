---
title: EXTERNDEF
ms.date: 12/06/2019
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 2cc5884a7473da9175a6b6af4b4251314deffeb4
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75313388"
---
# <a name="externdef"></a>EXTERNDEF

定義一或多*個名為 type 類型的外部*變數、標籤或*符號。*

## <a name="syntax"></a>語法

> **EXTERNDEF** ⟦*language-類型*⟧*名稱* __：__ *類型*⟦ __，__ ⟦*語言類型*⟧*名稱* __：__ *類型*.。。⟧

## <a name="remarks"></a>備註

*Language 類型*引數只在32位 MASM 中有效。

如果*名稱*是在模組中定義，則會被視為[公用](public-masm.md)。 如果在模組中參考*名稱*，則會將它視為[EXTERN](extern-masm.md)。 如果未參考*name* ，則會忽略它。 *類型*可以是[ABS](operator-abs.md)，其會將*名稱*當做常數來匯入。 通常用於 include 檔案中。

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
