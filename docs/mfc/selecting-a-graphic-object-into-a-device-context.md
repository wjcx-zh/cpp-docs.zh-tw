---
title: 選取圖形物件放入裝置內容 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- graphic objects [MFC], selecting into device context
- SelectObject method [MFC]
- GDI objects [MFC], device contexts
- lifetime, graphic objects [MFC]
- device contexts, selecting graphic objects into
- device contexts, graphic objects [MFC]
ms.assetid: cf54a330-63ef-421f-83eb-90ec7bd82eef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc605be317d51c985e32fbad038d846b056e5fe6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379680"
---
# <a name="selecting-a-graphic-object-into-a-device-context"></a>選取圖形物件放入裝置內容中
本主題適用於使用中視窗的裝置內容的圖形物件。 之後您[建立繪圖物件](../mfc/one-stage-and-two-stage-construction-of-objects.md)，您必須放入裝置內容，來取代預設的物件儲存於該處選取它：  
  
 [!code-cpp[NVC_MFCDocViewSDI#7](../mfc/codesnippet/cpp/selecting-a-graphic-object-into-a-device-context_1.cpp)]  
  
## <a name="lifetime-of-graphic-objects"></a>圖形物件的存留期  
 所傳回的圖形物件[SelectObject](../mfc/reference/cdc-class.md#selectobject)是 「 暫時性 」。 也就是說，它會刪除[OnIdle](../mfc/reference/cwinapp-class.md#onidle)類別成員函式`CWinApp`的下次程式取得閒置時間。 只要您使用所傳回的物件`SelectObject`中沒有將控制權傳回給主要訊息迴圈的單一函式，您將不會有問題。  
  
### <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [圖形物件](../mfc/graphic-objects.md)  
  
-   [一階段和兩階段的圖形物件建構](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [裝置內容](../mfc/device-contexts.md)  
  
-   [在檢視中繪圖](../mfc/drawing-in-a-view.md)  
  
## <a name="see-also"></a>另請參閱  
 [圖形物件](../mfc/graphic-objects.md)

