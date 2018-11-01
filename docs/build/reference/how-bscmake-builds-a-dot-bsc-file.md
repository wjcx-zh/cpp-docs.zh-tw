---
title: BSCMAKE 如何建置 .Bsc 檔
ms.date: 11/04/2016
helpviewer_keywords:
- browse information files (.bsc), building
ms.assetid: 8512b33e-c856-44a2-87bd-01ab10b52a95
ms.openlocfilehash: 053bc7565accce5db8998ae8efec256ef37d37b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442584"
---
# <a name="how-bscmake-builds-a-bsc-file"></a>BSCMAKE 如何建置 .Bsc 檔

BSCMAKE 建置或重建.bsc 檔中可以最有效率的方式。 若要避免潛在的問題，請務必了解建置程序。

當 BSCMAKE 建置瀏覽資訊檔時，它會截斷為長度為零的.sbr 檔案。 在相同檔案的後續組建，長度為零 （或空白） 的.sbr 檔案會告訴 BSCMAKE.sbr 檔案有進行任何新的比重。 它可讓 BSCMAKE 知道不需要更新之該部分的檔案，以及累加建置會就已足夠。 在每次建置期間 （除非已指定 [/n] 選項），BSCMAKE 會先嘗試使用已變更.sbr 檔，以累加方式更新檔案。

BSCMAKE 會尋找.bsc 檔具有 /o 選項所指定的名稱。 如果未指定 /o BSCMAKE 會尋找基底名稱的第一個的.sbr 檔案以及.bsc 延伸模組的檔案。 如果檔案存在，BSCMAKE 會執行使用只將參與的.sbr 檔案瀏覽資訊檔的累加組建。 如果檔案不存在，BSCMAKE 會執行完整建置，使用所有.sbr 檔案。 組建的規則如下所示：

- 若要成功完整建置，所有指定.sbr 檔必須存在，且不會被截斷。 如果遭到截斷的.sbr 檔案，您必須重建它 （藉由重新編譯或組合） 之前執行 BSCMAKE。

- 累加建置成功，.bsc 檔必須存在。 所有參與的.sbr 檔案，甚至是空的檔案，必須存在，且必須指定 BSCMAKE 命令列上。 如果您省略的.sbr 檔案，從命令列，BSCMAKE 會移除檔案的著作。

## <a name="see-also"></a>另請參閱

[建置 .Bsc 檔](../../build/reference/building-a-dot-bsc-file.md)