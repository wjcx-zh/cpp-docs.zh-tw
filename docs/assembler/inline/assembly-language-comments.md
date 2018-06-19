---
title: 組合語言註解 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 048635a874db604f872b4fa87d72bd06d0455438
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
ms.locfileid: "32050759"
---
# <a name="assembly-language-comments"></a>組合語言註解
## <a name="microsoft-specific"></a>Microsoft 特定的  
 `__asm` 區塊中的指令可使用組合語言註解：  
  
```  
__asm mov ax, offset buff ; Load address of buff  
```  
  
 由於 C 巨集會展開為單一邏輯資料行，請避免在巨集中使用組合語言註解。 (請參閱[__asm 區塊定義為 C 巨集](../../assembler/inline/defining-asm-blocks-as-c-macros.md)。)`__asm`區塊也可以包含 c-style 註解; 如需詳細資訊，請參閱[使用 C 或 c + + 在 __asm 區塊中的](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)