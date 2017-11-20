---
title: "如何： 從 MFC 應用程式載入功能區資源 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2384ff8b92936e646bc434583c6a20e07ccc85e7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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

