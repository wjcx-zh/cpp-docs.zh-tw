---
title: ML 非嚴重錯誤 A2031 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2031
dev_langs:
- C++
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ab35776944604f3133254532d2631460c755983
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
ms.locfileid: "32057142"
---
# <a name="ml-nonfatal-error-a2031"></a>ML 非嚴重錯誤 A2031
**必須是基底或索引暫存器**  
  
 您嘗試使用不是基底或索引暫存器記憶體運算式中的暫存器。  
  
 例如，下列運算式會造成這個錯誤：  
  
```  
[ax]  
[bl]  
```  
  
## <a name="see-also"></a>另請參閱  
 [ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)