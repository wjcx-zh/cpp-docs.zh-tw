---
title: ML 非嚴重錯誤 A2085 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2085
dev_langs:
- C++
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd5ec9f36a4f956b8eeb097b6a8f8eaed89ba2b2
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681432"
---
# <a name="ml-nonfatal-error-a2085"></a>ML 非嚴重錯誤 A2085

**指示或在目前的 CPU 模式中不接受暫存器**

您嘗試使用指示、 暫存器或目前的處理器模式中無效的關鍵字。

例如，32 位元暫存器需要[.386](../../assembler/masm/dot-386.md)或更新版本。 控制暫存器，例如需要特殊權限的模式變更 CR0 [.386P](../../assembler/masm/dot-386p.md)或更新版本。 此錯誤，也會產生如**NEAR32**， **FAR32**，並**一般**需要的關鍵字。**386**或更新版本。

## <a name="see-also"></a>另請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>