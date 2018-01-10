---
title: "檔名部分語法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a481f8c461cb4fddd4acb090edb2f2b5fd18636d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="filename-parts-syntax"></a>檔名部分語法
在命令中的檔名部分語法表示第一個相依檔案名稱 （這可能是隱含的相依性） 的元件。 檔名元件是檔案的磁碟機、 路徑、 基底名稱和副檔名為指定的不存在於磁碟上。 使用**%s**來代表完整的檔名。 使用**%&#124;**[*部分*]**F** (分隔號字元後面的百分比符號) 來代表組件的檔名，其中*部分*可以是零或多個下列的字母，以任何順序。  
  
|字母|描述|  
|------------|-----------------|  
|沒有字母|完整名稱 (與相同**%s**)|  
|**d**|磁碟機|  
|**p**|路徑|  
|**f**|基底檔案的名稱|  
|**e**|副檔名|  
  
 例如，如果檔案名稱是 c:\prog.exe:  
  
-   將 c:\prog.exe %s。  
  
-   %&#124;將 c:\prog.exe F。  
  
-   %&#124; dF 會成為 c  
  
-   %&#124; pF 會成為 c:\  
  
-   %&#124; fF 會成為 prog  
  
-   %&#124; eF 會成為 exe  
  
## <a name="see-also"></a>請參閱  
 [Makefile 中的命令](../build/commands-in-a-makefile.md)