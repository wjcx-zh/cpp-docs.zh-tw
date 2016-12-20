---
title: "MFC ActiveX 控制項：授權 ActiveX 控制項 | Microsoft Docs"
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
  - "COleObjectFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleObjectFactory 類別, 授權控制項"
  - "GetLicenseKey 方法"
  - "授權 ActiveX 控制項"
  - "MFC ActiveX 控制項, 授權"
  - "VerifyLicenseKey 方法"
  - "VerifyUserLicense 方法"
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：授權 ActiveX 控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

允許支援， ActiveX 控制項一個選擇性的功能，可讓您控制誰可以使用或散發控制項時。\(如需允許發出額外的討論，請參閱 [升級現有的 ActiveX 控制項](../mfc/upgrading-an-existing-activex-control.md)中的授權發行\)。  
  
 本文將討論下列主題:  
  
-   [ActiveX 控制項允許概觀](#_core_overview_of_activex_control_licensing)  
  
-   [建立授權控制項。](#_core_creating_a_licensed_control)  
  
-   [允許支援](#_core_licensing_support)  
  
-   [自訂允許 ActiveX 控制項](#_core_customizing_the_licensing_of_an_activex_control)  
  
 實作允許的 ActiveX 控制項，可讓您為控制項開發人員，判斷其他人將如何使用 ActiveX 控制項。  您提供控制購買者以控制和 .LIC 檔案，以這個通訊協定購買者而言可能散發控制項時，，但不是 .LIC 檔案，會使用控制項的應用程式。  這會讓該應用程式的使用者將使用控制項的新應用程式，而不需先，允許從您的控制項。  
  
##  <a name="_core_overview_of_activex_control_licensing"></a> ActiveX 控制項允許概觀  
 為 ActiveX 控制項提供允許支援， [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) 類別在 **IClassFactory2** 介面的數個函式提供的實作: **IClassFactory2::RequestLicKey**和 **IClassFactory2::GetLicInfo**和 **IClassFactory2::CreateInstanceLic**。  當容器應用程式開發人員提出要求建立控制項的執行個體時，對 `GetLicInfo` 的呼叫驗證控制項 .LIC 檔案存在。  如果控制項已授權，控制項的執行個體在容器可以建立並放置。  在開發人員完成建構容器應用程式之後，另一個函式，呼叫 `RequestLicKey`的動作，進行。  這個函式會傳回授權識別碼 \(簡單字串\) 對容器應用程式。  傳回的索引鍵在應用程式接著會內嵌。  
  
 下圖顯示在容器應用程式開發期間，將使用 ActiveX 控制項的授權驗證。  如前所述，容器應用程式開發人員必須在開發電腦上安裝適當的 .LIC 檔案建立控制項的執行個體。  
  
 ![在開發階段驗證具有授權的 ActiveX 控制項](../mfc/media/vc374d1.png "vc374D1")  
授權的 ActiveX 控制項的驗證在開發期間  
  
 當使用者在容器應用程式，下流程，下圖中所示，發生。  
  
 當應用程式啟動時，通常需要控制項的建立執行個體。  容器藉由呼叫來完成對 `CreateInstanceLic`，透過內嵌授權識別碼做為參數。  字串比較然後在內嵌授權授權金鑰的金鑰和控制項本身的複本之間。  如果比對失敗，控制項的建立執行個體，且應用程式會繼續正常執行。  請注意 .LIC 檔案不需要有控制項使用者的電腦。  
  
 ![在執行階段驗證具有授權的 ActiveX 控制項](../mfc/media/vc374d2.png "vc374D2")  
授權的 ActiveX 控制項的驗證執行期間  
  
 控制項允許包含兩個基本元件:在控制項實作 DLL 和授權檔案的程式碼。  程式碼是由兩個或三個 \(可能\) 函式呼叫和字串組成，以下稱為「授權字串」，包含著作權注意事項。  這些呼叫和授權資料控制項中實作 \(.CPP\) 檔案中。  授權檔，由產生 ActiveX 控制項精靈，是有著作權陳述式的文字檔。  使用與 .LIC 副檔名，重新命名，例如 SAMPLE.LIC 的專案名稱。  如果設計階段用途是必要的，必須由授權檔隨附授權控制項。  
  
##  <a name="_core_creating_a_licensed_control"></a> 建立授權控制項。  
 當您使用 ActiveX 控制項精靈建立控制項架構，包括可支援相當容易。  當您指定時控制項應該有一個執行階段授權， ActiveX 控制項精靈會將程式碼加入至控制項類別支援授權。  程式碼包含為授權驗證使用索引鍵和授權檔案的函式。  也可以修改這些函式自訂控制項以允許。  如需授權自訂的詳細資訊，請參閱本主題稍後的 [自訂允許 ActiveX 控制項](#_core_customizing_the_licensing_of_an_activex_control) 文章。  
  
#### 加入支援允許與 ActiveX 控制項精靈，當您建置控制項專案  
  
1.  使用指示在 [建立 MFC ActiveX 控制項](../mfc/reference/creating-an-mfc-activex-control.md)。  ActiveX 控制項精靈之 \[**應用程式設定**\] 頁包含選項建立與這個執行階段授權的控制項。  
  
 ActiveX 控制項精靈現在會產生包含基本的授權支援之 ActiveX 控制項框架。  如需授權程式碼的詳細說明，請參閱下一個主題。  
  
##  <a name="_core_licensing_support"></a> 允許支援  
 當您使用 ActiveX 控制項精靈將允許支援加入至 ActiveX 控制項時， ActiveX 控制項精靈加入宣告的程式碼，並實作允許功能加入至控制項的標題和實作檔。  這個程式碼是由 `VerifyUserLicense` 成員函式和 `GetLicenseKey` 成員函式所組成，覆寫 [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) 中的預設實作。  這些函式擷取並確認控制項授權。  
  
> [!NOTE]
>  第三 \+ 成成員函式， `VerifyLicenseKey` 未產生的 \(ActiveX 控制項精靈，，但是可以覆寫自訂授權金鑰驗證行為。  
  
 這些成員函式是:  
  
-   [VerifyUserLicense](../Topic/COleObjectFactory::VerifyUserLicense.md)  
  
     驗證控制項會檢查系統允許設計階段使用控制項授權檔是否存在。  為處理 **IClassFactory2::GetLicInfo** 和 **IClassFactory::CreateInstanceLic**的一部分，這個函式時由架構呼叫。  
  
-   [GetLicenseKey](../Topic/COleObjectFactory::GetLicenseKey.md)  
  
     要求控制項 DLL 的唯一索引鍵。  這個機碼在容器應用程式內嵌且與 `VerifyLicenseKey`搭配使用，之後，建立控制項的執行個體。  為處理 **IClassFactory2::RequestLicKey**的一部分，這個函式時由架構呼叫。  
  
-   [VerifyLicenseKey](../Topic/COleObjectFactory::VerifyLicenseKey.md)  
  
     驗證內嵌的金鑰和控制項的唯一索引鍵相同。  這可讓容器建立控制項的執行個體為其使用。  這個函式時由架構呼叫以處理 **IClassFactory2::CreateInstanceLic** 的一部分，而且可以覆寫提供授權識別碼的自訂的驗證。  預設實作執行字串比較。  如需詳細資訊，請參閱 [自訂允許 ActiveX 控制項](#_core_customizing_the_licensing_of_an_activex_control)，稍後在這篇文章。  
  
###  <a name="_core_header_file_modifications"></a> 標頭檔修改  
 ActiveX 控制項精靈在控制標頭檔將下列程式碼。  在此範例中， `CSampleCtrl` 物件 `factory` 的兩個成員函式宣告，驗證控制項 .LIC 檔案會擷取應用程式的授權識別碼包含控制項的一個與另一個:  
  
 [!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/CPP/mfc-activex-controls-licensing-an-activex-control_1.h)]  
  
###  <a name="_core_implementation_file_modifications"></a> 實作檔案修改  
 ActiveX 控制項精靈在控制項實作檔將下列兩個陳述式中宣告授權檔名和授權資料:  
  
 [!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/CPP/mfc-activex-controls-licensing-an-activex-control_2.cpp)]  
  
> [!NOTE]
>  如果您以任何方式修改 **szLicString** ，您也必須修改控制項 .LIC 檔案的第一行或允許將無法正常運作。  
  
 ActiveX 控制項精靈在控制項實作檔 \(Implementation File\) 將下列程式碼定義控制項類別的 `VerifyUserLicense` 和 `GetLicenseKey` 函式:  
  
 [!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/CPP/mfc-activex-controls-licensing-an-activex-control_3.cpp)]  
  
 最後， **ActiveX Control Wizard** 修改控制項目 .IDL 檔案。  **licensed** 關鍵字加入至控制項的 coclass 宣告，如下列範例所示:  
  
 [!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/CPP/mfc-activex-controls-licensing-an-activex-control_4.idl)]  
  
##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a> 自訂允許 ActiveX 控制項  
 由於 `VerifyUserLicense`、 `GetLicenseKey`和 `VerifyLicenseKey` 宣告時，虛擬控制站函式分類的成員，您可以自訂控制項的授權行為。  
  
 例如，您可以為控制項提供數個可以藉由覆寫 `VerifyUserLicense` 或 `VerifyLicenseKey` 成員函式。  在這個函式中您可調整的屬性或方法公開給使用者會根據您偵測的授權層級。  
  
 您也可以將程式碼加入至以通知使用者提供自訂的方法的 `VerifyLicenseKey` 函式控制建立失敗。  例如，在您的 `VerifyLicenseKey` 成員函式可以顯示訊息方塊，指出控制項無法初始化，以及。  
  
> [!NOTE]
>  另一種自訂 ActiveX 控制項授權驗證會檢查系統註冊資料庫特定的登錄機碼，而不是呼叫 `AfxVerifyLicFile`。  如需預設實作的範例，請參閱本文件的 [實作檔案修改](#_core_implementation_file_modifications) 一節。  
  
 如需授權發行的額外的討論，請參閱 [升級現有的 ActiveX 控制項](../mfc/upgrading-an-existing-activex-control.md)中的授權散發。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)