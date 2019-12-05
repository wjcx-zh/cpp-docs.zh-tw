---
title: ML 非嚴重錯誤 A2096
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2096
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
ms.openlocfilehash: 14fb30214cf7badf51368672dc52635d50a067f1
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74855470"
---
# <a name="ml-nonfatal-error-a2096"></a>ML 非嚴重錯誤 A2096

**需要區段、群組或區段註冊**

需要區段或群組，但找不到。

發生下列其中一種情況：

- 以區段覆寫運算子（ **：** ）指定的左運算元不是區段暫存器（CS、DS、SS、ES、FS 或 GS）、組名、區段名稱或區段運算式。

- [假設](../../assembler/masm/assume.md)指示詞在沒有有效區段位址、區段暫存器、群組**或特殊一般**群組的情況下，已獲得區段暫存器。

## <a name="see-also"></a>請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>