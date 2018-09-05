---
title: ML 非嚴重錯誤 A2219 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2219
dev_langs:
- C++
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 365997181b0d4f4471162d7cf8f65a4429e69e74
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681641"
---
# <a name="ml-nonfatal-error-a2219"></a>ML 非嚴重錯誤 A2219

**中的位移不正確對齊回溯程式碼**

運算元[。ALLOCSTACK](../../assembler/masm/dot-allocstack.md)和[。SAVEREG](../../assembler/masm/dot-savereg.md)必須是 8 的倍數。  運算元[。SAVEXMM128](../../assembler/masm/dot-savexmm128.md)和[。SETFRAME](../../assembler/masm/dot-setframe.md)必須是 16 的倍數。

## <a name="see-also"></a>另請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>