---
title: MFC ActiveX 控制項：當地語系化 ActiveX 控制項
ms.date: 09/12/2018
f1_keywords:
- LocaleID
- AfxOleRegisterTypeLib
helpviewer_keywords:
- localization, ActiveX controls
- MFC ActiveX controls [MFC], localizing
- LocaleID ambient property [MFC]
- LOCALIZE sample [MFC]
ms.assetid: a44b839a-c652-4ec5-b824-04392708a5f9
ms.openlocfilehash: 13c8ff545763017b01685e012ab2d497eaf7084a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767544"
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>MFC ActiveX 控制項：當地語系化 ActiveX 控制項

本文將討論當地語系化 ActiveX 控制項介面的程序。

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

如果您要改寫 ActiveX 控制項使其符合國際化市場，您可能會想要當地語系化控制項。 Windows 支援許多語言，除了預設的英文以外，還支援包括德文、法文和瑞典文。 如果控制項的介面只使用英文，可能會造成一些問題。

一般而言，ActiveX 控制項應該永遠根據使用者的環境 LocaleID 屬性來設定其地區設定。 執行這項作業的方法有三種：

- 根據環境 LocaleID 屬性的目前值載入資源 (一定在需要時)。 MFC ActiveX 控制項範例[LOCALIZE](../overview/visual-cpp-samples.md)會使用此策略。

- 當第一個控制項是根據環境 LocaleID 屬性所建立的執行個體時就載入資源，並針對其他執行個體使用這些資源。 本文示範這個策略。

    > [!NOTE]
    >  如果未來的執行個體有不同的地區設定，則這種方法在某些情況下可能無法正常運作。

- 使用`OnAmbientChanged`通知函式，以動態方式載入容器的地區設定的適當資源。

    > [!NOTE]
    >  這種方法可在控制項中運作，不過，當環境 LocaleID 屬性變更時，執行階段 DLL 不會動態更新其資源。 此外，ActiveX 控制項的執行階段 DLL 會使用執行緒地區設定來決定其資源的地區設定。

