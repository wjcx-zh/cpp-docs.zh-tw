---
title: Makefile 中的命令 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- commands, makefiles
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99e1eb5b4800ff1046ca60d4d4874d386809e2e0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="commands-in-a-makefile"></a>Makefile 中的命令
描述區塊或推斷規則指定一段命令執行的相依性已過時。 NMAKE 會顯示每個命令之前執行，除非 /S， **。無訊息**， **！CMDSWITCHES**，或使用 @。 如果描述區塊後面沒有接命令區塊，NMAKE 會尋找相符的推斷規則。  
  
 命令區塊包含一個或多個命令，每個的那一行。 相依性或規則與命令區塊之間都沒有空行。 不過，可以顯示包含只有空格或定位點的資料行;這一行會解譯為 null 的命令，並不會發生錯誤。 命令列之間不允許有空白的行。  
  
 命令列的一個或多個空格或定位點開頭。 反斜線 (\) 後面接著新行字元會解譯為命令; 中的空間使用線條結尾的反斜線，繼續到下一行的命令。 NMAKE 會逐字解譯反斜線如果任何其他字元，包括空格或索引標籤上，在反斜線。  
  
 命令加上分號 （;） 可能會出現在相依性線條或推斷規則，不論命令區塊後面：  
  
```  
project.obj : project.c project.h ; cl /c project.c  
```  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
 [命令修飾詞](../build/command-modifiers.md)  
  
 [檔名部分語法](../build/filename-parts-syntax.md)  
  
 [Makefile 中的內嵌檔](../build/inline-files-in-a-makefile.md)  
  
## <a name="see-also"></a>另請參閱  
 [NMAKE 參考](../build/nmake-reference.md)