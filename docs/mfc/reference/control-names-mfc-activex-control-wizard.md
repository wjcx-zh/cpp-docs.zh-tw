---
title: "控制項名稱，MFC ActiveX 控制項精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.ctl.names
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5f3444ec69ea96ee89ed7a0965f3575fc79e3b9c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="control-names-mfc-activex-control-wizard"></a>MFC ActiveX 控制項精靈、控制項名稱
指定之名稱的控制項類別和屬性頁類別的型別名稱，並輸入您的控制項的識別項。 除了**簡短名稱**，單獨進行編輯的所有其他欄位。 如果您變更的文字**簡短名稱**，變更會反映在此頁面中的所有其他欄位的名稱。 這項命名行為被為了讓您開發您的控制項時容易識別的所有名稱。  
  
 **簡短名稱**  
 提供控制項的縮寫的名稱。 根據預設，這個名稱會根據您在中提供的專案名稱上**新專案** 對話方塊。 您提供的名稱判斷類別名稱、 型別名稱和類型識別項，除非您個別變更這些欄位。  
  
 **控制項類別名稱**  
 根據預設的控制項類別名稱根據簡短名稱，與`C`做為前置詞和`Ctrl`做為尾碼。 例如，如果您的控制項的簡短名稱是`Price`，控制項類別名稱是`CPriceCtrl`。  
  
 **控制.h 檔案**  
 根據預設，標頭檔的名稱根據簡短名稱，與`Ctrl`做為尾碼和`.h`做為副檔名。 例如，如果您的控制項的簡短名稱是`Price`，標頭檔名稱是`PriceCtrl.h`。 此欄位中的名稱應符合控制項類別名稱。  
  
 **控制.cpp 檔案**  
 根據預設，標頭檔的名稱根據簡短名稱，與`Ctrl`做為尾碼和`.cpp`做為副檔名。 例如，如果您的控制項的簡短名稱是`Price`，標頭檔名稱是`PriceCtrl.cpp`。 此欄位中的名稱應該符合的標頭名稱。  
  
 **控制項型別名稱**  
 根據預設，控制項類型的名稱根據簡短名稱，後面接著`Control`。 例如，如果您的控制項的簡短名稱是`Price`，控制項的類別類型名稱是`Price Control`。 如果您變更此欄位中的值，請確定此名稱指出繼承。  
  
 **控制項類型識別碼**  
 設定控制項類別的控制項類型識別碼。 控制項加入至專案時，將此字串寫入至登錄。 容器應用程式會使用這個字串，來建立控制項的執行個體。  
  
 根據預設，控制項類型識別碼根據專案名稱，也就是您指示中**新專案**對話方塊中，以及簡短名稱。 這個名稱應該符合的型別名稱。  
  
 根據預設，控制項類型 ID 會顯示如下：  
  
 *ProjectName.ShortName*Ctrl.1  
  
 如果您變更的簡短名稱，在此對話方塊中，控制項類型識別碼會出現，如下所示：  
  
 *ProjectName.NewShortName*Ctrl.1  
  
 **屬性頁類別名稱**  
 根據預設，屬性頁類別的名稱根據簡短名稱，與`C`做為前置詞和`PropPage`做為尾碼。 例如，如果您的控制項的簡短名稱是`Price`，屬性頁類別名稱是`CPricePropPage`。 此名稱應符合控制項類別名稱，加上`PropPage`。  
  
 **屬性頁.h 檔案**  
 根據預設，屬性頁標頭檔的名稱為根據的簡短名稱，以`PropPage`做為尾碼和`.h`做為副檔名。 例如，如果您的控制項的簡短名稱是`Price`，屬性頁面標頭檔名稱是`PricePropPage.h`。 此名稱必須符合類別名稱。  
  
 **屬性頁.cpp 檔案中**  
 根據預設，屬性頁的實作檔的名稱為根據的簡短名稱，以`PropPage`做為尾碼和`.cpp`做為副檔名。 例如，如果您的控制項的簡短名稱是`Price`，屬性頁面標頭檔名稱是`PricePropPage.cpp`。 此名稱必須符合標頭檔名稱。  
  
 **屬性頁的型別名稱**  
 根據預設，屬性頁的型別名稱根據簡短名稱，後面接著`Property Page`。 例如，如果您的控制項的簡短名稱是`Price`，屬性頁的型別名稱是`Price Property Page`。 如果您變更此欄位中的值，請確定名稱會表示控制項類別。  
  
 **屬性頁類型識別碼**  
 設定屬性頁類別的識別碼。 控制項將套用至專案時，在登錄中寫入這個字串。 容器應用程式會使用這個字串建立的控制項屬性頁的執行個體。  
  
 根據預設，屬性頁類型 ID 根據專案名稱，也就是您指示中**新專案**對話方塊中，以及簡短名稱。 這個名稱應該符合的型別名稱。  
  
 根據預設，屬性頁類型 ID 會顯示如下：  
  
 *ProjectName.ShortName*PropPage.1  
  
 如果您變更此對話方塊中的簡短名稱，屬性頁類型 ID 會出現，如下所示：  
  
 *ProjectName.NewShortName*PropPage.1  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項精靈](../../mfc/reference/mfc-activex-control-wizard.md)   
 [MFC ActiveX 控制項精靈、 應用程式設定](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [MFC ActiveX 控制項精靈、 控制項設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)   
 [為 Visual C++ 專案建立的檔案類型](../../ide/file-types-created-for-visual-cpp-projects.md)

