---
title: ML 非嚴重錯誤 A2219
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: cf2be5db2aa9c21597c199a6840f4aaa50e0a681
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854585"
---
# <a name="ml-nonfatal-error-a2219"></a>ML 非嚴重錯誤 A2219

> 回溯程式碼中的位移不正確對齊

## <a name="remarks"></a>備註

[&period;ALLOCSTACK](../../assembler/masm/dot-allocstack.md)和[&period;SAVEREG](../../assembler/masm/dot-savereg.md)的運算元必須是8的倍數。  [&period;SAVEXMM128](../../assembler/masm/dot-savexmm128.md)和[&period;SETFRAME](../../assembler/masm/dot-setframe.md)的運算元必須是16的倍數。

## <a name="see-also"></a>請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)
