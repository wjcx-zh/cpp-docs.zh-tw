---
title: .IF
ms.date: 11/05/2019
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: 6992ec8b151a83b3f9fa920997845c20caf0476d
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317743"
---
# <a name="if-32-bit-masm"></a>.IF （32-bit MASM）

產生測試*condition1*的程式碼（例如，AX > 7），並在該條件為 true 時執行*語句*。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> **.如果** *condition1*\
> *語句*\
> ⟦ **。ELSEIF** *condition2*\
> *語句*⟧ \
> ⟦ **。否則**\
> *語句*⟧ \
> **.ENDIF**

## <a name="remarks"></a>備註

如果為，則為[。否則](dot-else.md)，如果原始條件為 false，則會執行它的語句。 請注意，在執行時間會評估條件。

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
