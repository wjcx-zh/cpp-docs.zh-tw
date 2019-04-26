---
title: EXTERNDEF
ms.date: 08/30/2018
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 23d34af470e825a8535de8cb28645a7bfb4c4d1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62203083"
---
# <a name="externdef"></a>EXTERNDEF

定義一或多個外部變數、 標籤或呼叫的符號*名稱*型別是`type`。

## <a name="syntax"></a>語法

> 名稱： 類型 EXTERNDEF [[langtype]] [[，[[langtype]] 名稱： 類型]]...

## <a name="remarks"></a>備註

如果*名稱*定義在模組中，將它視為[公用](../../assembler/masm/public-masm.md)。 如果*名稱*參考在模組中，將它視為[EXTERN](../../assembler/masm/extern-masm.md)。 如果*名稱*是未參考，則會忽略它。 `type`可以是[ABS](../../assembler/masm/operator-abs.md)，會匯入*名稱*做為常數。 通常用在包含檔案。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>