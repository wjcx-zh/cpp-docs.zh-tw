---
title: "編譯器警告 （層級 1） C4799 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4799
dev_langs:
- C++
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f41535c01d67e28baa2569ace2684865407a1d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4799"></a>編譯器警告 (層級 1) C4799  
  
> 在函式的結尾處沒有 EMMS '*函式*'  
  
函式具有一個以上的 MMX 指令，但沒有`EMMS`指令。 當使用多媒體指令時，`EMMS`指令或`_mm_empty`內建函式應該也可用來清除多媒體標記文字 MMX 程式碼的結尾。  
  
使用 ivec.h，指出程式碼不會正確地使用 execute EMMS 指令，再傳回時，可能會收到 C4799。 這是這些標頭，則為 false 的警告。 您可以關閉這些藉由定義 _SILENCE_IVEC_C4799 ivec.h 中。 不過，請注意，這也會使編譯器提供此類型正確的警告。  
  
如需相關資訊，請參閱[Intel 的 MMX 指令集](../../assembler/inline/intel-s-mmx-instruction-set.md)。