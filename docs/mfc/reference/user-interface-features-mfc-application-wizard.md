---
title: "MFC 應用程式精靈、 使用者介面功能 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.exe.ui
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, user interface features
ms.assetid: 59e7b829-a665-42eb-be23-3f2a36eb2dad
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 80513d5f6b8dff5b8108a5b80f1d8db1e53d0ea0
ms.lasthandoff: 02/24/2017

---
# <a name="user-interface-features-mfc-application-wizard"></a>MFC 應用程式精靈、使用者介面功能
本主題說明您可用來指定應用程式外觀的選項。 可用於專案的使用者介面功能取決於應用程式中所指定的類型[MFC 應用程式精靈、 應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)MFC 應用程式精靈頁面。 比方說，如果您建立單一文件介面應用程式時，您無法加入子框架樣式。  
  
 **主框架樣式**  
 設定您的應用程式主視窗框架的功能。  
  
|選項|描述|  
|------------|-----------------|  
|**粗框架**|建立有調整大小框線的視窗。 預設值。|  
|**最小化方塊**|包含在主框架視窗的最小化方塊。 預設值。|  
|**最大化方塊**|在主框架視窗包含最大化的方塊。 預設值。|  
|**最小化**|以圖示開啟主框架視窗。|  
|**最大化**|開啟以顯示完整大小的主框架視窗。|  
|**系統功能表**|在主框架視窗包含系統功能表。 預設值。|  
|**關於方塊**|包含**有關**應用程式 方塊中的。 使用者可以從應用程式的存取這個方塊**協助**功能表。 預設值，且不能變更，除非您選取**對話方塊架構**，請在[MFC 應用程式精靈、 應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)頁面。<br /><br /> **請注意**通常無法使用的選項表示精靈不會套用選項至專案，將無法使用項目的核取方塊為選取或清除。 在此情況下，精靈永遠會加入**有關**方塊至專案，除非您先指定專案為基礎的對話方塊，然後取消核取方塊。|  
|**初始狀態列**|將狀態列加入至您的應用程式。 狀態列包含自動標記鍵盤的 CAPS LOCK、 NUM LOCK 和 SCROLL LOCK 鍵，並顯示 [說明] 訊息列字串的功能表命令和工具列按鈕。 按一下此選項時，也會將功能表命令，以顯示或隱藏狀態列。 根據預設，應用程式的狀態列。 不能用於對話方塊架構應用程式類型。|  
|**分隔視窗**|提供分隔器列。 分隔列分隔應用程式的主要檢視中。 在多個文件介面 (MDI) 應用程式中，MDI 子框架的用戶端視窗為分隔視窗中，而在單一文件介面 (SDI) 應用程式和多個最上層文件應用程式中，主框架的用戶端視窗為分隔視窗。 不能用於對話方塊架構應用程式類型。|  
  
 **子框架樣式**  
 指定應用程式中的外觀及子框架的初始狀態。 對於 MDI 應用程式只使用子框架樣式。  
  
|選項|說明|  
|------------|-----------------|  
|**子系最小化方塊**|指定的子視窗是否有最小化按鈕 （預設為啟用）。|  
|**子系最大化 方塊**|指定的子視窗是否有最大化按鈕 （預設為啟用）。|  
|**最大化的子系**|指定的子視窗一開始最大化藉由設定 cs.style 旗標**WS_MAXIMIZE**中[PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow)成員函式`CChildFrame`。|  
  
 **命令列 （功能表/工具列/功能區）**  
 指出您的應用程式包括功能表、 工具列和/或功能區。 不能用於對話方塊架構應用程式。  
  
|選項|說明|  
|------------|-----------------|  
|**使用傳統功能表**|指定您的應用程式包含傳統的不可拖曳式功能表。|  
|**使用傳統的停駐工具列**|將標準的 Windows 工具列加入至您的應用程式。 工具列包含按鈕建立新的文件。開啟及儲存文件檔案。剪下複製、 貼上或列印的文字;並輸入說明模式。 啟用此選項時，也會將功能表命令，以顯示或隱藏工具列。|  
|**使用瀏覽器樣式工具列**|將 Internet Explorer 樣式工具列加入至您的應用程式。|  
|**使用功能表列和工具列**|指出您的應用程式包含可拖曳的功能表列和工具列。|  
|**使用者定義的工具列和影像**|可讓使用者自訂的工具列和工具列影像，在執行階段。|  
|**個人化的功能表行為**|指定功能表是否包含項目開啟時，完整清單，或如果它包含使用者最常使用的命令。|  
|**使用功能區**|在您的應用程式，而不是功能表列或工具列中，會使用類似 Office 2007 的功能區。|  
  
 **對話方塊標題**  
 如[CDialog 類別](../../mfc/reference/cdialog-class.md)-架構應用程式，這個標題會出現在對話方塊中的標題列。 若要編輯此欄位，您必須先選取**對話方塊架構**底下**應用程式類型**。 如需詳細資訊，請參閱[MFC 應用程式精靈、 應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)


