---
title: 堆疊使用方式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6f711636089a6f2966002002220aac88cebe17a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="stack-usage"></a>堆疊使用方式
目前的 RSP 位址以外的所有記憶體會被都視為 volatile： 使用者偵錯工作階段或中斷處理常式期間作業系統或偵錯工具中，可能會覆寫這個記憶體。 因此，必須一律設定 RSP，再嘗試讀取或寫入至堆疊框架的值。  
  
 本章節將討論的本機變數的堆疊空間配置和**alloca**內建函式。  
  
-   [堆疊配置](../build/stack-allocation.md)  
  
-   [動態參數堆疊區域建構](../build/dynamic-parameter-stack-area-construction.md)  
  
-   [函式類型](../build/function-types.md)  
  
-   [malloc 對齊](../build/malloc-alignment.md)  
  
-   [alloca](../build/alloca.md)  
  
## <a name="see-also"></a>另請參閱  
 [x64 軟體慣例](../build/x64-software-conventions.md)