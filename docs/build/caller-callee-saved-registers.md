---
title: 呼叫端-被呼叫端儲存的暫存器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8e877387dbb5b0be865e11017a3ac71a0c38faa
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707651"
---
# <a name="callercallee-saved-registers"></a>呼叫端/被呼叫端儲存的暫存器

暫存器 RAX、 RCX、 RDX、 R8，R9、 R10、 R11 會視為 volatile 和視為必須終結函式呼叫 (除非否則安全-可證明之分析整個程式最佳化 」 等)。

暫存器 RBX、 RBP、 RDI、 RSI、 RSP、 R12、 R13、 R14 和 R15 會被視為靜態的而且必須儲存和還原函式使用它們。

## <a name="see-also"></a>另請參閱

[呼叫慣例](../build/calling-convention.md)