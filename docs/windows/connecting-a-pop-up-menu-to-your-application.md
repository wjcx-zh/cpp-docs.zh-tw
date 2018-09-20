---
title: 將快顯功能表連接至您的 c + + 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- menus [C++], pop-up
- shortcut menus [C++], connecting to applications
ms.assetid: 295cbf0e-6416-478e-bc3d-472fb98e0e52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f1ebb5e2151fe770e6a59210ac564237155fafd4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412076"
---
# <a name="connecting-a-pop-up-menu-to-your-c-application"></a>將快顯功能表連接至您的 c + + 應用程式

### <a name="to-connect-a-pop-up-menu-to-your-application"></a>將快顯功能表連接至您的應用程式

1. （舉例來說） WM_CONTEXTMENU 新增的訊息處理常式。 如需詳細資訊，請參閱 <<c0> [ 將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md)。

2. 將下列程式碼加入至訊息處理常式：

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > [CPoint](../atl-mfc-shared/reference/cpoint-class.md)傳遞的訊息處理常式是在螢幕座標。

## <a name="requirements"></a>需求

MFC

## <a name="see-also"></a>另請參閱

[建立快顯功能表](../windows/creating-pop-up-menus.md)<br/>
[功能表編輯器](../windows/menu-editor.md)  