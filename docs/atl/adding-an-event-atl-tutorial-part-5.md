---
title: 加入事件 (ATL 教學課程，第 5 部分)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
ms.openlocfilehash: 57fc2adaadcca52cfc25736b5f9010fcb65a2ff0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278635"
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>加入事件 (ATL 教學課程，第 5 部分)

在此步驟中，您會將`ClickIn`和`ClickOut`ATL 控制項的事件。 您將會引發`ClickIn`事件，如果使用者按一下多邊形和火災內`ClickOut`如果使用者按一下之外。 要加入事件的工作如下所示：

- 新增`ClickIn`和`ClickOut`方法

- 產生類型程式庫

- 實作連接點介面

## <a name="adding-the-clickin-and-clickout-methods"></a>新增的 ClickIn 和 ClickOut 方法

當您在步驟 2 中建立 ATL 控制項時，您選取**連接點**核取方塊。 這個建立`_IPolyCtlEvents`Polygon.idl 檔案中的介面。 請注意，介面名稱以底線開頭。 這是慣例表示此介面是內部介面。 因此，讓您瀏覽 COM 物件的程式可以選擇不顯示使用者介面。 也請注意，選取**連接點**表示 Polygon.idl 檔案中加入下列這一行`_IPolyCtlEvents`是預設來源介面：

`[default, source] dispinterface _IPolyCtlEvents;`

來源屬性會指出控制項，做為來源的通知，使其將會在容器上呼叫此介面。

現在，加入`ClickIn`並`ClickOut`方法，以`_IPolyCtlEvents`介面。

### <a name="to-add-the-clickin-and-clickout-methods"></a>若要新增的 ClickIn 和 ClickOut 方法

1. 在 [**方案總管] 中**，開啟 Polygon.idl 並加入下列程式碼`methods:`中`dispInterface_IPolyCtlEvents`PolygonLib 程式庫的宣告：

    ```cpp
   [id(1), helpstring("method ClickIn")] void ClickIn([in] LONG x,[in] LONG y);
   [id(2), helpstring("method ClickOut")] void ClickOut([in] LONG x,[in] LONG y);
    ```

`ClickIn`和`ClickOut`方法接受 x 和 y 座標的按下點，做為參數。

## <a name="generating-the-type-library"></a>產生類型程式庫

此時，產生型別程式庫，因為專案將會用它來取得所建構的連接點介面和連接點容器介面控制項所需的資訊。

### <a name="to-generate-the-type-library"></a>若要產生類型程式庫

1. 重建您的專案。

     -或-

1. Polygon.idl 檔案中的以滑鼠右鍵按一下**方案總管**然後按一下**編譯**快顯功能表。

這會建立 Polygon.tlb 檔案，也就是您的型別程式庫。 Polygon.tlb 檔案不是可見的**方案總管 中**，因為它是二進位檔案，而且無法檢視或直接編輯。

## <a name="implementing-the-connection-point-interfaces"></a>實作連接點介面

實作連接點介面和連接點容器介面，為您的控制項。 在 COM 中，事件會透過連接點的機制來實作。 若要從 COM 物件接收事件，容器會建立 COM 物件實作連接點的諮詢連接。 COM 物件可以有多個連接點，因為 COM 物件也會實作連接點容器介面。 透過這個介面，容器就可以判斷哪一個連接點所支援。

實作連接點的介面稱為`IConnectionPoint`，並實作連接點容器的介面稱為`IConnectionPointContainer`。

若要協助實作`IConnectionPoint`，您將使用實作連接點精靈。 這個精靈會產生`IConnectionPoint`藉由讀取類型程式庫，並實作可以引發的每個事件的函式的介面。

### <a name="to-implement-the-connection-points"></a>實作連接點

1. 在 [**方案總管] 中**，開啟 _IPolyCtlEvents_CP.h 並加入下列程式碼底下`public:`陳述式中的`CProxy_IPolyCtlEvents`類別：

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

您會看到這個檔案的類別，稱為`CProxy_IPolyCtlEvents`衍生自`IConnectionPointImpl`。 _IPolyCtlEvents_CP.h 現在定義的兩種方法`Fire_ClickIn`和`Fire_ClickOut`，這需要兩個座標的參數。 當您想要引發的事件，從您的控制項時，您就會呼叫這些方法。

藉由建立與控制項**連接點**為您產生選取的選項，_IPolyCtlEvents_CP.h 檔案。 It 也加入`CProxy_PolyEvents`並`IConnectionPointContainerImpl`控制項的多個繼承清單和公開`IConnectionPointContainer`為您的 COM 對應中加入適當的項目。

您已完成實作支援事件的程式碼。 現在，加入一些程式碼以在適當時間引發事件。 請記住，就會引發`ClickIn`或`ClickOut`當使用者按一下滑鼠左的按鈕控制項中的事件。 若要了解，當使用者按一下按鈕，新增的處理常式`WM_LBUTTONDOWN`訊息。

### <a name="to-add-a-handler-for-the-wmlbuttondown-message"></a>若要新增 WM_LBUTTONDOWN 訊息的處理常式

1. 在 **類別檢視**，以滑鼠右鍵按一下`CPolyCtl`類別，並按一下 **屬性**快顯功能表上。

1. 在 [**屬性**] 視窗中，按一下**訊息**圖示，然後按一下`WM_LBUTTONDOWN`從左邊的清單。

1. 從出現的下拉式清單中，按一下**\<新增 > OnLButtonDown**。 `OnLButtonDown`處理常式宣告將會加入至 PolyCtl.h，並將處理常式實作會加入 PolyCtl.cpp。

接下來，修改這個處理常式。

### <a name="to-modify-the-onlbuttondown-method"></a>若要修改 OnLButtonDown 方法

1. 變更程式碼，包含`OnLButtonDown`PolyCtl.cpp （刪除由精靈所放置的任何程式碼） 中的方法，讓它看起來像這樣：

    [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]

使用點計算中的程式碼這樣`OnDraw`函式來建立的區域，偵測到使用者的滑鼠點按呼叫`PtInRegion`。

*UMsg*參數是要處理 Windows 訊息的識別碼。 這可讓您有一個函式會處理一個範圍的訊息。 *WParam*並*lParam*參數都是處理訊息的標準值。 參數*bHandled*可讓您指定是否函式或不處理訊息。 根據預設，值設為 TRUE，表示函式會處理訊息，但是您可以將它設定為 FALSE。 這會繼續尋找其他訊息處理常式函式，來傳送訊息給 ATL。

## <a name="building-and-testing-the-control"></a>建置和測試控制項

立即試用您的事件。 建置控制項，然後重新啟動 ActiveX 控制項測試容器。 此時，檢視事件記錄檔 視窗。 若要將事件路由至 [輸出] 視窗中，按一下**記錄**從**選項**功能表，然後選取**記錄至輸出視窗**。 插入控制項並嘗試按一下視窗中。 請注意，`ClickIn`如果您按一下 填滿的多邊形，內引發和`ClickOut`當您按一下 外部時會引發。

接下來，您將加入的屬性頁。

[回到步驟 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [至步驟 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="see-also"></a>另請參閱

[教學課程](../atl/active-template-library-atl-tutorial.md)
