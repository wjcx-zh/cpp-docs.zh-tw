---
title: "清單控制項和清單檢視 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 46c9d559d642b6edf926b9feb49332ef7ec2924a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="list-control-and-list-view"></a>清單控制項和清單檢視
為了方便起見，MFC 以兩種方式封裝清單控制項。 您可以下列方式來使用清單控制項：  
  
-   直接透過內嵌[CListCtrl](../mfc/reference/clistctrl-class.md)對話方塊類別中的物件。  
  
-   使用類別來間接[CListView](../mfc/reference/clistview-class.md)。  
  
 `CListView`輕鬆地整合清單控制項與 MFC 文件/檢視架構，封裝的控制類似[CEditView](../mfc/reference/ceditview-class.md)封裝編輯控制項： 控制項會填滿 MFC 檢視的整個介面區域。 (檢視*是*控制項，轉型為`CListView`。)  
  
 A`CListView`物件繼承自[CCtrlView](../mfc/reference/cctrlview-class.md)和它的基底類別，以及將成員函式來擷取基礎清單控制項。 使用檢視成員來運用檢視。 使用[GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl)成員函式來取得清單控制項的成員函式的存取。 使用這些成員：  
  
-   在清單中加入、刪除或操作「項目」。  
  
-   設定或取得清單控制項屬性。  
  
 若要取得以 `CListCtrl` 為基礎的 `CListView` 的參考，請從清單檢視類別呼叫 `GetListCtrl`：  
  
 [!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]  
  
 本主題說明兩種使用清單控制項的方式。  
  
## <a name="see-also"></a>請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)

