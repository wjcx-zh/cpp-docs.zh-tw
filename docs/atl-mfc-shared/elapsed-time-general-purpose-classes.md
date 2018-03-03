---
title: "經過時間： 一般用途類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 51eea60669fb7ad35525d65013ffc8420649349b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="elapsed-time-general-purpose-classes"></a>經過時間： 一般用途類別
下列程序顯示如何計算兩個之間的差異`CTime`物件和 get`CTimeSpan`結果。  
  
#### <a name="to-calculate-elapsed-time"></a>若要計算經過的時間  
  
1.  使用`CTime`和`CTimeSpan`物件來計算所經歷的時間，如下所示：  
  
     [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]  
  
     一旦您計算`elapsedTime`，您可以使用的成員函式`CTimeSpan`擷取耗用時間值的元件。  
  
## <a name="see-also"></a>請參閱  
 [日期和時間：一般用途類別](../atl-mfc-shared/date-and-time-general-purpose-classes.md)

