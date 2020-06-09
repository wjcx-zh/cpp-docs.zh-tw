---
title: 網際網路上的 ActiveX 控制項
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX controls [MFC], creating
- ActiveX controls [MFC], Internet
- downloading data with ActiveX controls
- OLE controls [MFC], upgrading to ActiveX
- Internet applications [MFC], ActiveX controls
- networks [MFC], downloading with ActiveX controls
ms.assetid: 7ab943c8-2022-41df-9065-d629b616eeec
ms.openlocfilehash: f06a6f6f71e922163fd95c59836c50b88b05ed3a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616484"
---
# <a name="activex-controls-on-the-internet"></a>網際網路上的 ActiveX 控制項

ActiveX 控制項是更新版本的 OLE 控制項規格。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

控制項是用於開發可程式化軟體元件的主要架構，可用於各種不同的容器，包括網際網路上 COM 感知的 Web 瀏覽器。 所有 ActiveX 控制項都可以是網際網路控制項，並可將其功能加入現用文件或成為網頁的一部分。 網頁上的控制項可以使用指令碼彼此通訊。

ActiveX 控制項不限於網際網路。 只要控制項支援容器所需的介面，ActiveX 控制項也可以用於所有容器。

**ActiveX 控制項有幾項優點，包括：**

- 所需的介面比先前的 OLE 控制項來得少。

- 可以是無視窗以及始終就地啟動。

**為了成為 ActiveX 控制項，控制項必須：**

- 支援 `IUnknown` 介面。

- 是個 COM 物件。

- 匯出**DLLRegisterServer**和**DLLUnRegisterServer**。

- 視功能所需支援其他介面。

## <a name="making-your-existing-controls-internet-friendly"></a>讓您現有的控制項容易在網際網路上使用

設計可在網際網路環境中正常運作的控制項，需要考量網際網路上相對低的傳輸速率。 您可以使用現有的控制項；不過，您應該採取幾個步驟讓您的程式碼大小較小以及非同步下載控制項屬性。

若要提高控制項的效能，考量效率時請遵循這些提示：

- 執行[ActiveX 控制項：優化](mfc-activex-controls-optimization.md)一文中所述的技術。

- 思考將控制項具現化的方式。

- 採非同步作業；不要阻擋其他程式。

- 下載小區塊中的資料。

   當下載大型資料流 (例如點陣圖或視訊資料) 時，配合容器非同步存取控制項的資料。 與其他可能也在擷取資料的控制項合作，以增量或漸進方式擷取資料。 程式碼也可以非同步下載。

- 在背景中下載程式碼和屬性。

- 盡快成為可用的使用者介面。

- 考慮如何儲存持續性資料，包括屬性和大型資料 BLOB (例如，點陣圖影像或視訊資料)。

   具有大量持續性資料的控制項 (例如，大型點陣圖或 AVI 檔案) 需要小心注意下載方法。 當控制項在背景中擷取資料時，資料或頁面可以盡快顯示，並讓使用者與頁面互動。

- 撰寫有效率的常式讓程式碼大小和執行階段保持最小。

   僅具有幾個位元組的持續性資料小按鈕和標籤控制項，適用於網際網路環境並在瀏覽器內運作正常。

- 考慮進度與容器通訊。

   通知容器非同步的下載進度，包括使用者何時可以開始與頁面互動以及何時下載完成。 容器可以向使用者顯示進度 (例如完成的百分比)。

- 考量在用戶端電腦上註冊控制項的方式。

## <a name="creating-a-new-activex-control"></a>建立新的 ActiveX 控制項

使用應用程式精靈建立新的控制項時，您可以選擇支援非同步 Moniker 以及其他最佳化。 若要增加非同步下載控制項屬性的支援，請依照下列步驟執行：

#### <a name="to-create-your-project-using-the-mfc-activex-control-wizard"></a>使用 MFC ActiveX 控制項精靈建立您的專案

1. 按一下 **[檔案**] 功能表上的 [**新增**]。

