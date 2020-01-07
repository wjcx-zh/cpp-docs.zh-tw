---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: 7a005e5e70a2696ca89fb0ad1a3ff02aab8ffe5a
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317184"
---
# <a name="invoke"></a>INVOKE

（僅限 32-bit MASM）。在*運算式*所指定的位址上呼叫程式，並根據語言類型的標準呼叫慣例，傳遞堆疊上或在暫存器中的引數。     

## <a name="syntax"></a>語法

> 叫用*運算式*⟦ __，__ *引數*.。。⟧

## <a name="remarks"></a>備註

傳遞至程式的每個引數都可以是運算式、暫存器組或位址運算式（前面加上**ADDR**的運算式）。

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
