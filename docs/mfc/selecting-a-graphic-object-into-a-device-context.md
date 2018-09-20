---
title: 選取圖形物件放入裝置內容 |Microsoft Docs
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
ms.openlocfilehash: 406c4e7cd87b350f9317022dcf1821fa92ddf4af
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427663"
---
# <a name="selecting-a-graphic-object-into-a-device-context"></a>選取圖形物件放入裝置內容中

本主題適用於使用視窗的裝置內容中的 圖形物件。 之後您[建立繪圖物件](../mfc/one-stage-and-two-stage-construction-of-objects.md)，您就必須放入裝置內容，來取代預設的物件儲存在該處選取它：

[!code-cpp[NVC_MFCDocViewSDI#7](../mfc/codesnippet/cpp/selecting-a-graphic-object-into-a-device-context_1.cpp)]

## <a name="lifetime-of-graphic-objects"></a>圖形物件的存留期

所傳回的圖形物件[SelectObject](../mfc/reference/cdc-class.md#selectobject)是 「 暫時性 」。 也就是說，它會刪除[OnIdle](../mfc/reference/cwinapp-class.md#onidle)類別成員函式`CWinApp`的下次程式取得閒置時間。 只要您使用所傳回的物件`SelectObject`沒有將控制權傳回給主訊息迴圈的單一函式，在中，您會有任何問題。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [圖形物件](../mfc/graphic-objects.md)

- [一階段和兩階段的圖形物件建構](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [裝置內容](../mfc/device-contexts.md)

- [在檢視中繪圖](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>另請參閱

[圖形物件](../mfc/graphic-objects.md)

