---
title: 呼叫端-被呼叫端儲存的暫存器
ms.date: 11/04/2016
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
ms.openlocfilehash: f34fbfff8e6c61b5d568c073f6b7da2a12e34535
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654697"
---
# <a name="callercallee-saved-registers"></a>呼叫端/被呼叫端儲存的暫存器

暫存器 RAX、 RCX、 RDX、 R8，R9、 R10、 R11 會視為 volatile 和視為必須終結函式呼叫 (除非否則安全-可證明之分析整個程式最佳化 」 等)。

暫存器 RBX、 RBP、 RDI、 RSI、 RSP、 R12、 R13、 R14 和 R15 會被視為靜態的而且必須儲存和還原函式使用它們。

## <a name="see-also"></a>另請參閱

[呼叫慣例](../build/calling-convention.md)