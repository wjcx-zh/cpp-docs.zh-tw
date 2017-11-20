---
title: "檢查記憶體覆寫 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4560fb580d3d1b24feccf84dc07bde7dc38458c2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="checking-for-memory-overwrites"></a>檢查記憶體覆寫
如果您將堆積操作函式的呼叫上取得存取違規，很可能您的程式已損毀堆積。 這種狀況的一般症狀會是：  
  
```  
Access Violation in _searchseg  
```  
  
 [_Heapchk](../../c-runtime-library/reference/heapchk.md)函式是適用於這兩個偵錯和發行的組建 (Windows NT) 來驗證執行的階段程式庫堆積的完整性。 您可以使用`_heapchk`中一樣為`AfxCheckMemory`例如隔離堆積覆寫的函式：  
  
```  
if(_heapchk()!=_HEAPOK)  
   DebugBreak();  
```  
  
 此函式發生問題時，如果您要找出在哪個點堆積已損毀。  
  
## <a name="see-also"></a>另請參閱  
 [解決發行組建的問題](../../build/reference/fixing-release-build-problems.md)