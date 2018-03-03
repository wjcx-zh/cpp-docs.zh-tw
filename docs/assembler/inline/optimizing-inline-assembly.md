---
title: "最佳化內嵌組譯碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 21f6954ece6adcc60fbb3a8620dd427e7c21042a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="optimizing-inline-assembly"></a>最佳化內嵌組譯碼
## <a name="microsoft-specific"></a>Microsoft 特定的  
 函式中若存在 `__asm` 區塊，則會透過多種方式影響最佳化。 首先，編譯器不會嘗試最佳化 `__asm` 區塊本身。 您在組合語言中撰寫的內容即會與取得的內容完全相同。 其次，`__asm` 區塊會影響暫存器變數儲存區。 如果 `__asm` 區塊可能會變更暫存器的內容，則編譯器會避免跨 `__asm` 區塊註冊這些變數。 最後，其他函式最佳化會受到函式中包含的組合語言所影響。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [內嵌組合語言](../../assembler/inline/inline-assembler.md)