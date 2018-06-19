---
title: 追蹤器 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- trackers [MFC]
- OLE applications [MFC], trackers
- applications [OLE], trackers
- tracking OLE items [MFC]
- OLE containers [MFC], trackers
- CDC class [MFC], trackers
- CRectTracker class [MFC], implementing trackers
- OLE server applications [MFC], trackers
ms.assetid: dcd09399-6637-4621-80e5-d12670429787
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f0a0cc52e3a5150702af4acd293def38df758fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381533"
---
# <a name="trackers"></a>追蹤器
[CRectTracker](../mfc/reference/crecttracker-class.md)類別會提供您的應用程式和您的使用者，藉由提供各種不同的顯示樣式中的矩形項目之間的使用者介面。 這些樣式包含實線、 影線，或虛線框線;包含陰影的模式，它涵蓋了項目;可位於外部或內部框線的調整大小控點。 追蹤器通常用於搭配 OLE 項目，也就是物件衍生自`COleClientItem`。 追蹤程式矩形提供項目的目前狀態的視覺提示。  
  
 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)示範如何使用追蹤器與 OLE 用戶端項目的觀點來看從容器應用程式的通用介面。 如需示範不同的樣式和追蹤器物件的能力，請參閱 MFC 一般範例[TRACKER](../visual-cpp-samples.md)。  
  
 如需有關 OLE 應用程式中實作追蹤器的詳細資訊，請參閱[追蹤器： 實作 OLE 應用程式中的追蹤器](../mfc/trackers-implementing-trackers-in-your-ole-application.md)  
  
## <a name="see-also"></a>另請參閱  
 [OLE](../mfc/ole-in-mfc.md)   
 [COleClientItem 類別](../mfc/reference/coleclientitem-class.md)
