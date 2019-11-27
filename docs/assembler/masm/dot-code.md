---
title: .CODE
ms.date: 08/30/2018
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: a5b6608ca71a2b406c54a06cd44ac2865211a8ac
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398571"
---
# <a name="code"></a>.CODE

與搭配使用時[。MODEL](../../assembler/masm/dot-model.md)：表示程式碼區段的開頭。

## <a name="syntax"></a>語法

> **.程式碼**⟦*名稱*⟧

### <a name="parameters"></a>參數

*名稱*\
指定程式碼片段名稱的選擇性參數。 針對小型、小型、精簡和平面[模型](../../assembler/masm/dot-model.md)，預設名稱是 **_TEXT** 。 預設名稱是其他模型的*modulename*_TEXT。

## <a name="see-also"></a>另請參閱

指示詞[參考](../../assembler/masm/directives-reference.md)\
[.DATA](../../assembler/masm/dot-data.md)
