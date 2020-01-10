---
title: .STACK
ms.date: 11/05/2019
f1_keywords:
- .STACK
helpviewer_keywords:
- .STACK directive
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
ms.openlocfilehash: 4dd45a0705b729e65bb413fc02671f86e5f9105b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318224"
---
# <a name="stack-32-bit-masm"></a>.堆疊（32位 MASM）

與搭配使用時[。MODEL](dot-model.md)，定義堆疊區段（含有區段名稱**堆疊**）。 選擇性的*大小*會指定堆疊的位元組數目（預設值為1024）。 **。STACK**指示詞會自動關閉堆疊語句。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> **.STACK** ⟦*大小*⟧

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
