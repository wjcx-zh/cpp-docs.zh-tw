---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: ba1377359ba9bc960e5d7d2a55df15adfe0d5d33
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076206"
---
# <a name="invoke"></a>INVOKE

（僅限 32-bit MASM）。在*運算式*所指定的位址上呼叫程式，並根據語言類型的標準呼叫慣例，傳遞堆疊上或在暫存器中的引數。

## <a name="syntax"></a>語法

> **INVOKE**叫用*運算式*⟦ __，__ *引數*.。。⟧

## <a name="remarks"></a>備註

傳遞至程式的每個引數都可以是運算式、暫存器組或位址運算式（前面加上**ADDR**的運算式）。

## <a name="see-also"></a>另請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
