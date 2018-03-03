---
title: "_emit 虛擬指令 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _emit
dev_langs:
- C++
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c506c689b94a7f6f7fa51c4c456e20454b28df02
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="emit-pseudoinstruction"></a>_emit 虛擬指令
## <a name="microsoft-specific"></a>Microsoft 特定的  
 **_Emit**虛擬指令會定義一個位元組的目前位置目前的文字區段中。 **_Emit**虛擬指令類似[DB](../../assembler/masm/db.md) MASM 指示詞。  
  
 下列片段將位元組 0x4A、0x43 和 0x4B 放入程式碼：  
  
```  
#define randasm __asm _emit 0x4A __asm _emit 0x43 __asm _emit 0x4B  
 .  
 .  
 .  
__asm {  
     randasm  
     }  
```  
  
> [!CAUTION]
>  如果 `_emit` 會產生修改暫存器的指令，而您以最佳化編譯應用程式，則編譯器無法判斷哪些暫存器會受到影響。 例如，如果`_emit`產生的指令，修改**rax**暫存器，編譯器不知道， **rax**已變更。 在內嵌組合語言程式碼執行之後，編譯器可能會對暫存器中的值做出不正確的假設。 因此，應用程式在執行時可能會表現出無法預期的行為。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)