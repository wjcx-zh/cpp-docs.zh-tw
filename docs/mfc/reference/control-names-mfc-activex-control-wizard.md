---
title: "MFC ActiveX 控制項精靈、控制項名稱 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.ctl.names"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC ActiveX 控制項精靈, 控制項名稱"
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項精靈、控制項名稱
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定控制項類別和屬性頁類別的名稱、控制項的型別名稱及型別識別項。  除了 \[簡短名稱\] 之外，所有其他欄位都可以單獨地進行編輯。  如果您變更 \[簡短名稱\] 當中的文字，這個頁面中所有其他欄位的名稱也都將反映此變更。  這項命名行為可讓您在開發控制項時能更容易識別所有的名稱。  
  
 **簡短名稱**  
 提供控制項的縮寫名稱。  依照預設，這個名稱是根據您在**新增專案**對話方塊中提供的專案名稱而定。  您所提供的名稱將決定類別名稱、型別名稱及型別識別項，除非您個別變更這些欄位。  
  
 **控制項類別名稱**  
 依照預設，控制項類別的名稱是根據簡短名稱而定，以 `C` 開頭並以 `Ctrl` 結尾。  例如，如果控制項的簡短名稱是 `Price`，則控制項類別名稱就是 `CPriceCtrl`。  
  
 **控制項 .h 檔案**  
 依照預設，標頭檔的名稱是根據簡短名稱而定，以 `Ctrl` 為結尾，而且副檔名為 `.h`。  例如，如果控制項的簡短名稱是 `Price`，則標頭檔名稱就是 `PriceCtrl.h`。  此一欄位中的名稱應符合控制項類別名稱。  
  
 **控制項 .cpp 檔案**  
 依照預設，標頭檔的名稱是根據簡短名稱而定，以 `Ctrl` 為結尾，而且副檔名為 `.cpp`。  例如，如果控制項的簡短名稱是 `Price`，則標頭檔名稱就是 `PriceCtrl.cpp`。  此一欄位中的名稱應符合標頭名稱。  
  
 **控制項型別名稱**  
 依照預設，控制項型別的名稱是根據簡短名稱而定，後面接著 `Control`。  例如，如果控制項的簡短名稱是 `Price`，則控制項類別的型別名稱就是 `Price Control`。  如果變更這個欄位中的值，請確定名稱會反應出繼承 \(Inheritance\)。  
  
 **控制項型別 ID**  
 設定控制項類別的控制項型別 ID。  當加入至專案時，控制項會將這個字串寫入登錄。  容器應用程式 \(Container Application\) 會使用這個字串來建立控制項的執行個體。  
  
 依照預設，控制項型別 ID 是根據專案名稱以及簡短名稱而定，專案名稱也就是您在 \[**新增專案**\] 對話方塊中指示的名稱。  這個名稱應與型別名稱相符。  
  
 控制項型別 ID 依預設會顯示如下：  
  
 *ProjectName*.*ShortName*Ctrl.1  
  
 如果變更這個對話方塊中的簡短名稱，控制項型別 ID 則會顯示如下：  
  
 *ProjectName*.*NewShortName*Ctrl.1  
  
 **屬性頁類別名稱**  
 依照預設，屬性頁類別的名稱是根據簡短名稱而定，以 `C` 開頭並以 `PropPage` 結尾。  例如，如果控制項的簡短名稱是 `Price`，則屬性頁的類別名稱就是 `CPricePropPage`。  這個名稱應與控制項類別名稱相符，後面附加 `PropPage`。  
  
 **屬性頁 .h 檔案**  
 依照預設，屬性頁標頭檔的名稱是根據簡短名稱而定，以 `PropPage` 為結尾，而且副檔名為 `.h`。  例如，如果控制項的簡短名稱是 `Price`，則屬性頁的標頭檔名稱就是 `PricePropPage.h`。  這個名稱應與類別名稱相符。  
  
 **屬性頁 .cpp 檔案**  
 依照預設，屬性頁實作檔的名稱是根據簡短名稱而定，以 `PropPage` 結尾，而且副檔名為 `.cpp`。  例如，如果控制項的簡短名稱是 `Price`，則屬性頁的標頭檔名稱就是 `PricePropPage.cpp`。  這個名稱應與標頭檔名稱相符。  
  
 **屬性頁型別名稱**  
 依照預設，屬性頁型別名稱是根據簡短名稱而定，後面接著 `Property Page`。  例如，如果控制項的簡短名稱是 `Price`，則屬性頁的型別名稱就是 `Price Property Page`。  如果變更這個欄位中的值，請確定名稱會反映控制項類別。  
  
 **屬性頁型別 ID**  
 設定屬性頁類別的 ID。  當套用至專案時，控制項會將這個字串寫入登錄。  容器應用程式會使用這個字串來建立控制項屬性頁的執行個體。  
  
 依照預設，屬性頁型別 ID 是根據專案名稱以及簡短名稱而定，專案名稱也就是您在 \[**新增專案**\] 對話方塊中指示的名稱。  這個名稱應與型別名稱相符。  
  
 屬性頁型別 ID 依預設會顯示如下：  
  
 *ProjectName*.*ShortName*PropPage.1  
  
 如果變更這個對話方塊中的簡短名稱，屬性頁型別 ID 則會顯示如下：  
  
 *ProjectName*.*NewShortName*PropPage.1  
  
## 請參閱  
 [MFC ActiveX 控制項精靈](../../mfc/reference/mfc-activex-control-wizard.md)   
 [應用程式設定，MFC ActiveX 控制項精靈](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [MFC ActiveX 控制項精靈、控制項設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)   
 [為 Visual C\+\+ 專案建立的檔案類型](../../ide/file-types-created-for-visual-cpp-projects.md)