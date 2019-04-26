---
title: ML 非嚴重錯誤 A2085
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2085
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
ms.openlocfilehash: 729f6f38761171c6ddc4cccfc2443c6a2b597bf3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62177184"
---
# <a name="ml-nonfatal-error-a2085"></a>ML 非嚴重錯誤 A2085

**指示或在目前的 CPU 模式中不接受暫存器**

您嘗試使用指示、 暫存器或目前的處理器模式中無效的關鍵字。

例如，32 位元暫存器需要[.386](../../assembler/masm/dot-386.md)或更新版本。 控制暫存器，例如需要特殊權限的模式變更 CR0 [.386P](../../assembler/masm/dot-386p.md)或更新版本。 此錯誤，也會產生如**NEAR32**， **FAR32**，並**一般**需要的關鍵字。**386**或更新版本。

## <a name="see-also"></a>另請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>