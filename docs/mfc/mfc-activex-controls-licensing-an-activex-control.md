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
ms.openlocfilehash: aaab4ae3bb13790784a66d53b41dbc3a7cdaec89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364609"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>MFC ActiveX 控制項：授權 ActiveX 控制項

許可支援是 ActiveX 控制件的可選功能,允許您控制誰能夠使用或分發控制件。 (有關授權問題的其他討論,請參閱[升級現有 ActiveX 控制件時](../mfc/upgrading-an-existing-activex-control.md)的授權問題 。

> [!IMPORTANT]
> ActiveX 是一種不應用於新開發的傳統技術。 有關取代 ActiveX 的現代技術的詳細資訊,請參閱[ActiveX 控制件](activex-controls.md)。

本文章討論下列主題：

- [ActiveX 控制授權概述](#_core_overview_of_activex_control_licensing)

- [建立授權控制項](#_core_creating_a_licensed_control)

- [許可支援](#_core_licensing_support)

- [自訂 ActiveX 控制項的授權](#_core_customizing_the_licensing_of_an_activex_control)

實現許可的 ActiveX 控制件允許您作為控制式開發人員確定其他人如何使用 ActiveX 控制件。 向控制者提供控制項和 。LIC 檔,同意購買者可以分發控制項,但不能分發 。LIC 檔,具有使用控制項的應用程式。 這可以防止該應用程式的使用者編寫使用該控制件的新應用程式,而無需首先從您獲得控制項的許可。

## <a name="overview-of-activex-control-licensing"></a><a name="_core_overview_of_activex_control_licensing"></a>ActiveX 控制授權概述

為了向 ActiveX 控制項提供授權支援[,COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)類別`IClassFactory2`為介面中的多個函`IClassFactory2::RequestLicKey``IClassFactory2::GetLicInfo`數`IClassFactory2::CreateInstanceLic`提供: 與 。 當容器應用程式開發人員請求創建控制項的實例時,將調用`GetLicInfo`以驗證控制項是否。LIC 檔案存在。 如果控制項已獲得許可,則可以創建控制項的實例並將其放置在容器中。 開發人員完成容器應用程式的建構後,將發出另一個函數調用,此時將`RequestLicKey`呼叫 。。 此功能向容器應用程式返回許可證密鑰(簡單字串)。 然後,返回的密鑰嵌入到應用程式中。

下圖展示了將在開發容器應用程式期間使用的 ActiveX 控制件的許可證驗證。 如前所述,容器應用程式開發人員必須具有正確的 。安裝在開發電腦上的 LIC 檔案以建立控制項的實體。

![在開發階段驗證具有授權的 ActiveX 控制項](../mfc/media/vc374d1.gif "在開發階段驗證具有授權的 ActiveX 控制項") <br/>
在開發過程中驗證授權的 ActiveX 控制項

下圖中顯示了下一個過程,當最終使用者運行容器應用程式時。"

啟動應用程式時,通常需要創建控制項的實例。 容器通過呼叫`CreateInstanceLic`、傳遞嵌入的許可證金鑰作為參數來實現此目的。 然後,在嵌入式許可證密鑰和控制者使用的許可證金鑰副本之間進行字串比較。 如果匹配成功,將創建控制項的實例,並且應用程式繼續正常執行。 請注意, .LIC 檔不需要存在於控制項使用者的電腦上。

![在執行階段驗證具有授權的 ActiveX 控制項](../mfc/media/vc374d2.gif "在執行階段驗證具有授權的 ActiveX 控制項") <br/>
執行期間對授權的 ActiveX 控制件進行驗證

控制許可由兩個基本元件組成:控制實現 DLL 和許可證檔中的特定代碼。 該代碼由兩個(或可能三個)函數調用和一個字串組成,其後稱為"許可證字串",其中包含版權通知。 這些調用和許可證字串位於控制項實現 (中。CPP)檔。 由 ActiveX 控制精靈生成的許可證檔是帶有版權聲明的文本檔。 它使用 專案名稱與命名。LIC 擴展,例如 SAMPLE。LIC. 如果需要設計時使用,許可控件必須附帶許可證檔。

## <a name="creating-a-licensed-control"></a><a name="_core_creating_a_licensed_control"></a>建立授權控制項

當您使用 ActiveX 控制精靈建立控制框架時,可以輕鬆包括許可支援。 當您指定控制項應具有執行時許可證時,ActiveX 控制嚮導會將代碼添加到控制項類以支援許可。 該代碼由使用金鑰和許可證檔進行許可證驗證的功能組成。 還可以修改這些功能以自定義控制者許可。 有關許可證自定義的詳細資訊,請參閱本文後面的[「自訂 ActiveX 控件許可](#_core_customizing_the_licensing_of_an_activex_control)」。

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>在建立控制項目時使用 ActiveX 控制精靈加入對授權的支援

1. 在[創建 MFC ActiveX 控制件](../mfc/reference/creating-an-mfc-activex-control.md)中使用說明。 ActiveX 控制項精靈**的應用程式設定**頁包含使用運行時許可證創建控制項的選項。

ActiveX 控制精靈現在生成一個 ActiveX 控制框架,其中包含基本許可支援。 有關許可代碼的詳細說明,請參閱下一個主題。

## <a name="licensing-support"></a><a name="_core_licensing_support"></a>許可支援

當您使用 ActiveX 控制向導向 ActiveX 控制件添加許可支援時,ActiveX 控制件精靈會添加聲明和實現許可功能的代碼將添加到控制標頭和實現檔中。 此代碼由`VerifyUserLicense`成員函數和`GetLicenseKey`成員函數組成,該函數覆蓋[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)中的預設實現。 這些功能檢索和驗證控制許可證。

> [!NOTE]
> 第三個成員函數`VerifyLicenseKey`不是由 ActiveX 控制精靈生成的,但可以重寫以自訂許可證密鑰驗證行為。

這些成員函數是:

- [驗證使用者授權](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)

   通過檢查系統是否存在控制許可證文件,驗證控件是否允許設計時使用。 此函數由框架調用作為處理`IClassFactory2::GetLicInfo``IClassFactory::CreateInstanceLic`和的一部分。

- [取得授權金鑰](../mfc/reference/coleobjectfactory-class.md#getlicensekey)

   從控制項 DLL 請求唯一的金鑰。 此密鑰嵌入到容器應用程式中,並在以後與`VerifyLicenseKey`結合使用來創建控制項的實例。 此函數由框架調用作為處理`IClassFactory2::RequestLicKey`的一部分。

- [驗證授權金鑰](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)

   驗證嵌入金鑰和控制項的唯一鍵是否相同。 這允許容器創建控制項的實例供其使用。 此函數由框架調用作為處理`IClassFactory2::CreateInstanceLic`的一部分,可以重寫以提供許可證密鑰的自定義驗證。 預設實現執行字串比較。 有關詳細資訊,請參閱在本文後面的自訂[ActiveX 控制件的許可](#_core_customizing_the_licensing_of_an_activex_control)。

### <a name="header-file-modifications"></a><a name="_core_header_file_modifications"></a>標題檔案修改

ActiveX 控制精靈將以下代碼放在控制項檔中。 在此範例中,`CSampleCtrl``factory`將聲明物件的兩個成員函數,一個函數驗證控制項的存在。LIC 檔案和其他檢索要在包含控制的應用程式中使用的授權金鑰的檔案:

[!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

### <a name="implementation-file-modifications"></a><a name="_core_implementation_file_modifications"></a>實作檔案修改

ActiveX 控制精靈在控制項實現檔案中放置以下兩個語句,以宣告授權檔案名和授權字串:

[!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
> 如果以任何方式修改`szLicString`,還必須修改控件 中的第一行。LIC 檔案或許可將無法正常運行。

ActiveX 控制精靈在控制項實現檔案中放置以下代碼,以定義控制項類別和`VerifyUserLicense``GetLicenseKey`函數:

[!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

最後 **,ActiveX 控件嚮導**修改控件專案。IDL 檔。 **授權**關鍵字將加入控制檔的 coclass 宣告中, 例如以下範例的 :

[!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

## <a name="customizing-the-licensing-of-an-activex-control"></a><a name="_core_customizing_the_licensing_of_an_activex_control"></a>自訂 ActiveX 控制項的授權

由於`VerifyUserLicense``GetLicenseKey``VerifyLicenseKey`, 和聲明為控件工廠類的虛擬成員函數,因此可以自定義控制項的許可行為。

例如,您可以通過重`VerifyUserLicense`寫`VerifyLicenseKey`或成員函數為控件提供多個級別的許可。 在此函數中,您可以根據檢測到的許可證級別調整向使用者公開的屬性或方法。

還可以向`VerifyLicenseKey`函數添加代碼,該函數提供自定義方法,通知使用者控件創建失敗。 例如,在`VerifyLicenseKey`成員函數中,可以顯示一個消息框,指出控件未能初始化以及原因。

> [!NOTE]
> 自訂 ActiveX 控制授權驗證的另一種方法是檢查註冊資料庫中的特定註冊表項,而不是`AfxVerifyLicFile`呼叫 。 有關預設實現的範例,請參閱本文的[「實現檔修改」](#_core_implementation_file_modifications)部分。

有關許可問題的其他討論,請參閱[升級現有 ActiveX 控件時](../mfc/upgrading-an-existing-activex-control.md)的許可問題。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)
