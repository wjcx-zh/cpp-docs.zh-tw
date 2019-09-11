---
title: 動態版面配置
ms.date: 09/09/2019
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
ms.openlocfilehash: 1b0d035d3c551fd309d515ccb8b22159218c1b0a
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907554"
---
# <a name="dynamic-layout"></a>動態版面配置

使用 Visual Studio 2015 中的 MFC，您可以建立使用者可以調整大小的對話方塊，而且可以控制配置調整大小變更的方式。 例如，您可以將對話方塊底部的按鈕附加至下邊緣，使其永遠保持在底部。 您也可以設定特定的控制項，例如清單方塊、編輯方塊和文字欄位，在使用者展開對話方塊時展開。

## <a name="specifying-dynamic-layout-settings-for-an-mfc-dialog-box"></a>指定 MFC 對話方塊的動態配置設定

當使用者調整對話方塊時，對話方塊中的控制項可以調整大小，或以 X 和 Y 方向移動。 在使用者調整對話方塊大小時，控制項大小或位置的變更即稱為動態配置。 例如，下列是調整大小之前的對話方塊：

重新重設![大小之前的對話方塊。]重新重設(../mfc/media/mfcdynamiclayout4.png "大小之前的對話方塊。")

調整大小之後，清單方塊區域會加大以顯示更多的項目，按鈕則會隨右下角移動：

重設![大小之後的對話方塊。]重設(../mfc/media/mfcdynamiclayout5.png "大小之後的對話方塊。")

您可以在 IDE 的資源編輯器中指定每個控制項的詳細資料，以控制動態配置，也可以藉由存取`CMFCDynamicLayout`特定控制項的物件並設定屬性，以程式設計方式來執行此動作。

### <a name="setting-dynamic-layout-properties-in-the-resource-editor"></a>在資源編輯器中設定動態配置屬性

您可以使用資源編輯器設定對話方塊的動態配置行為，而不需要撰寫任何程式碼。

#### <a name="to-set-dynamic-layout-properties-in-the-resource-editor"></a>在資源編輯器中設定動態配置屬性

1. 在 MFC 專案開啟的狀態下，於對話方塊編輯器中開啟您想要使用的對話方塊。

   ![在資源編輯器中開啟對話方塊。](../mfc/media/mfcdynamiclayout3.png "在資源編輯器中開啟對話方塊。")

1. 選取控制項，然後在 [**屬性**] 視窗（**類別檢視**中），設定其動態版面配置屬性。 [**屬性**] 視窗中的 [**動態**配置] 區段包含屬性**移動類型**、重設**大小類型**，以及根據為這些屬性選取的值，定義要移動多少控制項的特定屬性，或變更大小。 [**移動類型**] 決定當對話方塊的大小變更時，控制項的移動方式。[重設**大小類型**] 決定當對話方塊的大小變更時，控制項的大小調整方式。 **移動類型**和**大小調整類型**可能是**水準**、**垂直**、**兩者**或**無**，視您想要動態變更的維度而定。 水平是 X 維度 ；垂直是 Y 方向。

1. 如果您想要控制項（例如按鈕）為固定大小，並留在右下方，如同 [**確定]** 或 [**取消**] 按鈕的常見情況，請將**大小調整類型**設定為 [**無**]，並將**移動類型**設定為 [**兩者**]。 針對 [**移動類型**] 下的 [**移動 X** ] 和 [**移動 Y** ] 值，設定 [100%]，讓控制項從右下角保持固定的距離。

   ![動態版面]配置(../mfc/media/mfcdynamiclayout1.png "動態版面")配置

1. 假設您也有想要在對話方塊展開時加以展開的控制項。 一般而言，使用者可能會展開對話方塊，以展開多行編輯方塊，增加文字區域的大小，或者可能會展開清單控制項以查看詳細資料。 在此情況下，請將**大小調整類型**設定為 [兩者]，並將 [**移動類型**] 設為 [無]。 然後，將 [重設**大小 X** ] 和 [**調整 Y 值大小**] 設定為100。

   ![動態版面配置設定](../mfc/media/mfcdynamiclayout2.png "動態版面配置設定")

1. 實驗其他可能對您的控制項有意義的值。 例如，具有單行文字方塊的對話方塊可能會將重設**大小的類型**設定為 [**水準**]。

### <a name="setting-dynamic-layout-properties-programmatically"></a>以程式設計方式設定動態配置屬性

上一個程序可用於在設計階段指定對話方塊的動態配置屬性，但如果您想要在執行階段控制動態配置，可以透過程式設計方式設定動態配置屬性。

#### <a name="to-set-dynamic-layout-properties-programmatically"></a>以程式設計方式設定動態配置屬性

1. 在對話方塊類別的實作程式碼中，尋找或建立一個您要為對話指定動態配置的位置。 例如，您可能會想要在對話方塊中加入 `AdjustLayout` 這樣的方法，並從需要變更配置的位置呼叫它。 您可能會先從建構函式呼叫它，或在變更對話方塊後呼叫。

