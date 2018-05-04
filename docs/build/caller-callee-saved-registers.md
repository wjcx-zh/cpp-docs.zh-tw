---
title: 呼叫端被呼叫端儲存的暫存器 |Microsoft 文件
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
ms.openlocfilehash: 8f65e88c8609d6a2097e9e54c3f52cbd27dce36d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="callercallee-saved-registers"></a>呼叫端/被呼叫端儲存的暫存器
在函式呼叫終結 RAX、 RCX、 RDX、 R8、 R9 R10、 R11 會視為 volatile，而且必須考慮的暫存器 (除非否則安全-可證明分析，例如整個程式最佳化)。  
  
 RBX、 RBP、 RDI、 RSI、 RSP、 R12、 R13、 R14 和 R15 的暫存器會被視為靜態的而且必須儲存和還原函式，會使用它們。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫慣例](../build/calling-convention.md)