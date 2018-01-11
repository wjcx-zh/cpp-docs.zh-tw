---
title: "回呼項目和回呼遮罩 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 24d9992b8a9db679b30624d85ede1a35bfd9826d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="callback-items-and-the-callback-mask"></a>回呼項目和回呼遮罩
對於其各個項目中，清單檢視控制項通常會儲存標籤文字、項目圖示的影像清單索引，和一組用於項目狀態的位元旗標。 如果您的應用程式已經儲存某個項目的一些資訊，將個別項目定義為回呼項目會很有用。  
  
 做為回呼項目定義項目，藉由指定適當的值`pszText`和`iImage`成員**LV_ITEM**結構 (請參閱[clistctrl:: Getitem](../mfc/reference/clistctrl-class.md#getitem))。 如果應用程式會維護文字項目或子項目，指定**LPSTR_TEXTCALLBACK**值`pszText`成員。 如果應用程式會持續追蹤項目的圖示，指定**I_IMAGECALLBACK**值`iImage`成員。  
  
 除了定義回呼項目之外，您也可以修改控制項的回呼遮罩。 這個遮罩是一組指定儲存目前資料之應用程式 (而不是控制項) 項目狀態的位元旗標。 回呼遮罩適用於所有控制項的項目，與套用至特定項目的回呼項目指定不同。 回呼遮罩預設為零，表示控制項正在追蹤所有項目的狀態。 若要變更此預設行為，請將遮罩初始化為下列值的任何組合：  
  
-   `LVIS_CUT`項目已標示為 剪下和貼上作業。  
  
-   `LVIS_DROPHILITED`項目是做為拖放目標反白顯示。  
  
-   `LVIS_FOCUSED`項目具有焦點。  
  
-   `LVIS_SELECTED`選取的項目。  
  
-   **LVIS_OVERLAYMASK**應用程式會儲存每個項目目前的覆疊影像的影像清單索引。  
  
-   **LVIS_STATEIMAGEMASK**應用程式會儲存每個項目之目前狀態影像的影像清單索引。  
  
 如需擷取和設定這個遮罩的進一步資訊，請參閱[clistctrl:: Getcallbackmask](../mfc/reference/clistctrl-class.md#getcallbackmask)和[clistctrl:: Setcallbackmask](../mfc/reference/clistctrl-class.md#setcallbackmask)。  
  
## <a name="see-also"></a>請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)

