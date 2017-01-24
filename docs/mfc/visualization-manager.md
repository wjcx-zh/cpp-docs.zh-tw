---
title: "視覺化管理員 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "視覺化管理員"
ms.assetid: c9dd1365-27ac-42e5-8caa-1004525b4129
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 視覺化管理員
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

視覺化管理員是物件控制整個應用程式的外觀。  為您可以將應用程式的任何繪圖程式碼的單一類別。  MFC 程式庫包含數個視覺化管理員。  如果您要建置應用程式，自訂檢視您也可以建立自己的視覺化管理員。  在不同的視覺化管理員啟用時，下圖顯示相同的應用程式:  
  
 ![由 CMFCVisualManagerWindows 呈現的 MyApp](../mfc/media/vmwindows.png "VMWindows")  
使用 CMFCVisualManagerWindows 視覺化管理員的 MyApp  
  
 ![由 CMFCVisualManagerVS2005 呈現的 MyApp](../mfc/media/vmvs2005.png "VMVS2005")  
使用 CMFCVisualManagerVS2005 視覺化管理員的 MyApp  
  
 ![由 CMFCVisualManagerOfficeXP 呈現的 MyApp](../mfc/media/vmofficexp.png "VMOfficeXP")  
使用 CMFCVisualManagerOfficeXP 視覺化管理員的 MyApp  
  
 ![由 CMFCVisualManagerOffice2003 呈現的 MyApp](../mfc/media/vmoffice2003.png "VMOffice2003")  
使用 CMFCVisualManagerOffice2003 視覺化管理員的 MyApp  
  
 ![由 CMFCVisualManagerOffice2007 呈現的 MyApp](../mfc/media/msoffice2007.png "MSOffice2007")  
使用 CMFCVisualManagerOffice2007 視覺化管理員的 MyApp  
  
 根據預設，視覺化管理員會維護幾個 GUI 項目的繪製程式碼。  若要提供自訂 UI 項目，您需要覆寫視覺管理員的相關繪圖方法。  如需這些方法的清單，請參閱 [CMFCVisualManager Class](../mfc/reference/cmfcvisualmanager-class.md)。  您可以覆寫提供自訂外觀的方法是以 `OnDraw`中的所有方法。  
  
 您的應用程式只能有一個 `CMFCVisualManager` 物件。  若要取得指標對應用程式的視覺化管理員，請呼叫靜態函式 [CMFCVisualManager::GetInstance](../Topic/CMFCVisualManager::GetInstance.md)。  由於所有視覺化管理員繼承自 `CMFCVisualManager`， `CMFCVisualManager::GetInstance` 方法會取得指標為適當的視覺化管理員，，即使您建立自訂視覺管理員。  
  
 如果您要建立自訂視覺管理員，您必須從已存在的一位視覺化管理員取得它。  取得的預設類別為 `CMFCVisualManager`。  不過，您可以使用一個不同的視覺化管理員，則較佳類似要為應用程式想要。  例如，在中，如果您要使用 `CMFCVisualManagerOffice2007` 視覺管理員，不過，只要變更分隔符號的外觀，您可以從 `CMFCVisualManagerOffice2007`衍生您自己的自訂類別。  在這個案例中，您應該覆寫繪製的分隔符號方法。  
  
 有兩種可能的方式為您的應用程式使用特定視覺化管理員。  一種方式是呼叫 [CMFCVisualManager::SetDefaultManager](../Topic/CMFCVisualManager::SetDefaultManager.md) 方法並傳遞這個適當的視覺化管理員做為參數。  下列程式碼範例顯示如何使用這個方法的 `CMFCVisualManagerVS2005` 視覺管理員:  
  
```  
CMFCVisualManager::SetDefaultManager (RUNTIME_CLASS (CMFCVisualManagerVS2005));  
```  
  
 另一種使用一個視覺化管理員在您的應用程式將手動建立它。  應用程式的所有轉換會使用這個新的視覺管理員。  不過，，因為只能有一個應用程式的 `CMFCVisualManager` 物件，您必須刪除目前視覺化管理員，在建立新的。  在下列範例中， `CMyVisualManager` 是從 `CMFCVisualManager`衍生的自訂視覺化管理員。  下列方法會根據索引將會變更哪些視覺管理員用來顯示應用程式，例如:  
  
```  
void CMyApp::SetSkin (int index)  
{  
   if (CMFCVisualManager::GetInstance() != NULL)  
   {  
      delete CMFCVisualManager::GetInstance();  
   }  
  
   switch (index)  
   {  
   case DEFAULT_STYLE:  
      // The following statement creates a new CMFCVisualManager  
      CMFCVisualManager::GetInstance();  
      break;  
  
   case CUSTOM_STYLE:  
      new CMyVisualManager;  
      break;  
  
   default:  
      CMFCVisualManager::GetInstance();  
      break;  
   }  
  
   CMFCVisualManager::GetInstance()->RedrawAll();  
}  
```  
  
## 請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)   
 [CMFCVisualManager Class](../mfc/reference/cmfcvisualmanager-class.md)