1. 針對對話方塊，呼叫[GetDynamicLayout](../mfc/reference/cwnd-class.md#getdynamiclayout)，這是`CWnd`類別的方法。 `GetDynamicLayout` 傳回 `CMFCDynamicLayout` 物件的指標。

    ```cpp
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();
    ```

1. 針對您要加入動態行為的第一個控制項，請在動態配置類別上使用靜態方法來建立[MoveSettings](../mfc/reference/cmfcdynamiclayout-class.md#movesettings_structure)結構，以編碼控制項的調整方式。 若要這麼做，請先選擇適當的靜態方法：[CMFCDynamicLayout：： MoveHorizontal](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontal)、 [CMFCDynamicLayout：： MoveVertical](../mfc/reference/cmfcdynamiclayout-class.md#movevertical)、 [CMFCDynamicLayout：： MoveNone](../mfc/reference/cmfcdynamiclayout-class.md#movenone)或[CMFCDynamicLayout：： MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical)。 傳入移動之水平和/或垂直層面的百分比。 這些靜態方法全都會傳回新建立的 MoveSettings 物件，可讓您指定控制項的移動行為。

   請記住，100 表示移動的量與對話方塊變更大小的量剛好相等，這會使控制項的邊緣與新框線保持固定距離。

    ```cpp
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);
    ```

1. 針對大小行為執行相同的動作，這是使用[SizeSettings](../mfc/reference/cmfcdynamiclayout-class.md#sizesettings_structure)類型。 例如，若要指定控制項在重新調整對話方塊大小時不會變更大小，請使用下列程式碼：

    ```cpp
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();
    ```

1. 使用[CMFCDynamicLayout：： AddItem](../mfc/reference/cmfcdynamiclayout-class.md#additem)方法，將控制項新增至動態建構管理員。 指定想要之控制項的不同方式有兩個多載。 一個採用控制項的視窗控制代碼 (HWND)，另一個採用控制項 ID。

    ```cpp
    dynamicLayout->AddItem(hWndControl,
    moveSettings,
    sizeSettings);
    ```

1. 針對每個需要移動或調整大小的控制項重複進行。

1. 如有必要，可以使用[CMFCDynamicLayout：： HasItem](../mfc/reference/cmfcdynamiclayout-class.md#hasitem)方法來判斷控制項是否已經在受限於動態配置變更的控制項清單上，或[CMFCDynamicLayout：： IsEmpty](../mfc/reference/cmfcdynamiclayout-class.md#isempty)方法來判斷是否有任何控制項受限於變更。

1. 若要啟用對話方塊版面配置，請呼叫[CWnd：： EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout)方法。

    ```cpp
    pDialog->EnableDynamicLayout(TRUE);
    ```

1. 下一次使用者調整對話方塊大小時，會呼叫[CMFCDynamicLayout：：調整](../mfc/reference/cmfcdynamiclayout-class.md#adjust)方法，實際套用設定。

1. 如果您想要停用動態配置，請呼叫[CWnd：： EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) ，並使用**FALSE**作為*bEnabled*參數的。

    ```cpp
    pDialog->EnableDynamicLayout(FALSE);
    ```

#### <a name="to-set-the-dynamic-layout-programmatically-from-a-resource-file"></a>從資源檔以程式設計方式設定動態配置

1. 使用[CMFCDynamicLayout：： MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical)方法，在相關的資源腳本檔案（.rc 檔）中指定指定動態配置資訊的資源名稱，如下列範例所示：

    ```cpp
    dynamicLayout->LoadResource("IDD_DIALOG1");
    ```

   已命名的資源必須以資源檔中**AFX_DIALOG_LAYOUT**專案的形式，參考包含版面配置資訊的對話方塊，如下列範例所示：

    ```RC
    /////////////////////////////////////////////////////////////////////////////
    //
    // AFX_DIALOG_LAYOUT
    //

    IDD_MFCAPPLICATION1_DIALOG AFX_DIALOG_LAYOUT
    BEGIN
    0x0000,
    0x6400,
    0x0028,
    0x643c,
    0x0028
    END

    IDD_DIALOG1 AFX_DIALOG_LAYOUT
    BEGIN
    0x0000,
    0x6464,
    0x0000,
    0x6464,
    0x0000,
    0x0000,
    0x6464,
    0x0000,
    0x0000

    END
    ```

## <a name="see-also"></a>另請參閱

[CMFCDynamicLayout 類別](../mfc/reference/cmfcdynamiclayout-class.md)<br/>
[控制項類別](../mfc/control-classes.md)<br/>
[對話方塊類別](../mfc/dialog-box-classes.md)<br/>
[對話方塊編輯器](../windows/dialog-editor.md)<br/>
[Visual C++ 2015 中 MFC 的動態對話版面配置](https://mariusbancila.ro/blog/2015/07/27/dynamic-dialog-layout-for-mfc-in-visual-c-2015/)
