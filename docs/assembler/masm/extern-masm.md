---
title: EXTERN (MASM) |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- extern
dev_langs:
- C++
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a9008e8c1153c0a9b06530b14e661436f7e62a9
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693666"
---
# <a name="extern-masm"></a>EXTERN (MASM)

定義一或多個外部變數、 標籤或呼叫的符號*名稱*其型別的*型別*。

## <a name="syntax"></a>語法

> EXTERN [[*langtype*]]*名稱*[[(*altid*)]]:*類型*[[，[[*langtype*]] *名稱*[[(*altid*)]]:*類型*]]...

## <a name="remarks"></a>備註

*型別*可以是[ABS](../../assembler/masm/operator-abs.md)，會匯入*名稱*做為常數。 與相同[EXTRN](../../assembler/masm/extrn.md)。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>