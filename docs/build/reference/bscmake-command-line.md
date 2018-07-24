---
title: BSCMAKE 命令列 |Microsoft Docs
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
ms.openlocfilehash: b79f7e7c181112877c795f3601e8211e70403563
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207743"
---
# <a name="bscmake-command-line"></a>BSCMAKE 命令列
若要執行 BSCMAKE，使用下列命令列語法：  
  
```  
BSCMAKE [options] sbrfiles  
```  
  
 選項僅可出現在`options`命令列上的欄位。  
  
 *Sbrfiles*欄位會指定一或多個編譯器或組譯工具所建立的.sbr 檔案。 使用空格或定位字元分隔.sbr 檔案的名稱。 您必須指定擴充功能;沒有預設值。 您可以指定的路徑與檔名，而且您可以使用作業系統萬用字元 (\*和？)。  
  
 在累加建置，您可以指定新的.sbr 檔案未包含的原始的組建。 如果您想要保留在瀏覽資訊檔中的所有成果，您必須指定所有.sbr 檔 （包括已截斷的檔案），最初用來建立.bsc 檔案。 如果您省略的.sbr 檔案時，會移除該檔案的貢獻，以瀏覽資訊檔。  
  
 未指定完整的組建的已截斷的.sbr 檔案。 完整的建置需要從所有指定的.sbr 檔案。 執行完整建置之前，請重新編譯專案，並建立新的.sbr 檔，針對每個空的檔案。  
  
 下列命令會執行 BSCMAKE 來建置呼叫 MAIN.bsc 從三個.sbr 檔案檔：  
  
```  
BSCMAKE main.sbr file1.sbr file2.sbr  
```  
  
 如需相關資訊，請參閱[BSCMAKE 命令檔](../../build/reference/bscmake-command-file-response-file.md)並[BSCMAKE 選項](../../build/reference/bscmake-options.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BSCMAKE 參考](../../build/reference/bscmake-reference.md)