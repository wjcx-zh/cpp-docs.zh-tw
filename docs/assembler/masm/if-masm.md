---
title: IF (MASM)
ms.date: 12/17/2019
f1_keywords:
- if
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: 38d366a3a41e7b08759594899cdcbb2cb84dfbfa
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317288"
---
# <a name="if"></a>IF

如果*運算式*1 為 true （非零） *，則授*與*ifstatements*的元件，如果值為 false （0），則為*elseifstatements* ，而*運算式*為 true。

## <a name="syntax"></a>語法

> **IF** *運算式*\
> *if 語句*\
> ⟦**ELSEIF** *運算式*2\
> *elseif 語句*⟧ \
> ⟦**ELSE**\
> *else 語句*⟧ \
> **ENDIF**

## <a name="remarks"></a>備註

下列指示詞可能會取代為[ELSEIF](elseif-masm.md)： **ELSEIFB**、 **ELSEIFDEF**、 **ELSEIFDIF**、 **ELSEIFDIFI**、 **ELSEIFE**、 **ELSEIFIDN**、 **ELSEIFIDNI**、 **ELSEIFNB**和**ELSEIFNDEF**。 （選擇性）如果上一個運算式為 false，則會組合*else 語句*。 請注意，運算式會在元件時間評估。

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
