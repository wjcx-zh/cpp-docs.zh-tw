---
title: 如何：從 MFC 應用程式載入功能區應用程式
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
ms.openlocfilehash: 14ba37952d6f8849c51b36901a6bc17404f938e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515150"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>如何：從 MFC 應用程式載入功能區應用程式

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

