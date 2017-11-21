---
title: "橡皮框和追蹤器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- trackers [MFC]
- CRectTracker class [MFC], implementing trackers
- OLE objects [MFC], selecting
- rubber banding [MFC]
- WM_LBUTTONDOWN [MFC]
ms.assetid: 0d0fa64c-6418-4baf-ab7f-2d16ca039230
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 40ff1d5bf9e1514b8366cc113426ee83cb1dcc39
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="rubber-banding-and-trackers"></a>拖放矩形和追蹤器
另一個追蹤器隨附的功能是「拖放矩形」選取範圍，可讓使用者透過在要選取的項目附近拖曳縮放矩形來選取多個 OLE 項目。 當使用者放開滑鼠左鍵時，將會選取使用者在區域中選取的項目，並可供使用者操作。 例如，使用者可以將選取項目拖曳到另一個容器應用程式。  
  
 您的應用程式的 `WM_LBUTTONDOWN` 處理函式中必須有一些額外的程式碼，才能實作這項功能。  
  
 下列程式碼範例實作拖放矩形選取範圍和其他功能。  
  
 [!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/cpp/rubber-banding-and-trackers_1.cpp)]  
  
 如果您想要允許還原方向追蹤程式的拖放矩形期間，您應該呼叫[crecttracker:: Trackrubberband](../mfc/reference/crecttracker-class.md#trackrubberband)並第三個參數設定為**TRUE**。 請記住，允許還原方向有時候會使[crecttracker:: M_rect](../mfc/reference/crecttracker-class.md#m_rect)反轉。 這可由呼叫更正[Normalizerect](../atl-mfc-shared/reference/crect-class.md#normalizerect)。  
  
 如需詳細資訊，請參閱[容器用戶端項目](../mfc/containers-client-items.md)和[自訂拖放](../mfc/drag-and-drop-customizing.md)。  
  
## <a name="see-also"></a>另請參閱  
 [追蹤器： OLE 應用程式中實作追蹤器](../mfc/trackers-implementing-trackers-in-your-ole-application.md)   
 [CRectTracker 類別](../mfc/reference/crecttracker-class.md)
