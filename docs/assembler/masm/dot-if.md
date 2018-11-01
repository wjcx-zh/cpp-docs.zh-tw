---
title: .IF
ms.date: 08/30/2018
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: cf9c594d843c937dd2191bee2a7cebadbc615c82
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483628"
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