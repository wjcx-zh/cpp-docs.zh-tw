---
title: 與 Rich Edit 控制項相關的類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rich edit controls [MFC], and CRichEditItem
- CRichEditCtrl class [MFC], related classes
- CRichEditDoc class [MFC], Rich Edit controls
- rich edit controls [MFC], classes related to
- classes [MFC], related to rich edit controls
- rich edit controls [MFC], and CRichEditView
- CRichEditCtrlItem class and CRichEditCtrl
- rich edit controls [MFC], and CRichEditDoc
- CRichEditView class [MFC], and CRichEditCtrl
ms.assetid: 4b31c2cc-6ea1-4146-b7c5-b0b5b419f14d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f428242ac84adaf36ea0263f8e193dfeca7d0609
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341394"
---
# <a name="classes-related-to-rich-edit-controls"></a>與 Rich Edit 控制項相關的類別
[CRichEditView](../mfc/reference/cricheditview-class.md)， [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)，和[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)類別提供 windows rich edit 控制項的功能 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))在 MFC 的文件/檢視架構的內容。 `CRichEditView` 會維護文字和文字的格式特性。 `CRichEditDoc` 會維護檢視中的 OLE 用戶端項目的清單。 `CRichEditCntrItem` 提供 OLE 用戶端項目的存取權給容器端。 若要修改的內容`CRichEditView`，使用[cricheditview:: Getricheditctrl](../mfc/reference/cricheditview-class.md#getricheditctrl)來存取基礎 rich edit 控制項。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)

