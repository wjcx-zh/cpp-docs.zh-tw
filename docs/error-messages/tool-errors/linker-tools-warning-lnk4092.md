---
title: 連結器工具警告 LNK4092 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4092
dev_langs:
- C++
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72edd9e75dbc781355396e38f767a64c1ded3aa9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4092"></a>連結器工具警告 LNK4092
共用的可寫入區段 'section' 含有重新配置。映像可能無法正確執行  
  
 當您擁有一個共用的小節來警告您可能會發生嚴重問題，連結器就會發出這個警告。  
  
 多個處理序之間共用資料的一種方式為一個區段標示為 「 共用 」。 不過，標示為共用區段可能會造成問題。 例如，您有 DLL，其中包含共用的資料區段中的宣告如下：  
  
```  
int var = 1;  
int *pvar = &var;  
```  
  
 連結器無法解析`pvar`因為 DLL 載入記憶體中的位置取決於它的值，因此它的重新放置將記錄放置在 DLL 中。 當將 DLL 載入記憶體的位址`var`可以解決和`pvar`指派。 如果另一個處理序載入相同的 DLL，但卻無法載入在相同位址，重新配置的位址`var`第二個程序，而且第一個處理序位址空間，將指向錯誤的位址將會更新。