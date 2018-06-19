---
title: DUMPBIN 命令列 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- dumpbin
dev_langs:
- C++
helpviewer_keywords:
- DUMPBIN program, command line
ms.assetid: e6ad17d3-965d-41aa-9dfd-75bb073718d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc807a8f67ddaae894a0e0cba55475b804a0abce
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32370510"
---
# <a name="dumpbin-command-line"></a>DUMPBIN 命令列
若要執行 DUMPBIN，使用下列語法：  
  
```  
DUMPBIN [options] files...  
```  
  
 指定一或多個二進位檔，以及任何所需選項來控制的資訊。 DUMPBIN 至標準輸出顯示的資訊。 您可以將它重新導向至檔案，或使用 /OUT 選項指定輸出檔案名稱。  
  
 當您不指定選項，在檔案上執行 DUMPBIN 時，DUMPBIN 會顯示指定 /SUMMARY 輸出。  
  
 當您輸入命令`dumpbin`沒有命令列的輸入，DUMPBIN 會顯示摘要其選項的使用方式陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [C/c + + 建置工具](../../build/reference/c-cpp-build-tools.md)   
 [DUMPBIN 參考](../../build/reference/dumpbin-reference.md)