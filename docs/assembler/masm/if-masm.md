---
title: IF (MASM) |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- if
dev_langs:
- C++
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca0cce834924f7fc147b1ef301d5bd345dfd2973
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685303"
---
# <a name="if-masm"></a>IF (MASM)

授與組件*ifstatements*如果*expression1*為 true （非零） 或*elseifstatements*如果*expression1*為 false (0) 和*expression2*為 true。

## <a name="syntax"></a>語法

> 如果*expression1*<br/>
> *ifstatements*<br/>
> [[ELSEIF *expression2*<br/>
> *elseifstatements*]]<br/>
> [[其他<br/>
> *elsestatements*]]<br/>
> ENDIF

## <a name="remarks"></a>備註

下列指示詞可能用來替代[ELSEIF](../../assembler/masm/elseif-masm.md): **ELSEIFB**， **ELSEIFDEF**， **ELSEIFDIF**， **ELSEIFDIFI**， **ELSEIFE**， **ELSEIFIDN**， **ELSEIFIDNI**， **ELSEIFNB**，以及**ELSEIFNDEF**. （選擇性） 會組譯*elsestatements*如果上一個運算式為 false。 請注意，在組件時，會評估運算式。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>