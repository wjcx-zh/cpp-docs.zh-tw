---
title: 如何： 從 MFC 應用程式載入功能區資源 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b014e1725ae6c5043c051242a74e29338c3ef2d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>如何：從 MFC 應用程式載入功能區應用程式
若要在應用程式中使用功能區資源，請修改應用程式以載入功能區資源。  
  
### <a name="to-load-a-ribbon-resource"></a>載入功能區資源  
  
1.  在 `Ribbon Control` 類別宣告 `CMainFrame` 物件。  
  
 ```  
    CMFCRibbonBar m_wndRibbonBar;   
 ```  
  
2.  在 `CMainFrame::OnCreate` 中，建立並初始化功能區控制項。  
  
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