本文的其他部分將說明兩種當地語系化的策略。 第一項策略[當地語系化控制項的可程式性介面](#_core_localizing_your_control.92.s_programmability_interface)（的屬性、 方法和事件的名稱）。 第二個策略[當地語系化控制項的使用者介面](#_core_localizing_the_control.92.s_user_interface)，使用容器的環境 LocaleID 屬性。 如需控制項當地語系化的示範，請參閱 MFC ActiveX 控制項範例[LOCALIZE](../overview/visual-cpp-samples.md)。

##  <a name="_core_localizing_your_control.92.s_programmability_interface"></a> 當地語系化控制項的可程式性介面

在當地語系化控制項的可程式性介面 (由使用您的控制項撰寫應用程式之程式設計人員所使用的介面) 的應用程式時，您必須為每種要支援的語言建立控制項 .IDL 檔案 (一種用於建立控制項類型程式庫的指令碼) 的修改版本。 這是唯一您需要當地語系化控制項屬性名稱的地方。

當您在開發當地語系化的控制項時，請在類型程式庫層級包含地區設定 ID 做為屬性。 例如，如果您要提供法文當地語系化屬性名稱的類型程式庫，請為您的 SAMPLE.IDL 檔案建立副本，並其命名為 SAMPLEFR.IDL。 加入地區設定 ID 屬性至檔案 (法文的地區設定 ID 是 0x040c)，如下所示：

[!code-cpp[NVC_MFC_AxLoc#1](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]

將 SAMPLEFR.IDL 中的屬性名稱變更為其對應的法文名稱，然後使用 MKTYPLIB.EXE 產生法文類型程式庫，即 SAMPLEFR.TLB。

若要建立多個當地語系化類型程式庫，您可以將任何已當地語系化的 .IDL 檔案加入至專案，即可自動建立這些當地語系化類型程式庫。

#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>將 .IDL 檔加入至您的 ActiveX 控制項專案

1. 控制項專案中開啟，請在**專案**功能表上，按一下**加入現有項目**。

   **加入現有項目** 對話方塊隨即出現。

1. 如果需要，請選取要檢視的磁碟機和目錄。

1. 在 **類型的檔案**方塊中，選取**的所有檔案 (\*。\*)**.

1. 在檔案清單方塊中，按兩下您想要插入至專案的 .IDL 檔案。

1. 按一下 **開啟**在您已新增所有必要。IDL 檔案。

由於檔案已加入至專案，這些檔案會在建置專案的其他部分時進行建置。 當地語系化的類型程式庫會位於目前的 ActiveX 控制項專案目錄。

在您的程式碼中，請永遠使用內部屬性名稱 (通常為英文) 且不要進行當地語系化。 這包括控制項分派對應、屬性交換函式和您的屬性頁資料交換程式碼。

只有一個類型程式庫 (.TLB) 檔可以繫結至控制項實作 (.OCX) 檔案的資源。 這通常是標準化 (通常是英文) 名稱的版本。 若要銷售當地語系化版本的控制項，您需要提供 .OCX (已繫結至預設 .TLB 版本) 和具有適當地區設定的 .TLB。 這表示只需要英文版本的 .OCX，因為已有與其繫結的正確 .TLB。 對於其他地區設定，當地語系化的類型程式庫也必須隨附於 .OCX 一起提供。

為了確保控制項的用戶端可以找到當地語系化類型程式庫，請在 Windows 系統登錄的 TypeLib 區段下註冊您的特定地區設定 .TLB 檔。 第三個參數 （通常是選擇性的） [AfxOleRegisterTypeLib](../mfc/reference/registering-ole-controls.md#afxoleregistertypelib)函式針對此目的提供。 下列範例會註冊 ActiveX 控制項的法文類型程式庫：

[!code-cpp[NVC_MFC_AxLoc#2](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]

當控制項已註冊時，`AfxOleRegisterTypeLib` 函式會自動在與控制項相同的目錄中尋找指定的 .TLB 檔，並在 Windows 系統登錄資料庫中註冊該檔案。 如果找不到 .TLB 檔案，函式不會有任何作用。

##  <a name="_core_localizing_the_control.92.s_user_interface"></a> 當地語系化控制項的使用者介面

若要當地語系化控制項的使用者介面，請將所有控制項的使用者可見資源 (例如屬性頁和錯誤訊息) 放置於語言專屬的資源 DLL 中。 然後您可以使用容器的環境 LocaleID 屬性為使用者的地區設定選取適當的 DLL。

下列程式碼範例將示範一種方法來尋找和載入特定地區設定的資源 DLL。 這個成員函式 (此例中為 `GetLocalizedResourceHandle`) 可以是您的 ActiveX 控制項類別的成員函式：

[!code-cpp[NVC_MFC_AxLoc#3](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]

請注意次語言 ID 可以 switch 陳述式中的每一種情況下檢查，以提供特製化程度較高的當地語系化。 如需示範此函式，請參閱`GetResourceHandle`函式，在 MFC ActiveX 控制項範例[LOCALIZE](../overview/visual-cpp-samples.md)。

當控制項第一次將自己載入容器時，它可以呼叫[colecontrol:: Ambientlocaleid](../mfc/reference/colecontrol-class.md#ambientlocaleid)擷取地區設定識別碼。 控制項接著會將所傳回的地區設定 ID 值傳遞到 `GetLocalizedResourceHandle` 函式，以便載入適當的資源程式庫。 如果有的話，控制項應該傳遞產生的控制代碼，來[AfxSetResourceHandle](../mfc/reference/application-information-and-management.md#afxsetresourcehandle):

[!code-cpp[NVC_MFC_AxLoc#4](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]

將上述程式碼範例放入控制項，例如覆寫的成員函式[colecontrol:: Onsetclientsite](../mfc/reference/colecontrol-class.md#onsetclientsite)。 颾魤 ㄛ *m_hResDLL*應該是控制項類別的成員變數。

您可以使用類似的邏輯來當地語系化控制項的屬性頁。 若要當地語系化的屬性頁面，將類似下列範例程式碼新增至屬性頁的實作檔 (中的覆寫[colepropertypage:: Onsetpagesite](../mfc/reference/colepropertypage-class.md#onsetpagesite)):

[!code-cpp[NVC_MFC_AxLoc#5](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)
