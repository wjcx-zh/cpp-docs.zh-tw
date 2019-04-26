---
title: ML 非嚴重錯誤 A2031
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2031
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
ms.openlocfilehash: 794fb31fbc22bdefddf9f19e6efcb3c34bbc1861
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62177678"
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