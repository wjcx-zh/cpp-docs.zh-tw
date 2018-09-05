---
title: .IF | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .IF
dev_langs:
- C++
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7bd5ba5821b4dcfb2d088e31816f50540445018
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691540"
---
# <a name="if"></a>.IF

產生測試的程式碼`condition1`(例如，AX > 7)，並執行*陳述式*如果條件為 true。

## <a name="syntax"></a>語法

> .如果 condition1<br/>
> 陳述式<br/>
> [[.ELSEIF condition2<br/>
> 陳述式]]<br/>
> [[.其他<br/>
> 陳述式]]<br/>
> .ENDIF

## <a name="remarks"></a>備註

如果[。其他](../../assembler/masm/dot-else.md)如下所示，它的陳述式會執行，如果原始的條件為 false。 請注意，在執行階段評估條件。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>