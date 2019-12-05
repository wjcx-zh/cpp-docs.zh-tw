---
title: ML 非嚴重錯誤 A2031
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2031
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
ms.openlocfilehash: f964c67ba7bf399e9a3761e4e201662a6a712a1b
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856697"
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

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>