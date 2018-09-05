---
title: ML 非嚴重錯誤 A2031 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2031
dev_langs:
- C++
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf6744224847e114e76df6e7ad6470696d3e8387
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682654"
---
# <a name="ml-nonfatal-error-a2031"></a>ML 非嚴重錯誤 A2031

**必須是基底或索引暫存器**

您嘗試使用不是基底或索引暫存器記憶體運算式中的暫存器。

例如，下列運算式會造成這個錯誤：

```asm
[ax]
[bl]
```

## <a name="see-also"></a>另請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>