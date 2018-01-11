---
title: "動態配置 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e309d8ef023346c0e37babeabe23f7e6e1762939
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="dynamic-layout"></a>動態版面配置
Mfc 在 Visual Studio 2015 中，您可以建立對話方塊，使用者可以調整大小，而且您可以控制配置調整大小的變更的方式。 例如，您可以將對話方塊底部的按鈕附加至下邊緣，使其永遠保持在底部。 您也可以設定特定的控制項，例如清單方塊、編輯方塊和文字欄位，在使用者展開對話方塊時展開。  
  
## <a name="specifying-dynamic-layout-settings-for-an-mfc-dialog-box"></a>指定 MFC 對話方塊的動態配置設定  
 當使用者調整對話方塊時，對話方塊中的控制項可以調整大小，或以 X 和 Y 方向移動。 在使用者調整對話方塊大小時，控制項大小或位置的變更即稱為動態配置。 例如，下列是調整大小之前的對話方塊：  
  
 ![調整大小之前的對話方塊。] (../mfc/media/mfcdynamiclayout4.png "mfcdynamiclayout4")  
  
 調整大小之後，清單方塊區域會加大以顯示更多的項目，按鈕則會隨右下角移動：  
  
 ![調整大小之後的對話方塊。] (../mfc/media/mfcdynamiclayout5.png "mfcdynamiclayout5")  
  
 您可以在 IDE 的資源編輯器中指定每個控制項的詳細資料，以便控制動態配置，也可以用程式設計方式進行，亦即存取特定控制項的 CMFCDynamicLayout 物件並設定屬性。  
  
### <a name="setting-dynamic-layout-properties-in-the-resource-editor"></a>在資源編輯器中設定動態配置屬性  
 您可以使用資源編輯器設定對話方塊的動態配置行為，而不需要撰寫任何程式碼。  
  
##### <a name="to-set-dynamic-layout-properties-in-the-resource-editor"></a>在資源編輯器中設定動態配置屬性  
  
1.  在 MFC 專案開啟的狀態下，於對話方塊編輯器中開啟您想要使用的對話方塊。  
  
     ![資源編輯器中開啟對話方塊。] (../mfc/media/mfcdynamiclayout3.png "mfcdynamiclayout3")  
  
2.  選取控制項，並在 [屬性] 視窗中設定其動態配置屬性。 **動態配置**屬性 視窗中的區段包含內容**移動類型**，**調整大小類型**，並根據這些屬性中，選取的值定義多少控制項移動或大小改變的特定屬性。 **移動類型**決定如何移動控制項變更對話方塊的大小。**調整大小類型**如何調整控制項的大小會決定變更對話方塊的大小。 **移動類型**和**調整大小類型**可能**水平**，**垂直**，**兩者**，或**無**根據您想要以動態方式變更的維度。 水平是 X 維度 ；垂直是 Y 方向。  
  
3.  如果您想在固定的大小，並在右下方會保留按鈕等控制項，做為是很常見的**確定**或**取消**按鈕，設定**調整大小類型**至**無**，並設定**移動類型**至**兩者**。 如**移動 X**和**移動 Y**值下**移動類型**，設定 100%來讓保持固定的距離從底端右下角的控制項。  
  
     ![動態配置](../mfc/media/mfcdynamiclayout1.png "mfcdynamiclayout1")  
  
4.  假設您也有想要在對話方塊展開時加以展開的控制項。 一般而言，使用者可能會展開對話方塊，以展開多行編輯方塊，增加文字區域的大小，或者可能會展開清單控制項以查看詳細資料。 此案例中，設定**調整大小類型**兩者，並設定**移動類型**為 none。 然後，設定**調整大小 X**和**調整大小 Y**到 100 的值。  
  
     ![動態版面配置設定](../mfc/media/mfcdynamiclayout2.png "mfcdynamiclayout2")  
  
5.  實驗其他可能對您的控制項有意義的值。 單行文字方塊的對話方塊可能會有**調整大小類型**設**水平**僅為範例。  
  
### <a name="setting-dynamic-layout-properties-programmatically"></a>以程式設計方式設定動態配置屬性  
 上一個程序可用於在設計階段指定對話方塊的動態配置屬性，但如果您想要在執行階段控制動態配置，可以透過程式設計方式設定動態配置屬性。  
  
##### <a name="to-set-dynamic-layout-properties-programmatically"></a>以程式設計方式設定動態配置屬性  
  
1.  在對話方塊類別的實作程式碼中，尋找或建立一個您要為對話指定動態配置的位置。 例如，您可能會想要在對話方塊中加入 `AdjustLayout` 這樣的方法，並從需要變更配置的位置呼叫它。 您可能會先從建構函式呼叫它，或在變更對話方塊後呼叫。  
  
