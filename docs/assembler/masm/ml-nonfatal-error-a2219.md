---
title: ML 非嚴重錯誤 A2219
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: 611be49a1d4018eeb4edd9ee750d5a0614a83abe
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75311945"
---
# <a name="ml-nonfatal-error-a2219"></a>ML 非嚴重錯誤 A2219

> 回溯程式碼中的位移不正確對齊

## <a name="remarks"></a>備註

[&period;ALLOCSTACK](dot-allocstack.md)和[&period;SAVEREG](dot-savereg.md)的運算元必須是8的倍數。  [&period;SAVEXMM128](dot-savexmm128.md)和[&period;SETFRAME](dot-setframe.md)的運算元必須是16的倍數。

## <a name="see-also"></a>請參閱

[ML 錯誤訊息](ml-error-messages.md)
