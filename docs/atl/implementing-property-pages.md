---
title: 實作屬性頁 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1db6ca4ea374cd76d5b0e1df8e6c0cd03474fdf2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="implementing-property-pages"></a>實作屬性頁
屬性頁可讓您為 COM 物件實作`IPropertyPage`或**IPropertyPage2**介面。 ATL 提供實作透過屬性頁支援[ATL 屬性頁精靈](../atl/reference/atl-property-page-wizard.md)中[加入類別對話方塊](../ide/add-class-dialog-box.md)。  
  
 若要建立使用 ATL 屬性頁：  
  
-   建立或開啟 ATL 動態連結程式庫 (DLL) 的伺服器專案。  
  
-   開啟[加入類別對話方塊](../ide/add-class-dialog-box.md)選取**ATL 屬性頁**。  
  
-   請確定您屬性頁 apartment 執行緒 （因為它有使用者介面）。  
  
-   設定標題、 描述 （文件字串），以及要與頁面相關聯的說明檔。  
  
-   將控制項加入至產生的對話方塊資源做為使用者介面的屬性頁。  
  
-   回應您的頁面使用者介面來執行驗證、 更新頁面的網站，或更新與頁面相關聯的物件中的變更。 特別是，呼叫[IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty)當使用者變更屬性頁。  
  
-   選擇性地覆寫`IPropertyPageImpl`方法使用下列指導方針。  
  
    |IPropertyPageImpl 方法|當您想要覆寫...|注意|  
    |------------------------------|----------------------------------|-----------|  
    |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|執行基本的例行性檢查傳遞給您的頁面和它們所支援之介面的物件數目。|執行您自己的程式碼，然後再呼叫基底類別實作。 如果所設定的物件不符合您的預期，您應儘速失敗呼叫。|  
    |[啟動](../atl/reference/ipropertypageimpl-class.md#activate)|初始化頁面的使用者介面 （例如，從物件設定與目前的屬性值的對話方塊控制項、 控制項，動態建立或執行其他初始設定）。|呼叫基底類別實作您的程式碼之前，讓基底類別有機會建立對話方塊視窗和所有控制項，再重新加以更新。|  
    |[適用於](../atl/reference/ipropertypageimpl-class.md#apply)|驗證的屬性設定，然後更新的物件。|沒有需要呼叫基底類別實作，因為它只負責追蹤呼叫。|  
    |[停用](../atl/reference/ipropertypageimpl-class.md#deactivate)|清除與視窗相關項目。|基底類別實作會終結代表屬性頁對話方塊。 如果您需要清除，再終結對話方塊時，您應該加入程式碼，然後再呼叫基底類別。|  
  
 屬性頁面上執行範例，請參閱[範例： 實作屬性頁](../atl/example-implementing-a-property-page.md)。  
  
> [!NOTE]
>  如果您想要裝載 ActiveX 控制項屬性頁中，您必須變更您精靈產生的類別衍生。 取代**CDialogImpl\<CYourClass >** 與**CAxDialogImpl\<CYourClass >** 基底類別清單中。  
  
## <a name="see-also"></a>另請參閱  
 [屬性頁](../atl/atl-com-property-pages.md)   
 [ATLPages 範例](../visual-cpp-samples.md)