2.  對話方塊中，針對呼叫[GetDynamicLayout](../mfc/reference/cwnd-class.md#getdynamiclayout)，CWnd 類別的方法。 GetDynamicLayout 會將指標傳回 CMFCDynamicLayout 物件。  
  
 ```  
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();

 ```  
  
3.  針對您要加入動態行為的第一個控制項，使用靜態方法上的動態配置類別來建立[MoveSettings](../mfc/reference/cmfcdynamiclayout-class.md#movesettings_structure)控制項應調整的方式編碼的結構。 做法是第一個選擇適當的靜態方法： [cmfcdynamiclayout:: Movehorizontal](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontal)， [cmfcdynamiclayout:: Movevertical](../mfc/reference/cmfcdynamiclayout-class.md#movevertical)， [cmfcdynamiclayout:: Movenone](../mfc/reference/cmfcdynamiclayout-class.md#movenone)，或[cmfcdynamiclayout:: Movehorizontalandvertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical)。 傳入移動之水平和/或垂直層面的百分比。 這些靜態方法全都會傳回新建立的 MoveSettings 物件，可讓您指定控制項的移動行為。  
  
     請記住，100 表示移動的量與對話方塊變更大小的量剛好相等，這會使控制項的邊緣與新框線保持固定距離。  
  
 ```  
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);

 ```  
  
4.  執行相同的動作，大小行為，它會使用[SizeSettings](../mfc/reference/cmfcdynamiclayout-class.md#sizesettings_structure)型別。 例如，若要指定控制項在重新調整對話方塊大小時不會變更大小，請使用下列程式碼：  
  
 ```  
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();

 ```  
  
5.  將控制項加入動態配置管理員使用[cmfcdynamiclayout:: Additem](../mfc/reference/cmfcdynamiclayout-class.md#additem)方法。 指定想要之控制項的不同方式有兩個多載。 一個採用控制項的視窗控制代碼 (HWND)，另一個採用控制項 ID。  
  
 ```  
    dynamicLayout->AddItem(hWndControl,
    moveSettings,
    sizeSettings);

 ```  
  
6.  針對每個需要移動或調整大小的控制項重複進行。  
  
7.  如果有必要，可以使用[cmfcdynamiclayout:: Hasitem](../mfc/reference/cmfcdynamiclayout-class.md#hasitem)方法，以判斷控制項是否已經在進行配置變更，控制項的清單或[cmfcdynamiclayout:: Isempty](../mfc/reference/cmfcdynamiclayout-class.md#isempty)若要判斷是否有任何變更的控制項的方法。  
  
8.  若要啟用對話方塊版面配置，請呼叫[cwnd:: Enabledynamiclayout](../mfc/reference/cwnd-class.md#enabledynamiclayout)方法。  
  
 ```  
    pDialog->EnableDynamicLayout(TRUE);

 ```  
  
9. 使用者調整對話方塊中，在下一次[cmfcdynamiclayout:: Adjust](../mfc/reference/cmfcdynamiclayout-class.md#adjust)會呼叫方法，它會實際套用設定。  
  
10. 如果您想要停用動態配置，呼叫[cwnd:: Enabledynamiclayout](../mfc/reference/cwnd-class.md#enabledynamiclayout)與`FALSE`與`bEnabled`參數。  
  
 ```  
    pDialog->EnableDynamicLayout(FALSE);

 ```  
  
##### <a name="to-set-the-dynamic-layout-programmatically-from-a-resource-file"></a>從資源檔以程式設計方式設定動態配置  
  
1.  使用[cmfcdynamiclayout:: Movehorizontalandvertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical)方法，以指定動態配置資訊，如下列範例所示的相關資源指令碼檔 （.rc 檔） 中指定的資源名稱：  
  
 ```  
    dynamicLayout->LoadResource("IDD_DIALOG1");

 ```  
  
     具名的資源必須參考包含配置資訊的對話方塊，其形式為資源檔中的 AFX_DIALOG_LAYOUT 項目，如下列範例所示：  
  
 '' * / / * / / * / / AFX_DIALOG_LAYOUT * / /  
 
    IDD_MFCAPPLICATION1_DIALOG AFX_DIALOG_LAYOUT  
    開始 0X0000、 0X6400、 0X0028、 0X643C、 0X0028  
    END 
 
    IDD_DIALOG1 AFX_DIALOG_LAYOUT  
    開始 0X0000、 0X6464、 0X0000、 0X6464、 0X0000、 0X0000、 0X6464、 0X0000、 0X0000  
 
    END 
 ```  
  
## See Also  
 [CMFCDynamicLayout Class](../mfc/reference/cmfcdynamiclayout-class.md)   
 [Control Classes](../mfc/control-classes.md)   
 [Dialog Box Classes](../mfc/dialog-box-classes.md)   
 [Dialog Editor](../windows/dialog-editor.md)

