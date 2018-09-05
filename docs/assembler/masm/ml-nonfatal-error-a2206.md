---
title: ML 非嚴重錯誤 A2206 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2206
dev_langs:
- C++
helpviewer_keywords:
- A2206
ms.assetid: 711846d0-5a09-4353-8857-60588c25526a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10edbe68ca7f0093cdeb6a9ca5a02cde07f556e6
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676344"
---
# <a name="ml-nonfatal-error-a2206"></a>ML 非嚴重錯誤 A2206

**在運算式中遺漏運算子**

無法評估運算式，因為它遺漏運算子。 這則錯誤訊息也可能是先前的程式錯誤的副作用。

下面這一行會產生這個錯誤：

```asm
value1 = ( 1 + 2 ) 3
```

## <a name="see-also"></a>另請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>