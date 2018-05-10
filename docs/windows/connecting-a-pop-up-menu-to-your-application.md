---
title: 快顯功能表連接至您的應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- pop-up menus, connecting to applications
- context menus, connecting to applications
- menus, pop-up
- shortcut menus, connecting to applications
ms.assetid: 295cbf0e-6416-478e-bc3d-472fb98e0e52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 533fc4eea9299d51183a91febb371ff8142e0a7b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="connecting-a-pop-up-menu-to-your-application"></a>將快顯功能表連接至您的應用程式
### <a name="to-connect-a-pop-up-menu-to-your-application"></a>將快顯功能表連接至您的應用程式  
  
1.  （例如） WM_CONTEXTMENU 加入訊息處理常式。 如需詳細資訊，請參閱[訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md)。  
  
2.  將下列程式碼加入至訊息處理常式：  
  
    ```  
    CMenu menu;  
    VERIFY(menu.LoadMenu(IDR_MENU1));  
    CMenu* pPopup = menu.GetSubMenu(0);  
    ASSERT(pPopup != NULL);  
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());  
    ```  
  
    > [!NOTE]
    >  [CPoint](../atl-mfc-shared/reference/cpoint-class.md) **傳遞的訊息處理常式是在螢幕座標。**  
  

  
 **需求**  
  
 MFC  
  
## <a name="see-also"></a>另請參閱  
 [建立快顯功能表](../windows/creating-pop-up-menus.md)   
 [功能表編輯器](../windows/menu-editor.md)   
