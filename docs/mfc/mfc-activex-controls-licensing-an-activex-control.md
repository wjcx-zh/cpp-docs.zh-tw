---
title: MFC ActiveX 控制項：授權 ActiveX 控制項
ms.date: 11/19/2018
f1_keywords:
- COleObjectFactory
helpviewer_keywords:
- COleObjectFactory class [MFC], licensing controls
- MFC ActiveX controls [MFC], licensing
- VerifyLicenseKey method [MFC]
- VerifyUserLicense method [MFC]
- GetLicenseKey method [MFC]
- licensing ActiveX controls
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
ms.openlocfilehash: 35ca5d410f642f2557d9ee797eda2d9529f7f4d1
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176353"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>MFC ActiveX 控制項：授權 ActiveX 控制項

授權支援 ActiveX 控制項的選擇性功能可讓您控制能夠使用或散發控制項。 (如需額外的授權問題的詳細討論，請參閱中的授權問題[升級現有的 ActiveX 控制項](../mfc/upgrading-an-existing-activex-control.md)。)

> [!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

這篇文章討論下列主題：

- [授權的 ActiveX 控制項的概觀](#_core_overview_of_activex_control_licensing)

- [建立授權的控制](#_core_creating_a_licensed_control)

- [授權支援](#_core_licensing_support)

- [自訂授權的 ActiveX 控制項](#_core_customizing_the_licensing_of_an_activex_control)

實作授權的 ActiveX 控制項可讓您，為控制項開發人員，以判斷其他人如何使用 ActiveX 控制項。 您將控制購買提供控制項和。公用檔案，與採購者而非可能散發控制項，此協議。公用檔案，使用控制項的應用程式。 這可防止從撰寫新的應用程式，而不需要從您的控制項第一個授權使用控制項，該應用程式的使用者。

##  <a name="_core_overview_of_activex_control_licensing"></a> 授權的 ActiveX 控制項的概觀

為 ActiveX 控制項的授權可[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)類別會提供數個函式的實作`IClassFactory2`介面： `IClassFactory2::RequestLicKey`， `IClassFactory2::GetLicInfo`，和`IClassFactory2::CreateInstanceLic`。 當容器應用程式開發人員會要求建立的控制項，也就是呼叫執行個體`GetLicInfo`進行，以驗證的控制項。公用檔案會出現。 如果控制項已取得授權，就可以建立並放置在容器控制項的執行個體。 開發人員完成建構容器應用程式之後，另一個函式呼叫，這次`RequestLicKey`，進行。 此函式傳回的容器應用程式的授權金鑰 （簡單的字元字串）。 傳回的金鑰會內嵌在應用程式。

下圖示範如何將容器應用程式開發期間使用的 ActiveX 控制項的授權驗證。 如先前所述，容器應用程式開發人員必須正確。若要建立控制項的執行個體的開發電腦上安裝的授權檔案。

![授權 ActiveX 控制項，在開發階段驗證](../mfc/media/vc374d1.gif "在開發階段驗證的授權的 ActiveX 控制項") <br/>
授權的 ActiveX 控制項的開發期間進行驗證

當使用者執行的容器應用程式時，就會發生下一個程序下, 圖所示。

當應用程式啟動時，控制項的執行個體通常需要建立。 容器可完成此作業藉由呼叫`CreateInstanceLic`，傳遞做為參數的內嵌的授權金鑰。 內嵌的授權金鑰和控制自己的授權金鑰複本之間再進行字串比較。 如果比對成功，會建立控制項的執行個體和應用程式會繼續正常執行。 請注意，。公用檔案不需要存在於控制使用者的電腦上。

![授權 ActiveX 控制項在執行階段驗證](../mfc/media/vc374d2.gif "授權的 ActiveX 控制項在執行階段驗證") <br/>
授權的 ActiveX 控制項的執行期間進行驗證

控制項授權包含兩個基本元件： 在控制項實作 DLL 中的特定程式碼和授權檔案。 程式碼是由兩個 （或可能是三個） 的函式呼叫和字元字串，以下稱為 「 授權 」，包含字串的著作權注意事項所組成。 這些呼叫和授權字串位於控制項實作 (。CPP) 檔案。 ActiveX 控制項精靈，產生的授權檔案是含有文字檔案的著作權陳述式。 它會使用與專案名稱來命名。公用擴充功能，例如範例。授權。 授權的控制項必須伴隨授權檔案，視設計階段使用。

##  <a name="_core_creating_a_licensed_control"></a> 建立授權的控制

當您使用 「 ActiveX 控制項精靈 」 來建立控制架構時，很容易包含授權支援。 當您指定的控制項應該有執行階段授權時，ActiveX 控制項精靈會加入至控制項類別，以支援授權的程式碼。 程式碼是由用於授權驗證的金鑰和授權檔案的函式所組成。 這些函式也可以修改以自訂控制項的授權。 如需有關授權的自訂的詳細資訊，請參閱[自訂的 ActiveX 控制項授權](#_core_customizing_the_licensing_of_an_activex_control)本文稍後。

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>若要加入授權使用 「 ActiveX 控制項精靈 」，當您建立您的控制項專案的支援

1. 使用中的指示[建立 MFC ActiveX 控制項](../mfc/reference/creating-an-mfc-activex-control.md)。 **應用程式設定**ActiveX 控制項精靈的頁面包含建立控制項的執行階段授權的選項。

ActiveX 控制項精靈現在會產生一個 ActiveX 控制項架構，可包含基本授權的支援。 如需授權的程式碼的詳細說明，請參閱下一步。

##  <a name="_core_licensing_support"></a> 授權支援

當您使用授權的支援新增至 ActiveX 控制項的 ActiveX 控制項精靈時，[ActiveX 控制項精靈] 會將檔案加入程式碼會宣告並實作授權的功能來控制標頭和實作。 此程式碼組成`VerifyUserLicense`成員函式和`GetLicenseKey`成員函式，會覆寫預設的實作中找到[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) 。 這些函式擷取，並確認控制授權。

> [!NOTE]
>  第三個成員函式，`VerifyLicenseKey`不會產生 ActiveX 控制項精靈 」，但您可以自訂的授權金鑰的驗證行為覆寫。

這些成員函式如下：

- [VerifyUserLicense](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)

   驗證的控制項可讓設計階段使用，藉由檢查控制項授權檔案存在的系統。 由架構呼叫此函式處理過程`IClassFactory2::GetLicInfo`和`IClassFactory::CreateInstanceLic`。

- [GetLicenseKey](../mfc/reference/coleobjectfactory-class.md#getlicensekey)

   會控制 DLL 從要求的唯一索引鍵。 此金鑰會內嵌於容器應用程式和更新版本中，用於搭配`VerifyLicenseKey`，以建立控制項的執行個體。 由架構呼叫此函式處理過程`IClassFactory2::RequestLicKey`。

- [VerifyLicenseKey](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)

   確認內嵌索引鍵和控制項的唯一索引鍵都相同。 這可讓要建立使用控制項的執行個體的容器。 由架構呼叫此函式處理過程`IClassFactory2::CreateInstanceLic`可覆寫，以提供自訂的驗證的授權金鑰。 預設實作會執行字串比較。 如需詳細資訊，請參閱 <<c0> [ 自訂的 ActiveX 控制項授權](#_core_customizing_the_licensing_of_an_activex_control)稍後在本文中。

###  <a name="_core_header_file_modifications"></a> 標頭檔案修改

ActiveX 控制項精靈會將下列程式碼置於控制項標頭檔。 在此範例中的兩個成員函式`CSampleCtrl`的物件`factory`宣告，一個是驗證控制項的目前狀態。公用檔案，另一個則會擷取要用於包含控制項的應用程式的授權金鑰：

[!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

###  <a name="_core_implementation_file_modifications"></a> 實作檔案修改

ActiveX 控制項精靈會將下列兩個陳述式放在控制項實作檔，來宣告的授權檔名和授權字串：

[!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
>  如果您修改`szLicString`以任何方式，您也必須修改控制項中的第一行。公用檔案，或授權將無法正確運作。

ActiveX 控制項精靈會將下列程式碼置於控制項實作檔來定義控制項類別`VerifyUserLicense`和`GetLicenseKey`函式：

[!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

最後， **ActiveX 控制項精靈**修改控制項專案。IDL 檔案。 **授權**關鍵字加入至 coclass 控制項的宣告，如下列範例所示：

[!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a> 自訂授權的 ActiveX 控制項

因為`VerifyUserLicense`， `GetLicenseKey`，和`VerifyLicenseKey`會宣告為虛擬成員函式控制項 factory 類別中，您可以自訂控制項的授權行為。

例如，您可以在其中提供數個層級的授權控制項，藉由覆寫`VerifyUserLicense`或`VerifyLicenseKey`成員函式。 在此函式中，您無法調整哪一個屬性或方法會公開給使用者，根據您偵測到的授權層級。

您也可以加入程式碼`VerifyLicenseKey`函式，提供自訂的方法，以通知使用者控制建立失敗。 例如，在您`VerifyLicenseKey`成員函式，您可以顯示訊息方塊，指出控制項無法初始化和原因。

> [!NOTE]
>  若要自訂 ActiveX 控制項授權驗證的另一個方法是檢查登錄資料庫有無特定的登錄機碼，而不是呼叫`AfxVerifyLicFile`。 如需預設實作的範例，請參閱[實作的檔案修改](#_core_implementation_file_modifications)一節。

如需額外的授權問題的詳細討論，請參閱中的授權問題[升級現有的 ActiveX 控制項](../mfc/upgrading-an-existing-activex-control.md)。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)

