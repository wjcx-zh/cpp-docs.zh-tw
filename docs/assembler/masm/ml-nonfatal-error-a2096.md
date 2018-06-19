---
title: ML 非嚴重錯誤 A2096 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 6e5d07afa864c9f6f4214de953aa9e03fe0e7e4f
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
ms.locfileid: "32053668"
---
# <a name="ml-nonfatal-error-a2096"></a>ML 非嚴重錯誤 A2096
**區段、 群組或預期的區段暫存器**  
  
 區段或群組但找不到。  
  
 發生下列其中一項：  
  
-   指定與區段的左的運算元會覆寫運算子 (**:**) 不是區段暫存器 （CS、 DS、 SS、 ES、 FS 或 GS），群組名稱、 區段名稱或區段運算式。  
  
-   [假設](../../assembler/masm/assume.md)指示詞指定的區段暫存器，而不是有效的區段位址、 區段暫存器、 群組或特殊**一般**群組。  
  
## <a name="see-also"></a>另請參閱  
 [ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)