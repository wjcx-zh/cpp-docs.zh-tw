---
title: -RAWDATA |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /rawdata
dev_langs:
- C++
helpviewer_keywords:
- RAWDATA dumpbin option
- raw data
- -RAWDATA dumpbin option
- /RAWDATA dumpbin option
ms.assetid: 41cba845-5e1f-415e-9fe4-604a52235983
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28691e636f01174ecfe2a9d48b016523fce67f14
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374995"
---
# <a name="rawdata"></a>/RAWDATA
```  
/RAWDATA[:{1|2|4|8|NONE[,number]]  
```  
  
## <a name="remarks"></a>備註  
 此選項會顯示檔案中的每個區段的未經處理內容。 引數會控制顯示的格式，如下所示：  
  
|引數|結果|  
|--------------|------------|  
|1|預設值。 內容會顯示以十六進位位元組為單位，以及為 ASCII 字元，如果他們已列印表示方式。|  
|2|內容會顯示為 2 個位元組的十六進位值。|  
|4|內容會顯示為 4 個位元組的十六進位值。|  
|8|內容會顯示為 8 個位元組的十六進位值。|  
|無|隱藏未經處理資料。 這個引數是用於控制的輸出/所有。|  
|*數字*|顯示的每一行都將寬度設定為保留`number`每行的值。|  
  
 只有[/HEADERS](../../build/reference/headers.md) DUMPBIN 選項僅適用於所產生的檔案上[/GL](../../build/reference/gl-whole-program-optimization.md)編譯器選項。  
  
## <a name="see-also"></a>另請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)