---
title: HOW TO：從 MFC 應用程式載入功能區資源
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
ms.openlocfilehash: b7691d4168101209b0e2d2500012a2b4a8e47788
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289551"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>HOW TO：從 MFC 應用程式載入功能區資源

若要在應用程式中使用功能區資源，請修改應用程式以載入功能區資源。

### <a name="to-load-a-ribbon-resource"></a>載入功能區資源

1. 在 `Ribbon Control` 類別宣告 `CMainFrame` 物件。

```
    CMFCRibbonBar m_wndRibbonBar;
```

1. 在 `CMainFrame::OnCreate` 中，建立並初始化功能區控制項。

```
    if (!m_wndRibbonBar.Create (this))
{
    return -1;
}

    if (!m_wndRibbonBar.LoadFromResource(IDR_RIBBON))
{
    return -1;
}
```

## <a name="see-also"></a>另請參閱

[功能區設計工具 (MFC)](../mfc/ribbon-designer-mfc.md)
