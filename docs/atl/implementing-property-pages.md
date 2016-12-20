---
title: "Implementing Property Pages | Microsoft Docs"
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
  - "IPropertyPage class"
  - "IPropertyPage2 class"
  - "屬性頁, 實作"
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementing Property Pages
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

屬性頁是實作 `IPropertyPage` 或 **IPropertyPage2** 介面的 COM 物件。  ATL 提供用於實作屬性頁的支援傳入的 [加入類別對話方塊。](../ide/add-class-dialog-box.md)[ATL 屬性頁精靈](../atl/reference/atl-property-page-wizard.md) 。  
  
 使用，建立 ATL 屬性頁:  
  
-   建立或開啟 ATL 動態連結程式庫 \(DLL\) \(DLL\) 伺服器專案。  
  
-   開啟 [加入類別對話方塊。](../ide/add-class-dialog-box.md) 並選取 **ATL 屬性頁**。  
  
-   請確定您的屬性頁是執行緒 Apartment \(因為它有使用者介面\)。  
  
-   設定與關聯的標題、描述文件 \(字串\) 和說明檔與您的頁面。  
  
-   將控制項加入至產生的對話方塊資源做為屬性頁的使用者介面。  
  
-   回應在頁面的使用者介面的變更執行驗證時，更新頁面網站或更新物件與您的頁面。  特別是，呼叫 [IPropertyPageImpl::SetDirty](../Topic/IPropertyPageImpl::SetDirty.md) ，當使用者對屬性頁的變更。  
  
-   您也可以選擇覆寫方法 `IPropertyPageImpl` 使用下列方針。  
  
    |IPropertyPageImpl 方法|覆寫，在您想要…|備註|  
    |--------------------------|--------------|--------|  
    |[SetObjects](../Topic/IPropertyPageImpl::SetObjects.md)|對傳遞至其所支援之網頁和介面之物件數目的基本號上清除  核取方塊。|在呼叫基底類別的實作之前執行自己的程式碼。  如果設定的物件不符合您的預期，您應該盡快會使呼叫失敗。|  
    |[啟動](../Topic/IPropertyPageImpl::Activate.md)|初始化頁面的使用者介面 \(例如，會使用目前屬性值的對話方塊控制項從物件，動態建立控制項或執行其他初始設定\)。|在您的程式碼之前呼叫基底類別實作，讓基底類別有機會建立對話方塊視窗和所有控制項，在您嘗試更新這些檔案。|  
    |[套用](../Topic/IPropertyPageImpl::Apply.md)|驗證屬性設定為並更新物件。|因為它不會執行任何東西來追蹤超出這個呼叫，不必呼叫基底類別 \(Base Class\) 實作。|  
    |[停用。](../Topic/IPropertyPageImpl::Deactivate.md)|清除與視窗相關的項目。|基底類別實作終結表示屬性頁的  對話方塊。  如果您需要清除，再終結此對話方塊，您應該在呼叫基底類別的前面加入您的程式碼。|  
  
 如需範例屬性頁實作，請參閱 [範例:實作屬性頁](../atl/example-implementing-a-property-page.md)。  
  
> [!NOTE]
>  如果要裝載在屬性頁的 ActiveX 控制項，您將需要變更您的精靈產生之類別的衍生。  在基底類別清單中的 **CAxDialogImpl\<CYourClass\>** 取代 **CDialogImpl\<CYourClass\>** 。  
  
## 請參閱  
 [屬性頁](../atl/atl-com-property-pages.md)   
 [ATLPages 範例](../top/visual-cpp-samples.md)