---
title: "呼叫端被呼叫端儲存的暫存器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ebdcf30ea56587b71015a04b5e514dd9ff21aeba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="callercallee-saved-registers"></a>呼叫端/被呼叫端儲存的暫存器
在函式呼叫終結 RAX、 RCX、 RDX、 R8、 R9 R10、 R11 會視為 volatile，而且必須考慮的暫存器 (除非否則安全-可證明分析，例如整個程式最佳化)。  
  
 RBX、 RBP、 RDI、 RSI、 RSP、 R12、 R13、 R14 和 R15 的暫存器會被視為靜態的而且必須儲存和還原函式，會使用它們。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫慣例](../build/calling-convention.md)