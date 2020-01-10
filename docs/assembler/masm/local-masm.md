---
title: LOCAL (MASM)
ms.date: 12/16/2019
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: 2bef6b26f1b922be6512bd6ebe8e0b2627e86f45
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317145"
---
# <a name="local"></a>LOCAL

在宏內的第一個指示詞中， **LOCAL**會定義每個宏實例特有的標籤。

## <a name="syntax"></a>語法

> **LOCAL** *LocalId* ⟦， *localId* .。。⟧
>
> **LOCAL** *labelId* ⟦ __\[__ *count* __]__ ⟧⟦ __：__ *qualifiedType*⟧⟦ __，__ *labelId* ⟦ __\[__ *count* __]__ *⟧⟦ qualifiedType ⟧ ...* ⟧

## <a name="remarks"></a>備註

在第二個指示詞中，在程序定義（**PROC**）內， **LOCAL**會建立在程式期間存在的堆疊型變數。 *LabelId*可以是簡單變數或包含*count*元素的陣列，其中*count*是常數運算式。

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
