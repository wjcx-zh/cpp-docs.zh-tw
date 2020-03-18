---
title: EXTERN (MASM)
ms.date: 12/06/2019
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 2674f358fe22f74c5272d90a0d8cbff234ddcd11
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440879"
---
# <a name="extern"></a>EXTERN

定義一或多*個名為 type 類型的外部*變數、標籤或*符號。*

## <a name="syntax"></a>語法

> **EXTERN** ⟦*language type*⟧ *name* ⟦ __（__ *altid* __）__ ⟧ __：__ *type* ⟦ __，__ ⟦*language-type*⟧ *name* ⟦ __（__ *altid* __）__ ⟧ __：__ *type* .。。⟧

## <a name="remarks"></a>備註

*Language 類型*引數只在32位 MASM 中有效。

*類型*可以是[ABS](operator-abs.md)，其會將*名稱*當做常數來匯入。 與[EXTRN](extrn.md)相同。

## <a name="see-also"></a>另請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
