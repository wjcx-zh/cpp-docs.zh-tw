---
title: 加入事件 (ATL 教學課程，第 5 部分)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
ms.openlocfilehash: c9a7c6f38a2f47ec808081e440a200737ad1928a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127570"
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>加入事件 (ATL 教學課程，第 5 部分)

在此步驟中，您會將 `ClickIn` 和 `ClickOut` 事件新增至您的 ATL 控制項。 如果使用者按一下多邊形內的 `ClickIn` 事件，並在使用者按一下 [外部] 時引發 `ClickOut`，您將會引發。 新增事件的工作如下所示：

- 新增 `ClickIn` 和 `ClickOut` 方法

- 產生類型程式庫

- 執行連接點介面

## <a name="adding-the-clickin-and-clickout-methods"></a>新增 ClickIn 和 ClickOut 方法

當您在步驟2中建立 ATL 控制項時，您已選取 [**連接點**] 核取方塊。 這會在多邊形 .idl 檔案中建立 `_IPolyCtlEvents` 介面。 請注意，介面名稱是以底線開頭。 這是指示介面為內部介面的慣例。 因此，可讓您流覽 COM 物件的程式可以選擇不要向使用者顯示介面。 另請注意，選取**連接點**會在多邊形 .idl 檔案中加入下列這一行，以指出 `_IPolyCtlEvents` 是預設來源介面：

`[default, source] dispinterface _IPolyCtlEvents;`

[來源] 屬性指出控制項是通知的來源，因此它會在容器上呼叫此介面。

現在，將 `ClickIn` 和 `ClickOut` 方法新增至 `_IPolyCtlEvents` 介面。

### <a name="to-add-the-clickin-and-clickout-methods"></a>若要新增 ClickIn 和 ClickOut 方法

1. 在**方案總管**中，開啟多邊形 .idl，並在 PolygonLib 程式庫的 `dispInterface_IPolyCtlEvents` 宣告中的 `methods:` 下新增下列程式碼：

    ```cpp
   [id(1), helpstring("method ClickIn")] void ClickIn([in] LONG x,[in] LONG y);
   [id(2), helpstring("method ClickOut")] void ClickOut([in] LONG x,[in] LONG y);
    ```

`ClickIn` 和 `ClickOut` 方法會將所選點的 x 和 y 座標當做參數。

## <a name="generating-the-type-library"></a>產生類型程式庫

此時產生類型程式庫，因為專案將使用它來取得為您的控制項建立連接點介面和連接點容器介面所需的資訊。

### <a name="to-generate-the-type-library"></a>產生類型程式庫

1. 重建您的專案。

     -或-

1. 以滑鼠右鍵按一下**方案總管**中的多邊形 .idl 檔案，然後按一下快捷方式功能表上的 [**編譯**]。

這會建立多邊形 .tlb 檔案，也就是您的類型程式庫。 無法從**方案總管**看到多邊形 .tlb 檔案，因為它是二進位檔案，無法直接查看或編輯。

## <a name="implementing-the-connection-point-interfaces"></a>執行連接點介面

執行控制項的連接點介面和連接點容器介面。 在 COM 中，事件是透過連接點的機制來執行。 為了接收 COM 物件的事件，容器會建立與 COM 物件所執行之連接點的諮詢連接。 因為 COM 物件可以有多個連接點，所以 COM 物件也會執行連接點容器介面。 透過這個介面，容器可以判斷支援哪些連接點。

執行連接點的介面稱為 `IConnectionPoint`，而執行連接點容器的介面則稱為 `IConnectionPointContainer`。

為了協助執行 `IConnectionPoint`，您將使用「執行連接點」 Wizard。 此 wizard 會藉由讀取您的類型程式庫，並針對每個可以引發的事件來執行函式，以產生 `IConnectionPoint` 介面。

### <a name="to-implement-the-connection-points"></a>若要執行連接點

