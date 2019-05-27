---
title: ML 非嚴重錯誤 A2219
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: 61fa6bc6d630f1e8a8ac84492b60690c9545fb3e
ms.sourcegitcommit: 79e985d3c6e8ccaf94f6e641972887cae8c6eeb0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66197673"
---
# <a name="ml-nonfatal-error-a2219"></a>ML 非嚴重錯誤 A2219

> 中的位移不正確對齊回溯程式碼

## <a name="remarks"></a>備註

運算元[ &period;ALLOCSTACK](../../assembler/masm/dot-allocstack.md)並[ &period;SAVEREG](../../assembler/masm/dot-savereg.md)必須是 8 的倍數。  運算元[ &period;SAVEXMM128](../../assembler/masm/dot-savexmm128.md)並[ &period;SETFRAME](../../assembler/masm/dot-setframe.md)必須是 16 的倍數。

## <a name="see-also"></a>另請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)
