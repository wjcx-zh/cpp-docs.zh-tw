---
title: BSCMAKE 命令檔 （回應檔） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BSCMAKE, response file
- BSCMAKE, command file
- response files, BSCMAKE
- command files, BSCMAKE
- response files
- command files
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a879306078c52e0ad11d29f1786a2e55c2480d2f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="bscmake-command-file-response-file"></a>BSCMAKE 命令檔 (回應檔)
您可以提供的命令檔中的命令列輸入部分或全部。 指定命令檔，請使用下列語法：  
  
```  
BSCMAKE @filename  
```  
  
 允許只能有一個命令檔。 您可以指定具有路徑*filename*。 在前面*filename*以 at 符號 (@)。 BSCMAKE 不會採用擴充功能。 您可以指定其他*sbrfiles*之後在命令列上*filename*。 命令檔是包含 BSCMAKE 相同順序的輸入，像您會在命令列上指定它的文字檔案。 與一或多個空格、 tab 字元或換行字元分隔的命令列引數。  
  
 下列命令會呼叫 BSCMAKE 使用命令檔：  
  
```  
BSCMAKE @prog1.txt  
```  
  
 以下是範例指令檔：  
  
```  
/n /v /o main.bsc /El  
/S (  
toolbox.h  
verdate.h c:\src\inc\screen.h  
)  
file1.sbr file2.sbr file3.sbr file4.sbr  
```  
  
## <a name="see-also"></a>另請參閱  
 [BSCMAKE 參考](../../build/reference/bscmake-reference.md)