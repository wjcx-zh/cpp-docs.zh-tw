---
title: 控制項名稱，MFC ActiveX 控制項精靈 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.ctl.names
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d8342c76e58b5d21f36147f073e1380fbad15bd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712110"
---
# <a name="control-names-mfc-activex-control-wizard"></a>MFC ActiveX 控制項精靈、控制項名稱
指定控制項類別和屬性頁類別，型別名稱的名稱和型別識別項，為您的控制項。 除了**簡短名稱**，可獨立編輯所有其他欄位。 如果您變更的文字**簡短名稱**，變更會反映在這個頁面中的所有其他欄位的名稱。 此命名的行為可讓您開發您的控制項時輕鬆地識別所有的名稱。  
  
- **簡短名稱**

   提供控制項的縮寫的名稱。 根據預設，這個名稱會根據您在中提供的專案名稱**新的專案** 對話方塊。 您提供的名稱會決定類別名稱、 型別名稱和型別識別項，除非您個別變更這些欄位。  
  
- **控制項類別名稱**

   根據預設，控制項類別的名稱為根據的簡短名稱，與`C`做為前置詞和`Ctrl`做為尾碼。 例如，如果您的控制項的簡短名稱是`Price`，控制項類別名稱是`CPriceCtrl`。  
  
- **控制項.h 檔案**

   根據預設，標頭檔的名稱為根據的簡短名稱，與`Ctrl`做為尾碼和`.h`做為副檔名。 例如，如果您的控制項的簡短名稱是`Price`，標頭檔名稱是`PriceCtrl.h`。 此欄位中的名稱應符合控制項類別名稱。  
  
- **控制項.cpp 檔案**

   根據預設，標頭檔的名稱為根據的簡短名稱，與`Ctrl`做為尾碼和`.cpp`做為副檔名。 例如，如果您的控制項的簡短名稱是`Price`，標頭檔名稱是`PriceCtrl.cpp`。 此欄位中的名稱應該符合的標頭名稱。  
  
- **控制項型別名稱**

   根據預設，控制項類型的名稱根據簡短名稱，後面接著`Control`。 例如，如果您的控制項的簡短名稱是`Price`，控制項類別的型別名稱是`Price Control`。 如果您變更此欄位中的值，請確定名稱指出繼承。  
  
- **控制項類型識別碼**

   設定控制項類別的控制項型別 ID。 控制項可將此字串寫入至登錄，而當它新增至專案時。 容器應用程式會使用此字串來建立控制項的執行個體。  
  
   根據預設，控制項類型識別碼根據專案名稱，也就是您指示中**新的專案** 對話方塊中，而是簡短名稱。 這個名稱應該符合的型別名稱。  
  
   依預設，控制項類型識別碼出現，如下所示：  
  
   *ProjectName.ShortName*Ctrl.1  
  
   如果您變更的簡短名稱，在此對話方塊中，控制項類型識別碼會出現，如下所示：  
  
   *ProjectName.NewShortName*Ctrl.1  
  
- **PropPage 類別名稱**

   根據預設，屬性頁類別的名稱為根據的簡短名稱，與`C`做為前置詞和`PropPage`做為尾碼。 例如，如果您的控制項的簡短名稱是`Price`，屬性頁類別名稱是`CPricePropPage`。 此名稱應符合控制項類別名稱，加上`PropPage`。  
  
- **PropPage.h 檔案**

   根據預設，屬性頁標頭檔的名稱為根據的簡短名稱，以`PropPage`做為尾碼和`.h`做為副檔名。 例如，如果您的控制項的簡短名稱是`Price`，屬性頁面標頭檔名稱是`PricePropPage.h`。 此名稱應該符合類別名稱。  
  
- **PropPage.cpp 檔案**

   根據預設，屬性頁的實作檔的名稱為根據的簡短名稱，以`PropPage`做為尾碼和`.cpp`做為副檔名。 例如，如果您的控制項的簡短名稱是`Price`，屬性頁面標頭檔名稱是`PricePropPage.cpp`。 此名稱應該符合標頭檔名稱。  
  
- **PropPage 類型名稱**

   根據預設，屬性頁的型別名稱根據簡短名稱，後面接著`Property Page`。 例如，如果您的控制項的簡短名稱是`Price`，屬性頁的型別名稱是`Price Property Page`。 如果您變更此欄位中的值，請確定名稱表示控制項類別。  
  
- **PropPage 類型識別碼**

   設定屬性頁類別的識別碼。 控制項套用至專案時，將此字串寫入登錄中。 容器應用程式會使用此字串來建立控制項的屬性頁的執行個體。  
  
   根據預設，屬性頁類型 ID 根據專案名稱，也就是您指示中**新的專案** 對話方塊中，而是簡短名稱。 這個名稱應該符合的型別名稱。  
  
   根據預設，屬性頁類型 ID 看起來像這樣：  
  
   *ProjectName.ShortName*PropPage.1  
  
   如果您變更的簡短名稱，在此對話方塊中，屬性頁類型 ID 會出現，如下所示：  
  
   *ProjectName.NewShortName*PropPage.1  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項精靈](../../mfc/reference/mfc-activex-control-wizard.md)   
 [MFC ActiveX 控制項精靈、 應用程式設定](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [MFC ActiveX 控制項精靈、 控制項設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)   
 [為 Visual C++ 專案建立的檔案類型](../../ide/file-types-created-for-visual-cpp-projects.md)

