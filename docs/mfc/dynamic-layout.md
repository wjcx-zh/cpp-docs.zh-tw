---
title: "動態版面配置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# 動態版面配置
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中的 MFC，可建立使用者能夠調整大小的對話方塊，而且您可以控制配置調整大小變更的方式。  例如，您可以將對話方塊底部的按鈕附加至下邊緣，使其永遠保持在底部。  您也可以設定特定的控制項，例如清單方塊、編輯方塊和文字欄位，在使用者展開對話方塊時展開。  
  
## 指定 MFC 對話方塊的動態配置設定  
 當使用者調整對話方塊時，對話方塊中的控制項可以調整大小，或以 X 和 Y 方向移動。  在使用者調整對話方塊大小時，控制項大小或位置的變更即稱為動態配置。  例如，下列是調整大小之前的對話方塊：  
  
 ![調整大小之前的對話方塊。](../mfc/media/mfcdynamiclayout4.png "MFCDynamicLayout4")  
  
 調整大小之後，清單方塊區域會加大以顯示更多的項目，按鈕則會隨右下角移動：  
  
 ![調整大小之後的對話方塊。](../mfc/media/mfcdynamiclayout5.png "MFCDynamicLayout5")  
  
 您可以在 IDE 的資源編輯器中指定每個控制項的詳細資料，以便控制動態配置，也可以用程式設計方式進行，亦即存取特定控制項的 CMFCDynamicLayout 物件並設定屬性。  
  
### 在資源編輯器中設定動態配置屬性  
 您可以使用資源編輯器設定對話方塊的動態配置行為，而不需要撰寫任何程式碼。  
  
##### 在資源編輯器中設定動態配置屬性  
  
1.  在 MFC 專案開啟的狀態下，於對話方塊編輯器中開啟您想要使用的對話方塊。  
  
     ![在資源編輯器中開啟對話方塊。](../mfc/media/mfcdynamiclayout3.png "MFCDynamicLayout3")  
  
2.  選取控制項，並在 \[屬性\] 視窗中設定其動態配置屬性。  \[屬性\] 視窗中的 \[動態配置\] 區段包含屬性 \[移動類型\]、\[調整大小類型\]，以及定義控制項移動或大小改變多寡的特定屬性 \(取決於為那些屬性選取的值\)。  \[移動類型\] 決定變更對話方塊的大小時如何移動控制項。\[調整大小類型\] 決定變更對話方塊的大小時如何調整控制項的大小。  \[移動類型\] 和 \[調整大小類型\] 可以為 \[水平\]、\[垂直\]、\[兩者\] 或 \[無\]，視您想要以動態方式變更的維度而定。  水平是 X 維度 ；垂直是 Y 方向。  
  
3.  如果您希望常見的 \[確定\] 或 \[取消\] 按鈕等控制項大小固定且維持在右下方，則請將 \[調整大小類型\] 設為 \[無\]，並將 \[移動類型\] 設為 \[兩者\]。  針對 \[移動類型\] 下的 \[移動 X\] 和 \[移動 Y\] 值，設定 100% 來讓控制項與右下角保持固定的距離。  
  
     ![動態版面配置](../mfc/media/mfcdynamiclayout1.png "MFCDynamicLayout1")  
  
4.  假設您也有想要在對話方塊展開時加以展開的控制項。  一般而言，使用者可能會展開對話方塊，以展開多行編輯方塊，增加文字區域的大小，或者可能會展開清單控制項以查看詳細資料。  針對此案例，請將 \[調整大小類型\] 設為 \[兩者\]，並將 \[移動類型\] 設為 \[無\]。  接著，將 \[調整大小 X\] 和 \[調整大小 Y\] 值設為 100。  
  
     ![動態配置設定](../mfc/media/mfcdynamiclayout2.png "MFCDynamicLayout2")  
  
5.  實驗其他可能對您的控制項有意義的值。  例如，單行文字方塊的對話方塊可能只會將 \[調整大小類型\] 設為 \[水平\]。  
  
### 以程式設計方式設定動態配置屬性  
 上一個程序可用於在設計階段指定對話方塊的動態配置屬性，但如果您想要在執行階段控制動態配置，可以透過程式設計方式設定動態配置屬性。  
  
##### 以程式設計方式設定動態配置屬性  
  
1.  在對話方塊類別的實作程式碼中，尋找或建立一個您要為對話指定動態配置的位置。  例如，您可能會想要在對話方塊中加入 `AdjustLayout` 這樣的方法，並從需要變更配置的位置呼叫它。  您可能會先從建構函式呼叫它，或在變更對話方塊後呼叫。  
  
2.  針對對話方塊，請呼叫 [GetDynamicLayout](../Topic/CWnd::GetDynamicLayout.md)，這是 CWnd 類別的方法。  GetDynamicLayout 會將指標傳回 CMFCDynamicLayout 物件。  
  
    ```  
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();  
    ```  
  
