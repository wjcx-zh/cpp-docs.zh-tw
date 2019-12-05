---
title: ML 非嚴重錯誤 A2085
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2085
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
ms.openlocfilehash: 3bd89fb2b7f8b755cdb095e63ed89386332ecf9d
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74855754"
---
# <a name="ml-nonfatal-error-a2085"></a>ML 非嚴重錯誤 A2085

**目前的 CPU 模式不接受指示或註冊**

嘗試使用對目前處理器模式不正確指令、註冊或關鍵字。

例如，32位暫存器需要[386](../../assembler/masm/dot-386.md)或更新版本。 控制暫存器（例如 CR0 暫存器）需要特殊許可權模式[。 .386p](../../assembler/masm/dot-386p.md)或更新版本。 也會針對需要的**NEAR32**、 **FAR32**和**一般關鍵字產生**此錯誤。**386**或更新版本。

## <a name="see-also"></a>請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>