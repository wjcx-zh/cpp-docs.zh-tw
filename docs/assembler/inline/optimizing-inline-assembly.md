---
title: 最佳化內嵌組譯碼 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c494594e3b7c541487f34fd33359b0e31f73dd61
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="optimizing-inline-assembly"></a>最佳化內嵌組譯碼
## <a name="microsoft-specific"></a>Microsoft 特定的  
 函式中若存在 `__asm` 區塊，則會透過多種方式影響最佳化。 首先，編譯器不會嘗試最佳化 `__asm` 區塊本身。 您在組合語言中撰寫的內容即會與取得的內容完全相同。 其次，`__asm` 區塊會影響暫存器變數儲存區。 如果 `__asm` 區塊可能會變更暫存器的內容，則編譯器會避免跨 `__asm` 區塊註冊這些變數。 最後，其他函式最佳化會受到函式中包含的組合語言所影響。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [內嵌組合語言](../../assembler/inline/inline-assembler.md)