1. 在**方案總管**中，開啟 _IPolyCtlEvents_CP，然後在 `CProxy_IPolyCtlEvents` 類別的 `public:` 語句底下新增下列程式碼：

    ```cpp
    VOID Fire_ClickIn(LONG x, LONG y)
    {
        T* pT = static_cast<T*>(this);
        int nConnectionIndex;
        CComVariant* pvars = new CComVariant[2];
        int nConnections = m_vec.GetSize();

        for (nConnectionIndex = 0; nConnectionIndex < nConnections; nConnectionIndex++)
        {
            pT->Lock();
            CComPtr<IUnknown> sp = m_vec.GetAt(nConnectionIndex);
            pT->Unlock();
            IDispatch* pDispatch = reinterpret_cast<IDispatch*>(sp.p);
            if (pDispatch != NULL)
            {
                pvars[1].vt = VT_I4;
                pvars[1].lVal = x;
                pvars[0].vt = VT_I4;
                pvars[0].lVal = y;
                DISPPARAMS disp = { pvars, NULL, 2, 0 };
                pDispatch->Invoke(0x1, IID_NULL, LOCALE_USER_DEFAULT, DISPATCH_METHOD, &disp, NULL, NULL, NULL);
            }
        }
        delete[] pvars;

    }
    VOID Fire_ClickOut(LONG x, LONG y)
    {
        T* pT = static_cast<T*>(this);
        int nConnectionIndex;
        CComVariant* pvars = new CComVariant[2];
        int nConnections = m_vec.GetSize();

        for (nConnectionIndex = 0; nConnectionIndex < nConnections; nConnectionIndex++)
        {
            pT->Lock();
            CComPtr<IUnknown> sp = m_vec.GetAt(nConnectionIndex);
            pT->Unlock();
            IDispatch* pDispatch = reinterpret_cast<IDispatch*>(sp.p);
            if (pDispatch != NULL)
            {
                pvars[1].vt = VT_I4;
                pvars[1].lVal = x;
                pvars[0].vt = VT_I4;
                pvars[0].lVal = y;
                DISPPARAMS disp = { pvars, NULL, 2, 0 };
                pDispatch->Invoke(0x2, IID_NULL, LOCALE_USER_DEFAULT, DISPATCH_METHOD, &disp, NULL, NULL, NULL);
            }
        }
        delete[] pvars;

    }
    ```

您會看到這個檔案有一個稱為 `CProxy_IPolyCtlEvents` 的類別，衍生自 `IConnectionPointImpl`。 _IPolyCtlEvents_CP 現在會定義 `Fire_ClickIn` 和 `Fire_ClickOut`的兩個方法，其採用兩個座標參數。 當您想要從控制項引發事件時，可以呼叫這些方法。

藉由選取 [使用**連接點**建立控制項] 選項，就會為您產生 _IPolyCtlEvents_CP .h 檔案。 它也會將 `CProxy_PolyEvents` 和 `IConnectionPointContainerImpl` 加入控制項的多重繼承清單中，並藉由將適當的專案加入至 COM 對應，為您公開 `IConnectionPointContainer`。

您已完成執行程式碼以支援事件。 現在，請新增一些程式碼，以便在適當的時間引發事件。 請記住，當使用者按一下控制項中的滑鼠左鍵時，就會引發 `ClickIn` 或 `ClickOut` 事件。 若要找出使用者按一下按鈕的時間，請加入 `WM_LBUTTONDOWN` 訊息的處理常式。

### <a name="to-add-a-handler-for-the-wm_lbuttondown-message"></a>若要加入 WM_LBUTTONDOWN 訊息的處理常式

1. 在**類別檢視**中，以滑鼠右鍵按一下 `CPolyCtl` 類別，然後按一下快捷方式功能表上的 [**屬性**]。

1. 在 [**屬性**] 視窗中，按一下 [**訊息**] 圖示，然後按一下左側清單中的 [`WM_LBUTTONDOWN`]。

1. 從出現的下拉式清單中，按一下 [ **\<新增 > OnLButtonDown**]。 `OnLButtonDown` 處理常式宣告會加入至 PolyCtl，而且處理常式的執行會加入至 PolyCtl。

接下來，修改處理常式。

### <a name="to-modify-the-onlbuttondown-method"></a>修改 OnLButtonDown 方法

1. 變更 PolyCtl 中包含 `OnLButtonDown` 方法的程式碼（刪除 wizard 所放置的任何程式碼），使其看起來像這樣：

    [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]

這段程式碼會使用在 `OnDraw` 函式中計算的點來建立區域，以透過呼叫 `PtInRegion`來偵測使用者的滑鼠點擊。

*UMsg*參數是要處理之 Windows 訊息的識別碼。 這可讓您擁有一個函式來處理某個範圍的訊息。 *WParam*和*lParam*參數是所處理之訊息的標準值。 參數*bHandled*可讓您指定函數是否處理訊息。 根據預設，此值會設定為 TRUE，表示函式已處理訊息，但您可以將它設定為 FALSE。 這會導致 ATL 繼續尋找另一個訊息處理常式函式，以將訊息傳送至。

## <a name="building-and-testing-the-control"></a>建置和測試控制項

立即試用您的活動。 建立控制項，並再次啟動 ActiveX 控制項測試容器。 此時，請查看 [事件記錄檔] 視窗。 若要將事件路由至 [輸出] 視窗，請從 [**選項**] 功能表按一下 [**記錄**]，然後選取 [記錄**到輸出視窗]** 。 插入控制項，然後嘗試在視窗中按一下。 請注意，如果您在填滿的多邊形內按一下，就會引發 `ClickIn`，而當您按一下其外部時，`ClickOut` 就會引發。

接下來，您將新增屬性頁。

[回到步驟 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [的步驟 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="see-also"></a>另請參閱

[教學課程](../atl/active-template-library-atl-tutorial.md)
