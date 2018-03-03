---
title: "連結器工具警告 LNK4105 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4105
dev_langs:
- C++
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 913a6da056908def8df5aab1c2425ef9a187c1e2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4105"></a>連結器工具警告 LNK4105
未指定選項 'option'; 引數忽略選項  
  
 只會發生這個警告時[/LIBPATH](../../build/reference/libpath-additional-libpath.md)選項設定。 如果未不指定任何目錄，使用此選項時，連結器會忽略此選項，並會產生這則警告訊息。  
  
 如果您不需要覆寫現有的環境程式庫設定，請從 連結器命令列移除 /LIBPATH 選項。 如果您想要用於程式庫有替代的搜尋路徑，請指定 /LIBPATH 選項後面的替代路徑。  
  
## <a name="example"></a>範例  
  
```  
link /libpath:c:\filepath\lib bar.obj  
```  
  
 會指示連結器所需的程式庫中搜尋`c:\filepath\lib`之前搜尋的預設位置中。