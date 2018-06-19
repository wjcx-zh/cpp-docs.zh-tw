---
title: BSCMAKE 如何建置。Bsc 檔案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- browse information files (.bsc), building
ms.assetid: 8512b33e-c856-44a2-87bd-01ab10b52a95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0cdc8a2840e3beb1272b33b2794f70a979684f46
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373484"
---
# <a name="how-bscmake-builds-a-bsc-file"></a>BSCMAKE 如何建置 .Bsc 檔
BSCMAKE 建立或重建.bsc 檔中可以最有效率的方式。 若要避免潛在的問題，請務必了解建置程序。  
  
 當 BSCMAKE 建置瀏覽資訊檔時，它會截斷為零長度的.sbr 檔案。 在相同檔案的後續建置期間長度為零 （或空白） 的.sbr 檔案會告訴 BSCMAKE.sbr 檔有沒有新的比重進行。 它可讓 BSCMAKE 知道不需要更新之該部分的檔案，以及將足以使用累加建置。 在每次建置期間 （除非指定了 /n 選項），BSCMAKE 第一次嘗試使用已變更的.sbr 檔案以累加方式更新檔案。  
  
 BSCMAKE 尋找.bsc 檔具有 /o 選項所指定的名稱。 如果未指定 /o，BSCMAKE 會尋找基底名稱的第一個的.sbr 檔案和.bsc 副檔名的檔案。 如果檔案存在，BSCMAKE 執行瀏覽資訊檔使用的參與.sbr 檔案的累加建置。 如果檔案不存在，BSCMAKE 會執行完整建置使用所有.sbr 檔。 組建的規則如下所示：  
  
-   若要成功完整建置，指定所有.sbr 檔必須存在，且不會被截斷。 如果遭到截斷的.sbr 檔案，您必須 （以重新編譯或組裝） 重建之前執行 BSCMAKE。  
  
-   累加建置成功，.bsc 檔必須存在。 所有參與的.sbr 檔，即使是空的檔案，必須存在而且必須指定 BSCMAKE 命令列上。 如果您省略的.sbr 檔案，從命令列，BSCMAKE 會從檔案移除該著作。  
  
## <a name="see-also"></a>另請參閱  
 [建置 .Bsc 檔](../../build/reference/building-a-dot-bsc-file.md)