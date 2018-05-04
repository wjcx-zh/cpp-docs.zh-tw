---
title: BSCMAKE 命令列 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7866d2960acdd89c3015470ef3971307ba162cd3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="bscmake-command-line"></a>BSCMAKE 命令列
若要執行 BSCMAKE，使用下列命令列語法：  
  
```  
BSCMAKE [options] sbrfiles  
```  
  
 選項僅可出現在`options`命令列上的欄位。  
  
 *Sbrfiles*欄位會指定一或多個由編譯器或組譯工具所建立的.sbr 檔案。 使用空格或定位字元分隔.sbr 檔案的名稱。 您必須指定副檔名。沒有預設值。 您可以指定的路徑與檔名，而且您可以使用作業系統萬用字元 (* 和？)。  
  
 累加建置期間，您可以指定新的.sbr 檔案沒有原始組建的一部分。 如果您想要在瀏覽資訊檔中保留所有的比重時，您必須指定所有.sbr 檔 （包括已截斷的檔案） 原本用來建立.bsc 檔案。 如果您省略的.sbr 檔案時，會移除該檔案的比重瀏覽資訊檔。  
  
 請勿指定完整建置截斷的.sbr 檔案。 完整建置需要從所有指定的.sbr 檔案。 在執行完整的組建之前，請重新編譯此專案，並建立新的.sbr 檔，針對每個空的檔案。  
  
 下列命令執行 BSCMAKE 來建置呼叫 MAIN.bsc 從三個.sbr 檔案檔：  
  
```  
BSCMAKE main.sbr file1.sbr file2.sbr  
```  
  
 如需相關資訊，請參閱[BSCMAKE 命令檔](../../build/reference/bscmake-command-file-response-file.md)和[BSCMAKE 選項](../../build/reference/bscmake-options.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BSCMAKE 參考](../../build/reference/bscmake-reference.md)