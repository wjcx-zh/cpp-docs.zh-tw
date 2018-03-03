---
title: "經過時間： Automation 類別 |Microsoft 文件"
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
- elapsed time, calculating in Automation
- Automation classes, elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: 26b34b37-c10e-4b91-82c3-1dc5ffb5361f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e4cf7fef17499910d9664ab26fa1b07438e7900
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="elapsed-time-automation-classes"></a>經過時間： Automation 類別
此程序顯示如何計算兩個之間的差異`CTime`物件和 get`CTimeSpan`結果。  
  
#### <a name="to-calculate-elapsed-time"></a>若要計算經過的時間  
  
1.  建立兩個`COleDateTime`物件。  
  
2.  其中一個設定`COleDateTime`物件為目前的時間。  
  
3.  執行一些相當耗時的工作。  
  
4.  設定其他`COleDateTime`物件為目前的時間。  
  
5.  需要兩個時間之間的差異。  
  
     [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [日期和時間：Automation 支援](../atl-mfc-shared/date-and-time-automation-support.md)