1. 從 Visual Studio c + + 專案中選取 [ **MFC ActiveX Control Wizard]** ，並為您的專案命名。

1. 在 [**控制設定**] 頁面上，選取 [**以非同步方式載入屬性**]。 選取此選項會為您設定就緒狀態屬性和就緒狀態變更的事件。

   您也可以選取其他優化，例如[ActiveX 控制項：優化](mfc-activex-controls-optimization.md)中所述的**無視窗啟用**。

1. 選擇 **[完成]** 以建立專案。

#### <a name="to-create-a-class-derived-from-cdatapathproperty"></a>建立從 CDataPathProperty 衍生的類別

1. 建立從 `CDataPathProperty` 衍生的類別。

1. 在每個包含控制項標頭檔的原始程式檔中，在它的前面加入此類別的標頭檔。

1. 在這個類別中，覆寫 `OnDataAvailable`。 每當有資料可供顯示時呼叫這個函式。 當資料可用時，您可以選擇的任何方法進行處理，例如逐步轉譯。

   下列程式碼摘要就是在編輯控制項中漸進顯示資料的簡易範例。 請注意，使用旗標**BSCF_FIRSTDATANOTIFICATION**清除編輯控制項。

   [!code-cpp[NVC_MFCActiveXControl#1](codesnippet/cpp/activex-controls-on-the-internet_1.cpp)]

   請注意，您必須包含 AFXCMN.H 才能使用 `CListCtrl` 類別。

1. 當控制項的整體狀態變更 (例如，從載入到初始化或使用者互動) 時，呼叫 `COleControl::InternalSetReadyState`。 如果您的控制項只有一個 [資料路徑] 屬性，您可以在**BSCF_LASTDATANOTIFICATION**上新增程式碼，以通知容器您的下載已完成。 例如：

   [!code-cpp[NVC_MFCActiveXControl#2](codesnippet/cpp/activex-controls-on-the-internet_2.cpp)]

1. 覆寫 `OnProgress`。 在 `OnProgress` 中，會傳遞給您一個數字顯示最大範圍以及一個數字顯示目前下載的進度。 您可以使用這些數字向使用者顯示狀態 (例如完成的百分比)。

下一個程序會將屬性加入至控制項，以使用剛衍生的類別。

#### <a name="to-add-a-property"></a>若要加入屬性

1. 在**類別檢視**中，以滑鼠右鍵按一下程式庫節點底下的介面，然後依序選取 [**新增**] 和 [**新增屬性**]。 這會啟動 [**新增屬性] Wizard**。

1. 在 [**加入屬性]** 中，選取 [**設定/取得方法**] 選項按鈕，輸入**屬性名稱**（例如 EDITCONTROLTEXT)），然後選取 [BSTR] 做為**屬性類型**。

1. 按一下 [完成] 。

1. 將 `CDataPathProperty` 衍生類別的成員變數，宣告為 ActiveX 控制項類別。

   [!code-cpp[NVC_MFCActiveXControl#3](codesnippet/cpp/activex-controls-on-the-internet_3.h)]

1. 實作 `Get/Set` 方法。 若為 `Get` ，則傳回字串。 對於 `Set`，載入屬性並呼叫 `SetModifiedFlag`。

   [!code-cpp[NVC_MFCActiveXControl#4](codesnippet/cpp/activex-controls-on-the-internet_4.cpp)]

1. 在[DoPropExchange](reference/colecontrol-class.md#dopropexchange)中，新增下列程式程式碼：

   [!code-cpp[NVC_MFCActiveXControl#5](codesnippet/cpp/activex-controls-on-the-internet_5.cpp)]

1. 覆寫[ResetData](reference/cdatapathproperty-class.md#resetdata)以通知屬性藉由新增這一行來重設其控制項：

   [!code-cpp[NVC_MFCActiveXControl#6](codesnippet/cpp/activex-controls-on-the-internet_6.cpp)]

## <a name="deciding-whether-to-derive-from-cdatapathproperty-or-ccacheddatapathproperty"></a>決定是否要從 CDataPathProperty 或 CCachedDataPathProperty 衍生

上述範例說明從 `CDataPathProperty` 衍生控制項屬性的步驟。 如果您將下載經常變更的即時資料，這是不錯的選擇，如此您就不需要保留所有資料，只會保留目前值。 範例是股票行情指示器控制項。

您也可以從 `CCachedDataPathProperty` 衍生。 在這種情況下，下載的資料會快取到記憶體檔案中。 如果您需要保留所有下載的資料 (例如，漸進轉譯點陣圖的控制項)，這是不錯的選擇。 在這個案例中，類別具有包含資料的成員變數：

`CMemFile m_Cache;`

在您的 ActiveX 控制項類別中，您可以在 `OnDraw` 中使用此記憶體對應檔來顯示資料。 在您的 ActiveX 控制項 `CCachedDataPathProperty` 衍生類別中，覆寫成員函式 `OnDataAvailable` 並在呼叫基底類別實作之後，使控制項失效。

[!code-cpp[NVC_MFCActiveXControl#7](codesnippet/cpp/activex-controls-on-the-internet_7.cpp)]

## <a name="downloading-data-asynchronously-using-activex-controls"></a>使用 ActiveX 控制項非同步下載資料

透過網路下載資料應該使用非同步方式。 這麼做的好處是如果轉換大量資料或者連線緩慢，下載程序也不會封鎖用戶端上的其他處理序。

非同步 Moniker 提供透過網路非同步下載資料的途徑。 即使作業尚未完成，非同步 Moniker 的讀取作業也會立即傳回。

例如，如果只有 10 個位元組可用且在 1K 檔案上非同步呼叫「讀取」，則不會封鎖讀取，但會傳回目前可用的 10 個位元組。

您可以使用類別來執行[非同步名字](asynchronous-monikers-on-the-internet.md) `CAsyncMonikerFile` 。 不過，ActiveX 控制項可以使用 `CDataPathProperty` 類別 (衍生自 `CAsyncMonikerFile`)，來協助實作非同步控制項屬性。

## <a name="displaying-a-control-on-a-web-page"></a>在網頁上顯示控制項

以下是供在網頁上插入控制項中的物件標記和屬性的範例。

```xml
<OBJECT
  CLASSID="clsid:FC25B780-75BE-11CF-8B01-444553540000"
  CODEBASE="/ie/download/activex/iechart.ocx"
  ID=chart1
  WIDTH=400
  HEIGHT=200
  ALIGN=center
  HSPACE=0
  VSPACE=0>
  <PARAM NAME="BackColor" value="#ffffff"/>
  <PARAM NAME="ForeColor" value="#0000ff"/>
  <PARAM NAME="url" VALUE="/ie/controls/chart/mychart.txt"/>
</OBJECT>
```

## <a name="updating-an-existing-ole-control-to-use-new-activex-control-features"></a>更新現有的 OLE 控制項以使用新的 ActiveX 控制項功能

如果您的 OLE 控制項是以 Visual C++ 4.2 之前的版本建立，則有些步驟是您可以採取，以改善其效能和增強其功能。 如需這些變更的詳細討論，請參閱[ActiveX 控制項：優化](mfc-activex-controls-optimization.md)。

如果您將非同步屬性支援加入至現有的控制項，您將需要自行加入就緒狀態屬性和 `ReadyStateChange` 事件。 在您的控制項的建構函式中，加入：

[!code-cpp[NVC_MFCActiveXControl#8](codesnippet/cpp/activex-controls-on-the-internet_8.cpp)]

您將會藉由呼叫[COleControl：： InternalSetReadyState](reference/colecontrol-class.md#internalsetreadystate)來更新您的程式碼，以更新就緒狀態。 您可以呼叫 `InternalSetReadyState` 的位置是從 `OnProgress` 衍生的類別覆寫 `CDataPathProperty`。

## <a name="see-also"></a>另請參閱

[MFC 網際網路程式設計工作](mfc-internet-programming-tasks.md)<br/>
[MFC 網際網路程式設計基本概念](mfc-internet-programming-basics.md)
