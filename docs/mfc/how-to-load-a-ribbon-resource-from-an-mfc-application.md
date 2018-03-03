---
title: "如何： 從 MFC 應用程式載入功能區資源 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6a943f82fc9b438a74af3673e0210612183304c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [功能區設計工具 (MFC)](../mfc/ribbon-designer-mfc.md)

