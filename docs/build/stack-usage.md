---
title: 堆疊使用方式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d6e3aa8d01dcc85b6c37684ccccaf82c84d8dfb3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="stack-usage"></a>堆疊使用方式
目前的 RSP 位址以外的所有記憶體會被都視為 volatile： 使用者偵錯工作階段或中斷處理常式期間作業系統或偵錯工具中，可能會覆寫這個記憶體。 因此，必須一律設定 RSP，再嘗試讀取或寫入至堆疊框架的值。  
  
 本章節將討論的本機變數的堆疊空間配置和**alloca**內建函式。  
  
-   [堆疊配置](../build/stack-allocation.md)  
  
-   [動態參數堆疊區域建構](../build/dynamic-parameter-stack-area-construction.md)  
  
-   [函式類型](../build/function-types.md)  
  
-   [malloc 對齊](../build/malloc-alignment.md)  
  
-   [alloca](../build/alloca.md)  
  
## <a name="see-also"></a>請參閱  
 [x64 軟體慣例](../build/x64-software-conventions.md)