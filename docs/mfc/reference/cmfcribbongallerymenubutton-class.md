---
title: "CMFCRibbonGalleryMenuButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonGalleryMenuButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonGalleryMenuButton class"
ms.assetid: 4d459d9b-8b1a-4371-92f6-dc4ce6cc42c8
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonGalleryMenuButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作包含功能區組件庫的功能區功能表按鈕。  
  
## 語法  
  
```  
class CMFCRibbonGalleryMenuButton : public CMFCToolBarMenuButton  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton](../Topic/CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton.md)|建構並初始化 `CMFCRibbonGalleryMenuButton` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonGalleryMenuButton::CopyFrom](../Topic/CMFCRibbonGalleryMenuButton::CopyFrom.md)|\(覆寫 [CMFCToolBarMenuButton::CopyFrom](../Topic/CMFCToolBarMenuButton::CopyFrom.md)。\)|  
|[CMFCRibbonGalleryMenuButton::CreatePopupMenu](../Topic/CMFCRibbonGalleryMenuButton::CreatePopupMenu.md)|\(覆寫 [CMFCToolBarMenuButton::CreatePopupMenu](../Topic/CMFCToolBarMenuButton::CreatePopupMenu.md)。\)|  
|[CMFCRibbonGalleryMenuButton::GetPalette](../Topic/CMFCRibbonGalleryMenuButton::GetPalette.md)||  
|[CMFCRibbonGalleryMenuButton::HasButton](../Topic/CMFCRibbonGalleryMenuButton::HasButton.md)|\(覆寫 `CMFCToolBarMenuButton::HasButton`。\)|  
|[CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed](../Topic/CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed.md)|\(覆寫 [CMFCToolBarMenuButton::IsEmptyMenuAllowed](../Topic/CMFCToolBarMenuButton::IsEmptyMenuAllowed.md)。\)|  
  
### 備註  
 組件庫功能表按鈕會顯示成含箭頭的快顯功能表。  當使用者按一下此按鈕時，會顯示影像庫。  當您建構組件庫功能表按鈕時，您必須指定包含這些影像的影像清單。  
  
## 範例  
 下列範例示範如何顯示功能表按鈕中項目符號的組件庫：  
  
```  
BOOL CMainFrame::OnShowPopupMenu (CMFCPopupMenu* pMenuPopup)  
{  
    int nBulletIndex = pMenuBar->CommandToIndex (ID_PARA_BULLETS);  
    if (nBulletIndex >= 0)  
    {  
        CMFCToolBarButton* pExButton =  
            pMenuBar->GetButton(nBulletIndex);  
        ASSERT_VALID (pExButton);  
        CMFCRibbonGalleryMenuButton paletteBullet (  
            pExButton->m_nID,  
            pExButton->GetImage (),  
            pExButton->m_strText);  
        InitBulletPalette (&paletteBullet.GetPalette ());  
        pMenuBar->ReplaceButton (ID_PARA_BULLETS, paletteBullet);  
    }  
}  
```  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) [CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md)  
  
## 需求  
 **標頭：**afxRibbonPaletteGallery.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md)   
 [CMFCRibbonGallery Class](../../mfc/reference/cmfcribbongallery-class.md)