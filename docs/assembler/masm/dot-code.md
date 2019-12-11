---
title: .CODE
ms.date: 12/06/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 36d9c01d2a24b446ddc91fe73f3cb677067b3e4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987914"
---
# <a name="code-32-bit-masm"></a>.程式碼（32位 MASM）

與搭配使用時[。MODEL](../../assembler/masm/dot-model.md)：表示程式碼區段的開頭。

## <a name="syntax"></a>語法

> **.程式碼**⟦*名稱*⟧

### <a name="parameters"></a>參數

*名稱*\
指定程式碼片段名稱的選擇性參數。 針對小型、小型、精簡和平面[模型](../../assembler/masm/dot-model.md)，預設名稱是 **_TEXT** 。 預設名稱是其他模型的*modulename*_TEXT。

## <a name="see-also"></a>請參閱

指示詞[參考](../../assembler/masm/directives-reference.md)\
[.DATA](../../assembler/masm/dot-data.md)
