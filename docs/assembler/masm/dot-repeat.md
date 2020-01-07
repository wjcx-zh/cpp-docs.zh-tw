---
title: .REPEAT
ms.date: 11/05/2019
f1_keywords:
- .REPEAT
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
ms.openlocfilehash: f21f3f3cc4cb86b1ca2503d515dcd7fbcdffe622
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318276"
---
# <a name="repeat-32-bit-masm"></a>.重複（32位 MASM）

產生會重複執行*語句*區塊的程式碼，直到*條件*變成 true 為止。 [.UNTILCXZ](dot-untilcxz.md)，如果 CX 為零，則可替代[。直到](dot-until.md)。 *條件*是選擇性的 **.UNTILCXZ**。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> **.重複**\
> *語句*\
> **.UNTIL** *條件*

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
