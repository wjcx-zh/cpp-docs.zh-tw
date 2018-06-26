---
title: MFC ActiveX 控制項： 授權 ActiveX 控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- COleObjectFactory
dev_langs:
- C++
helpviewer_keywords:
- COleObjectFactory class [MFC], licensing controls
- MFC ActiveX controls [MFC], licensing
- VerifyLicenseKey method [MFC]
- VerifyUserLicense method [MFC]
- GetLicenseKey method [MFC]
- licensing ActiveX controls
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0b1e8f0c54cf4d409aedb99fc3195b927d5f127
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929740"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>MFC ActiveX 控制項：授權 ActiveX 控制項
授權支援 ActiveX 控制項的選用功能可讓您控制哪些使用者能夠使用或散發控制項。 (如需額外的授權問題的詳細討論，請參閱中的授權問題[升級現有的 ActiveX 控制項](../mfc/upgrading-an-existing-activex-control.md)。)  
  
 本文將討論下列主題：  
  
-   [授權 ActiveX 控制項的概觀](#_core_overview_of_activex_control_licensing)  
  
-   [建立授權的控制項](#_core_creating_a_licensed_control)  
  
-   [授權支援](#_core_licensing_support)  
  
-   [自訂授權的 ActiveX 控制項](#_core_customizing_the_licensing_of_an_activex_control)  
  
 實作授權的 ActiveX 控制項可讓您，做為控制項開發人員，以判斷其他人使用 ActiveX 控制項的方式。 您將控制購買提供控制項和。與採購者可能但未散發控制項，此協議的授權檔案。授權檔案，請使用控制項的應用程式。 這可防止撰寫新的應用程式，不需從您的控制項第一次授權使用控制項，該應用程式的使用者。  
  
##  <a name="_core_overview_of_activex_control_licensing"></a> 授權 ActiveX 控制項的概觀  
 若要提供 ActiveX 控制項授權支援[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)類別提供幾個函式中的實作`IClassFactory2`介面： `IClassFactory2::RequestLicKey`， `IClassFactory2::GetLicInfo`，和`IClassFactory2::CreateInstanceLic`。 當容器應用程式開發人員提出的要求建立控制項，呼叫的執行個體`GetLicInfo`進行驗證的控制項。授權的檔案存在。 如果控制項係授權使用，可建立及放置在容器中控制項的執行個體。 開發人員建構容器應用程式完成後，另一個函式呼叫，這次`RequestLicKey`，進行。 此函數會傳回該容器應用程式的授權金鑰 （簡單的字元字串）。 傳回的索引鍵則會內嵌在應用程式中。  
  
 下圖示範授權的 ActiveX 控制項容器應用程式開發期間將會使用驗證。 如先前所述，容器應用程式開發人員必須正確。若要建立控制項的執行個體的開發電腦上安裝的授權檔案。  
  
 ![授權 ActiveX 控制項在開發階段驗證](../mfc/media/vc374d1.gif "vc374d1")  
在開發期間的驗證的授權的 ActiveX 控制項  
  
 當使用者執行的容器應用程式時，就會發生下一個程序中下, 圖所示。  
  
 應用程式啟動時，控制項的執行個體通常需要建立。 容器可完成此作業藉由呼叫`CreateInstanceLic`，做為參數傳遞的內嵌的授權金鑰。 字串比較然後對內嵌的授權金鑰，並控制自己的授權金鑰。 如果比對成功，會建立控制項的執行個體和應用程式會繼續正常執行。 請注意，。授權檔不需要存在於控制使用者的電腦上。  
  
 ![授權 ActiveX 控制項在執行階段驗證](../mfc/media/vc374d2.gif "vc374d2")  
在執行期間的驗證的授權的 ActiveX 控制項  
  
 控制項授權包含兩個基本元件： 在控制項 DLL 實作特定程式碼和授權檔案。 程式碼是由兩個 （或可能是三個） 的函式呼叫和字元字串，以下稱為 「 授權字串 」，其中包含的著作權注意事項所組成。 這些呼叫及授權字串位於控制項實作 (。CPP) 檔案。 ActiveX 控制項精靈所產生的授權檔案是著作權陳述式的文字檔案。 它會命名為使用與專案名稱。授權延伸模組，例如範例。授權。 授權的控制項需要設計階段使用時必須附帶授權檔案。  
  
##  <a name="_core_creating_a_licensed_control"></a> 建立授權的控制項  
 當您使用 ActiveX 控制項精靈來建立控制架構時，很容易包含授權支援。 當您指定的控制項應該有執行階段授權時，ActiveX 控制項精靈會將程式碼加入至控制項類別，以支援授權。 程式碼使用的授權驗證的金鑰和授權檔案的函式所組成。 這些函式也可以修改以自訂控制項的授權。 如需有關自訂授權的詳細資訊，請參閱[自訂授權的 ActiveX 控制項](#_core_customizing_the_licensing_of_an_activex_control)本文稍後。  
  
#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>若要新增授權使用 ActiveX 控制項精靈，當您建立您的控制項專案的支援  
  
1.  使用中的指示[建立 MFC ActiveX 控制項](../mfc/reference/creating-an-mfc-activex-control.md)。 **應用程式設定**ActiveX 控制項精靈的頁面包含建立控制項的執行階段授權的選項。  
  
 ActiveX 控制項精靈現在會產生 ActiveX 控制項架構，其中包含基本授權的支援。 如需授權的程式碼的詳細說明，請參閱下一個主題。  
  
##  <a name="_core_licensing_support"></a> 授權支援  
 當您加入至 ActiveX 控制項的授權支援使用 ActiveX 控制項精靈時，ActiveX 控制項精靈會新增宣告並實作授權的功能會加入程式碼控制標頭與實作檔。 此程式碼組成`VerifyUserLicense`成員函式和`GetLicenseKey`成員函式，以覆寫預設的實作中找到[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) 。 這些函式會擷取，並確認控制授權。  
  
> [!NOTE]
>  第三個成員函式，`VerifyLicenseKey`不會產生 ActiveX 控制項精靈 」，但您可以覆寫自訂授權金鑰驗證行為。  
  
 這些成員函式會：  
  
-   [VerifyUserLicense](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)  
  
     確認控制項可讓設計階段使用狀況，檢查有系統控制授權檔案。 由架構呼叫此函式處理期間`IClassFactory2::GetLicInfo`和`IClassFactory::CreateInstanceLic`。  
  
-   [GetLicenseKey](../mfc/reference/coleobjectfactory-class.md#getlicensekey)  
  
     控制 DLL 從要求的唯一索引鍵。 此索引鍵是內嵌在容器應用程式和更新版本中，用於搭配`VerifyLicenseKey`，以建立控制項的執行個體。 由架構呼叫此函式處理期間`IClassFactory2::RequestLicKey`。  
  
-   [VerifyLicenseKey](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)  
  
     確認內嵌的金鑰和控制項的唯一索引鍵都相同。 這可讓容器建立其使用的控制項的執行個體。 由架構呼叫此函式處理期間`IClassFactory2::CreateInstanceLic`，且可以提供自訂的驗證的授權金鑰。 預設實作會執行字串比較。 如需詳細資訊，請參閱[自訂授權的 ActiveX 控制項](#_core_customizing_the_licensing_of_an_activex_control)在本文稍後。  
  
###  <a name="_core_header_file_modifications"></a> 標頭檔案修改  
 ActiveX 控制項精靈會將下列程式碼置於控制項標頭檔。 在此範例中，兩個成員函式的`CSampleCtrl`的物件`factory`宣告，一個是驗證控制項的目前狀態。授權檔以及另一個擷取的授權金鑰，以用於包含控制項的應用程式：  
  
 [!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]  
  
###  <a name="_core_implementation_file_modifications"></a> 實作檔案修改  
 ActiveX 控制項精靈會將下列兩個陳述式放在控制項實作檔，來宣告授權檔名和授權字串：  
  
 [!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]  
  
> [!NOTE]
>  如果您修改`szLicString`以任何方式，您也必須修改控制項中的第一行。授權檔案，或授權無法正常運作。  
  
 ActiveX 控制項精靈會將下列程式碼置於控制項實作檔定義的控制項類別`VerifyUserLicense`和`GetLicenseKey`函式：  
  
 [!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]  
  
 最後， **ActiveX 控制項精靈**修改控制項專案。IDL 檔案。 **授權**關鍵字加入至 coclass 控制項的宣告，如下列範例所示：  
  
 [!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]  
  
##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a> 自訂授權的 ActiveX 控制項  
 因為`VerifyUserLicense`， `GetLicenseKey`，和`VerifyLicenseKey`會宣告為虛擬成員函式的控制項 factory 類別中，您可以自訂控制項的授權行為。  
  
 例如，您可以提供數個層級授權控制項，藉由覆寫`VerifyUserLicense`或`VerifyLicenseKey`成員函式。 此函式內，您無法調整哪個屬性或方法會公開給使用者，根據您偵測到的授權層級。  
  
 您也可以將程式碼加入`VerifyLicenseKey`函式會提供自訂的方法，通知使用者，以控制建立失敗。 例如，在您`VerifyLicenseKey`成員函式，您無法顯示訊息方塊，指出控制項無法初始化和原因。  
  
> [!NOTE]
>  若要自訂 ActiveX 控制項授權驗證另一個方法是檢查登錄資料庫有特定的登錄機碼，而不是呼叫`AfxVerifyLicFile`。 如需預設實作的範例，請參閱[實作檔的修改](#_core_implementation_file_modifications)本文一節。  
  
 如需額外的授權問題的詳細討論，請參閱中的授權問題[升級現有的 ActiveX 控制項](../mfc/upgrading-an-existing-activex-control.md)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)

