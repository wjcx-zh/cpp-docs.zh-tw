---
title: .IF
ms.date: 11/05/2019
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: 83c9ff588e2fe273e24e1d0b1c16517c5eee3365
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703785"
---
# <a name="if-32-bit-masm"></a>.IF （32-bit MASM）

產生測試 `condition1` 的程式碼（例如，AX > 7），並在該條件為 true 時執行*語句*。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> .如果 condition1<br/>
> 陳述式<br/>
> [[.ELSEIF condition2<br/>
> 語句]]<br/>
> [[.東西<br/>
> 語句]]<br/>
> .ENDIF

## <a name="remarks"></a>備註

如果為，則為[。否則](../../assembler/masm/dot-else.md)，如果原始條件為 false，則會執行它的語句。 請注意，在執行時間會評估條件。

## <a name="see-also"></a>請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>