3.  針對您要加入動態行為的第一個控制項，請在動態配置類別使用靜態方法，建立為控制項應調整方式編碼的 [MoveSettings](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md) 結構。  要這樣做，首先要選擇適當的靜態方法：[CMFCDynamicLayout::MoveHorizontal](../Topic/CMFCDynamicLayout::MoveHorizontal.md)、[CMFCDynamicLayout::MoveVertical](../Topic/CMFCDynamicLayout::MoveVertical.md)、[CMFCDynamicLayout::MoveNone](../Topic/CMFCDynamicLayout::MoveNone.md) 或 [CMFCDynamicLayout::MoveHorizontalAndVertical](../Topic/CMFCDynamicLayout::MoveHorizontalAndVertical.md)。  傳入移動之水平和\/或垂直層面的百分比。  這些靜態方法全都會傳回新建立的 MoveSettings 物件，可讓您指定控制項的移動行為。  
  
     請記住，100 表示移動的量與對話方塊變更大小的量剛好相等，這會使控制項的邊緣與新框線保持固定距離。  
  
    ```  
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);  
    ```  
  
4.  針對大小行為進行相同的動作，大小行為是使用 [SizeSettings](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md) 類型。  例如，若要指定控制項在重新調整對話方塊大小時不會變更大小，請使用下列程式碼：  
  
    ```  
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();  
    ```  
  
5.  使用 [CMFCDynamicLayout::AddItem](../Topic/CMFCDynamicLayout::AddItem.md) 方法，將控制項加入動態配置管理員。  指定想要之控制項的不同方式有兩個多載。  一個採用控制項的視窗控制代碼 \(HWND\)，另一個採用控制項 ID。  
  
    ```  
    dynamicLayout->AddItem(hWndControl, moveSettings, sizeSettings);  
    ```  
  
6.  針對每個需要移動或調整大小的控制項重複進行。  
  
7.  如果有必要，可以使用 [CMFCDynamicLayout::HasItem](../Topic/CMFCDynamicLayout::HasItem.md) 方法，判斷控制項是否已在要進行動態配置變更之控制項的清單上，或使用 [CMFCDynamicLayout::IsEmpty](../Topic/CMFCDynamicLayout::IsEmpty.md) 方法，判斷是否有任何要進行變更的控制項。  
  
8.  若要啟用對話方塊版面配置，請呼叫 [CWnd::EnableDynamicLayout](../Topic/CWnd::EnableDynamicLayout.md) 方法。  
  
    ```  
    pDialog->EnableDynamicLayout(TRUE);  
    ```  
  
9. 下次使用者重新調整對話方塊的大小時，會呼叫 [CMFCDynamicLayout::Adjust](../Topic/CMFCDynamicLayout::Adjust.md) 方法，它會實際套用設定。  
  
10. 如果您想要停用動態配置，請呼叫 [CWnd::EnableDynamicLayout](../Topic/CWnd::EnableDynamicLayout.md)，並且針對 `bEnabled` 參數使用 `FALSE`。  
  
    ```  
    pDialog->EnableDynamicLayout(FALSE);  
    ```  
  
##### 從資源檔以程式設計方式設定動態配置  
  
1.  使用 [CMFCDynamicLayout::MoveHorizontalAndVertical](../Topic/CMFCDynamicLayout::MoveHorizontalAndVertical.md) 方法指定相關資源指令碼檔案 \(.rc 檔\) 中的資源名稱，此檔案會指定動態配置資訊，如下列範例所示：  
  
    ```  
    dynamicLayout->LoadResource("IDD_DIALOG1");  
    ```  
  
     具名的資源必須參考包含配置資訊的對話方塊，其形式為資源檔中的 AFX\_DIALOG\_LAYOUT 項目，如下列範例所示：  
  
    ```  
    /////////////////////////////////////////////////////////////////////////////  
    //  
    // AFX_DIALOG_LAYOUT  
    //  
  
    IDD_MFCAPPLICATION1_DIALOG AFX_DIALOG_LAYOUT  
    BEGIN  
        0x0000, 0x6400, 0x0028, 0x643c, 0x0028  
    END  
  
    IDD_DIALOG1 AFX_DIALOG_LAYOUT  
    BEGIN  
        0x0000, 0x6464, 0x0000, 0x6464, 0x0000, 0x0000, 0x6464, 0x0000, 0x0000  
  
    END  
    ```  
  
## 請參閱  
 [CMFCDynamicLayout 類別](../mfc/reference/cmfcdynamiclayout-class.md)   
 [控制項類別](../mfc/control-classes.md)   
 [對話方塊類別](../mfc/dialog-box-classes.md)   
 [Dialog Editor](../mfc/dialog-editor.md)