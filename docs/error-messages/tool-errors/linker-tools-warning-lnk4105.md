---
title: 連結器工具警告 LNK4105 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4105
dev_langs:
- C++
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ffdd8953e08f38d36bdfc2e68ad6cb8e06fb85b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33304410"
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