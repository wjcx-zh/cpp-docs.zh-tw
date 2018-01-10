---
title: "組合語言註解 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ee9ab1975a1146b598d7955d15b8e91a0f396724
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="assembly-language-comments"></a>組合語言註解
## <a name="microsoft-specific"></a>Microsoft 特定的  
 `__asm` 區塊中的指令可使用組合語言註解：  
  
```  
__asm mov ax, offset buff ; Load address of buff  
```  
  
 由於 C 巨集會展開為單一邏輯資料行，請避免在巨集中使用組合語言註解。 (請參閱[__asm 區塊定義為 C 巨集](../../assembler/inline/defining-asm-blocks-as-c-macros.md)。)`__asm`區塊也可以包含 c-style 註解; 如需詳細資訊，請參閱[使用 C 或 c + + 在 __asm 區塊中的](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)