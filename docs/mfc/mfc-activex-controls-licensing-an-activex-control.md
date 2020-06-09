---
title: MFC ActiveX 控制項：授權 ActiveX 控制項
ms.date: 11/19/2018
helpviewer_keywords:
- COleObjectFactory class [MFC], licensing controls
- MFC ActiveX controls [MFC], licensing
- VerifyLicenseKey method [MFC]
- VerifyUserLicense method [MFC]
- GetLicenseKey method [MFC]
- licensing ActiveX controls
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
ms.openlocfilehash: 4fe2fcf63cce02ed6c1c9943e6d0fe6ffab00a92
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622361"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>MFC ActiveX 控制項：授權 ActiveX 控制項

授權支援是 ActiveX 控制項的選用功能，可讓您控制誰能夠使用或散發控制項。 （如需授權問題的其他討論，請參閱[升級現有的 ActiveX 控制項](upgrading-an-existing-activex-control.md)中的授權問題）。

> [!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需取代 ActiveX 之新式技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

本文章討論下列主題：

- [ActiveX 控制項授權總覽](#_core_overview_of_activex_control_licensing)

- [建立授權的控制項](#_core_creating_a_licensed_control)

- [授權支援](#_core_licensing_support)

- [自訂 ActiveX 控制項的授權](#_core_customizing_the_licensing_of_an_activex_control)

執行授權的 ActiveX 控制項可讓您（控制項開發人員）決定其他人如何使用 ActiveX 控制項。 您可以使用控制項和來提供控制項購買者。授權檔案，具有購買者可能散發控制項的合約，而不是。授權檔案，包含使用此控制項的應用程式。 這可防止該應用程式的使用者撰寫使用此控制項的新應用程式，而不需要先向您授權控制項。

## <a name="overview-of-activex-control-licensing"></a><a name="_core_overview_of_activex_control_licensing"></a>ActiveX 控制項授權總覽

為了提供 ActiveX 控制項的授權支援， [COleObjectFactory](reference/coleobjectfactory-class.md)類別會針對介面中的數個函式提供實作用 `IClassFactory2` ： `IClassFactory2::RequestLicKey` 、 `IClassFactory2::GetLicInfo` 和 `IClassFactory2::CreateInstanceLic` 。 當容器應用程式開發人員提出要求來建立控制項的實例時，就會呼叫來 `GetLicInfo` 驗證控制項。已有授權檔案案。 如果控制項已獲得授權，則可以建立控制項的實例並將其放置在容器中。 在開發人員完成容器應用程式的建立作業之後，會進行另一個函式呼叫，這次 `RequestLicKey` 是。 此函式會將授權金鑰（簡單的字元字串）傳回至容器應用程式。 傳回的索引鍵接著會內嵌在應用程式中。

下圖顯示在開發容器應用程式期間將使用的 ActiveX 控制項授權驗證。 如先前所述，容器應用程式開發人員必須具備適當的。在開發電腦上安裝的 .LIC 檔案，用以建立控制項的實例。

![在開發階段驗證具有授權的 ActiveX 控制項](../mfc/media/vc374d1.gif "在開發階段驗證具有授權的 ActiveX 控制項") <br/>
在開發期間驗證已授權的 ActiveX 控制項

下圖顯示的下一個程式會在終端使用者執行容器應用程式時發生。

當應用程式啟動時，通常需要建立控制項的實例。 容器會呼叫來完成這 `CreateInstanceLic` 項工作，傳遞內嵌授權金鑰做為參數。 然後，在內嵌授權金鑰與控制項自己的授權金鑰複本之間進行字串比較。 如果比對成功，就會建立控制項的實例，並繼續正常執行應用程式。 請注意，。授權檔案不需要存在於控制使用者的電腦上。

![在執行階段驗證具有授權的 ActiveX 控制項](../mfc/media/vc374d2.gif "在執行階段驗證具有授權的 ActiveX 控制項") <br/>
在執行期間驗證授權的 ActiveX 控制項

控制授權包含兩個基本元件：控制項執行 DLL 中的特定程式碼和授權檔案。 這段程式碼是由兩個（或可能有三個）函式呼叫和字元字串所組成，這些都是指「授權字串」，其中包含著作權注意事項。 這些呼叫和授權字串可在控制項執行（中找到。CPP）檔案。 由 ActiveX 控制項 Wizard 產生的授權檔案是具有著作權語句的文字檔。 其命名方式是搭配使用專案名稱和。.LIC 延伸模組，例如 SAMPLE。.LIC. 如果需要設計階段使用，授權的控制項必須附有授權檔案。

## <a name="creating-a-licensed-control"></a><a name="_core_creating_a_licensed_control"></a>建立授權的控制項

當您使用 ActiveX Control Wizard 建立控制架構時，很容易就能包含授權支援。 當您指定控制項應具有執行時間授權時，ActiveX 控制項 Wizard 會將程式碼加入至控制項類別，以支援授權。 程式碼是由使用金鑰和授權檔案進行授權驗證的函式所組成。 這些函式也可以修改以自訂控制項授權。 如需有關授權自訂的詳細資訊，請參閱本文稍後的[自訂 ActiveX 控制項的授權](#_core_customizing_the_licensing_of_an_activex_control)。

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>當您建立控制項專案時，使用 ActiveX 控制項嚮導新增授權的支援

1. 使用[建立 MFC ActiveX 控制項](reference/creating-an-mfc-activex-control.md)中的指示。 [ActiveX 控制項嚮導] 的 [**應用程式設定**] 頁面包含使用執行時間授權建立控制項的選項。

ActiveX Control Wizard 現在會產生 ActiveX 控制項架構，其中包含基本的授權支援。 如需授權碼的詳細說明，請參閱下一個主題。

## <a name="licensing-support"></a><a name="_core_licensing_support"></a>授權支援

當您使用 ActiveX Control Wizard 將授權支援新增至 ActiveX 控制項時，ActiveX Control Wizard 會加入宣告和執行授權功能的程式碼，並新增至控制項標頭和實作為檔案。 此程式碼是由成員函式和成員函式所組成 `VerifyUserLicense` `GetLicenseKey` ，其會覆寫在[COleObjectFactory](reference/coleobjectfactory-class.md)中找到的預設值。 這些函式會取得並驗證控制授權。

> [!NOTE]
> 第三個成員函式 `VerifyLicenseKey` 不是由 ActiveX Control Wizard 所產生，但是可以覆寫以自訂授權金鑰驗證行為。

這些成員函式包括：

- [VerifyUserLicense](reference/coleobjectfactory-class.md#verifyuserlicense)

   藉由檢查系統是否有控制授權檔案，確認控制項允許設計階段的使用方式。 此函式是由架構在處理和中呼叫 `IClassFactory2::GetLicInfo` `IClassFactory::CreateInstanceLic` 。

- [GetLicenseKey](reference/coleobjectfactory-class.md#getlicensekey)

   向控制 DLL 要求唯一索引鍵。 此金鑰會內嵌在容器應用程式中，並在稍後搭配使用 `VerifyLicenseKey` 以建立控制項的實例。 在處理過程中，架構會呼叫這個函式 `IClassFactory2::RequestLicKey` 。

- [VerifyLicenseKey](reference/coleobjectfactory-class.md#verifylicensekey)

   確認內嵌索引鍵和控制項的唯一索引鍵相同。 這可讓容器建立控制項的實例以供其使用。 此函式是由架構在處理過程中呼叫 `IClassFactory2::CreateInstanceLic` ，可以覆寫以提供授權金鑰的自訂驗證。 預設的實作為執行字串比較。 如需詳細資訊，請參閱本文稍後的[自訂 ActiveX 控制項的授權](#_core_customizing_the_licensing_of_an_activex_control)。

### <a name="header-file-modifications"></a><a name="_core_header_file_modifications"></a>標頭檔修改

ActiveX 控制項 Wizard 會將下列程式碼放在控制項標頭檔中。 在此範例中，會宣告物件的兩個成員函式 `CSampleCtrl` `factory` ，其中一個會驗證控制項是否存在。授權檔案，另一個則會抓取要在包含控制項的應用程式中使用的授權金鑰：

[!code-cpp[NVC_MFC_AxUI#39](codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

### <a name="implementation-file-modifications"></a><a name="_core_implementation_file_modifications"></a>執行檔案修改

ActiveX 控制項 Wizard 會將下列兩個語句放在控制項執行檔中，以宣告授權檔案名和授權字串：

[!code-cpp[NVC_MFC_AxUI#40](codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
> 如果您 `szLicString` 以任何方式修改，也必須修改控制項中的第一行。授權檔案或授權將無法正常運作。

ActiveX 控制項 Wizard 會將下列程式碼放在控制項執行檔中，以定義控制項類別的和函式 `VerifyUserLicense` `GetLicenseKey` ：

[!code-cpp[NVC_MFC_AxUI#41](codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

最後， **ActiveX 控制項 Wizard**會修改控制項專案。IDL 檔案。 已**授權**的關鍵字會加入至控制項的 coclass 宣告，如下列範例所示：

[!code-cpp[NVC_MFC_AxUI#42](codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

## <a name="customizing-the-licensing-of-an-activex-control"></a><a name="_core_customizing_the_licensing_of_an_activex_control"></a>自訂 ActiveX 控制項的授權

因為 `VerifyUserLicense` 、 `GetLicenseKey` 和 `VerifyLicenseKey` 會宣告為控制 factory 類別的虛擬成員函式，所以您可以自訂控制項的授權行為。

例如，您可以藉由覆寫或成員函式，為控制項提供數個層級的授權 `VerifyUserLicense` `VerifyLicenseKey` 。 在此函式內，您可以根據偵測到的授權等級，調整要對使用者公開的屬性或方法。

您也可以將程式碼新增至函式，該函式會 `VerifyLicenseKey` 提供自訂的方法，以通知使用者控制項建立已失敗。 例如，在您的成員函式中， `VerifyLicenseKey` 您可以顯示訊息方塊，指出控制項無法初始化和原因。

> [!NOTE]
> 自訂 ActiveX 控制項授權驗證的另一種方法是，檢查註冊資料庫是否有特定登錄機碼，而不是呼叫 `AfxVerifyLicFile` 。 如需預設執行的範例，請參閱本文的「[執行檔案修改](#_core_implementation_file_modifications)」一節。

如需授權問題的其他討論，請參閱[升級現有的 ActiveX 控制項](upgrading-an-existing-activex-control.md)中的授權問題。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項精靈](reference/mfc-activex-control-wizard.md)
