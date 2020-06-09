---
title: 與 Rich Edit 控制項相關的類別
ms.date: 11/04/2016
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
ms.openlocfilehash: 584649a2bb2d9a118e390aebf9f7411c3123b1a3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620718"
---
# <a name="classes-related-to-rich-edit-controls"></a>與 Rich Edit 控制項相關的類別

[CRichEditView](reference/cricheditview-class.md)、 [CRichEditDoc](reference/cricheditdoc-class.md)和[CRichEditCntrItem](reference/cricheditcntritem-class.md)類別會在 MFC 的檔/視圖架構內容中提供 rich edit 控制項（[CRichEditCtrl](reference/cricheditctrl-class.md)）的功能。 `CRichEditView` 會維護文字和文字的格式特性。 `CRichEditDoc` 會維護檢視中的 OLE 用戶端項目的清單。 `CRichEditCntrItem` 提供 OLE 用戶端項目的存取權給容器端。 若要修改的內容 `CRichEditView` ，請使用[CRichEditView：： GetRichEditCtrl](reference/cricheditview-class.md#getricheditctrl)來存取基礎 rich edit 控制項。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](using-cricheditctrl.md)<br/>
[控制項](controls-mfc.md)
