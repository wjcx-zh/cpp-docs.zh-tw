---
title: 經過時間： 一般用途類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- adding dates
- calculating dates and times
- dates, calculating intervals
- elapsed time, calculating
- elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: e5c5d3d2-ce1d-409e-875c-98848434e716
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff7ef11bb20124a05e2e85c408ce27de8f982546
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354262"
---
# <a name="elapsed-time-general-purpose-classes"></a>經過時間： 一般用途類別
下列程序顯示如何計算兩個之間的差異`CTime`物件和 get`CTimeSpan`結果。  
  
#### <a name="to-calculate-elapsed-time"></a>若要計算經過的時間  
  
1.  使用`CTime`和`CTimeSpan`物件來計算所經歷的時間，如下所示：  
  
     [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]  
  
     一旦您計算`elapsedTime`，您可以使用的成員函式`CTimeSpan`擷取耗用時間值的元件。  
  
## <a name="see-also"></a>另請參閱  
 [日期和時間：一般用途類別](../atl-mfc-shared/date-and-time-general-purpose-classes.md)

