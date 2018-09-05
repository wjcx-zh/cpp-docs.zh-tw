---
title: ML 非嚴重錯誤 A2096 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2096
dev_langs:
- C++
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82f4ef76dca10b1208a931bc3e1cc09d82a639d2
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679594"
---
# <a name="ml-nonfatal-error-a2096"></a>ML 非嚴重錯誤 A2096

**區段、 群組或預期的區段註冊**

區段或群組必須，但是找不到。

發生下列其中一項：

- 指定與區段的左的運算元會覆寫運算子 (**:**) 不是區段註冊 （CS、 DS、 SS、 ES、 FS 或 GS），群組名稱、 的區段名稱或區段的運算式。

- [假設](../../assembler/masm/assume.md)指示詞指定的區段暫存器，而不是有效的區段位址、 區段註冊、 群組或特殊**一般**群組。

## <a name="see-also"></a>另請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>