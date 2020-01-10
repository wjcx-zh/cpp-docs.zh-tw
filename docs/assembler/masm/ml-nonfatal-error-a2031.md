---
title: ML 非嚴重錯誤 A2031
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2031
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
ms.openlocfilehash: 4764f7296e28e2128fc4fc80e64f39ceb2a8ed8c
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317067"
---
# <a name="ml-nonfatal-error-a2031"></a>ML 非嚴重錯誤 A2031

**必須是索引或基底暫存器**

嘗試使用的暫存器不是記憶體運算式中的基底或索引註冊。

例如，下列運算式會造成此錯誤：

```asm
[ax]
[bl]
```

## <a name="see-also"></a>請參閱

[ML 錯誤訊息](ml-error-messages.md)
