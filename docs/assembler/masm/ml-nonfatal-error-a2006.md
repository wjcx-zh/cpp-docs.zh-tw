---
title: ML 非嚴重錯誤 A2006 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2006
dev_langs:
- C++
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f287c6ab46c6af71ba6dc0032f332ce3cc489454
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677401"
---
# <a name="ml-nonfatal-error-a2006"></a>ML 非嚴重錯誤 A2006

**未定義的符號： 識別項**

您嘗試使用未定義的符號。

可能發生下列其中一項：

- 未定義符號。

- 欄位不是指定之結構的成員。

- 符號已定義未包含的 include 檔案中。

- 若不使用的外部符號[EXTERN](../../assembler/masm/extern-masm.md)或是[EXTERNDEF](../../assembler/masm/externdef.md)指示詞。

- 拼錯的符號名稱。

- 其範圍外參考本機程式碼的標籤。

## <a name="see-also"></a>另請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>