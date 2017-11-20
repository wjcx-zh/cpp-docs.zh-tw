---
title: "目前時間： 一般用途類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- time, setting current
- current time, CTime object
- procedures, getting current time
- initializing objects, with the current time
- time, getting current
ms.assetid: c39e6775-6a92-4b27-95a7-5c86ed371d8a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d40f0044795c6fd7c5df3850261ceb4314f50dbd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="current-time-general-purpose-classes"></a>目前時間： 一般用途類別
下列程序示範如何建立`CTime`物件，並將它初始化為目前時間。  
  
#### <a name="to-get-the-current-time"></a>若要取得目前的時間  
  
1.  配置`CTime`物件，如下所示：  
  
     [!code-cpp[NVC_ATLMFC_Utilities#171](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_1.cpp)]  
  
    > [!NOTE]
    >  未初始化`CTime`物件不會初始化為有效的時間。  
  
2.  呼叫`CTime::GetCurrentTime`函式可從作業系統取得目前的時間。 此函數會傳回`CTime`物件可以用來設定的值， `CTime`、，如下所示：  
  
     [!code-cpp[NVC_ATLMFC_Utilities#172](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_2.cpp)]  
  
     因為`GetCurrentTime`是靜態成員函式從`CTime`類別，您必須限定其名稱與類別和範圍解析運算子的名稱 (`::`)， `CTime::GetCurrentTime()`。  
  
 當然，所述的兩個步驟之前無法合併成單一的程式陳述式，如下所示：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#173](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_3.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [日期和時間：一般用途類別](../atl-mfc-shared/date-and-time-general-purpose-classes.md)



