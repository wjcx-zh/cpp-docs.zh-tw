---
title: .CODE
ms.date: 12/17/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 7e53befcc46319d0ecf2287ab96a19a73a0b0b85
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076269"
---
# <a name="code"></a>.CODE

（僅限 32-bit MASM）。與搭配使用時[。MODEL](dot-model.md)：表示程式碼區段的開頭。

## <a name="syntax"></a>語法

> **.程式碼**⟦*名稱*⟧ \
> ⟦ *segmentItem* ⟧ ... \
> ⟦ *codesegmentnameId* **結束**;;⟧\

### <a name="parameters"></a>參數

*名稱*\
指定程式碼片段名稱的選擇性參數。 針對小型、小型、精簡和平面[模型](dot-model.md)，預設名稱是 **_TEXT** 。 預設名稱是其他模型的*modulename*_TEXT。

## <a name="see-also"></a>另請參閱

指示詞[參考](directives-reference.md)\
[.資料](dot-data.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
