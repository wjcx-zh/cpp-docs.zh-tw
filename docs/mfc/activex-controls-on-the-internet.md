---
title: "網際網路上的 ActiveX 控制項 | Microsoft Docs"
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
helpviewer_keywords: 
  - "ActiveX 控制項 [C++], 建立"
  - "ActiveX 控制項 [C++], 網際網路"
  - "使用 ActiveX 控制項下載資料"
  - "網際網路應用程式 [C++], ActiveX 控制項"
  - "網路 [C++], 使用 ActiveX 控制項下載"
  - "OLE 控制項 [C++], 升級至 ActiveX"
ms.assetid: 7ab943c8-2022-41df-9065-d629b616eeec
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 網際網路上的 ActiveX 控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ActiveX 控制項是 OLE automation 控制項規格的更新版本。  控制項是開發的可用於各種不同的容器的可程式化軟體元件的主要結構，包括在網際網路上 COM 明確的 Web 瀏覽器。  所有 ActiveX 控制項是網際網路位址控制項，並可將功能加入至現用文件或是網頁的一部分。  使用指令碼，網頁上的控制項才能彼此通訊。  
  
 ActiveX 控制項不限於網際網路。  只要控制項支援該容器，需要的介面 ActiveX 控制項也可以用於所有容器。  
  
 **ActiveX 控制項有幾個優點，包括:**  
  
-   最少必要介面比上一個 OLE automation 控制項。  
  
-   可以是無視窗和永遠就地啟動。  
  
 **若要為 ActiveX 控制項，控制項必須:**  
  
-   支援 **IUnknown** 介面。  
  
-   是個COM 物件。  
  
-   匯出 **DLLRegisterServer** 和 **DLLUnRegisterServer**。  
  
-   支援其他介面所需的功能。  
  
## 讓您現有的控制項很容易在網際網路上使用  
 設計在網際網路環境中正常運作的控制項在網際網路上相當低傳輸速率需要考量。  您可以使用現有的控制項；不過，您應該採用使您的程式碼大小較小且控制項的屬性下載非同步的步驟。  
  
 若要提高控制效能，請遵循效率考量這些技巧:  
  
-   實作本文所述的技術 [ActiveX 控制項:最佳化](../mfc/mfc-activex-controls-optimization.md)。  
  
-   考慮控制項如何具現化。  
  
-   為非同步作業;不要封鎖其他程式。  
  
-   下載位於小區塊中的資料。  
  
     當下載大型資料流 \(例如點陣圖或視訊資料時，請在與容器合作下存取控制資料非同步。  擷取資料加入或進度方式，以合作方式與可能也會擷取資料的其他控制項一起使用。  程式碼也可以下載非同步。  
  
-   下載程式碼和屬性在背景。  
  
-   會成為之使用者介面 \(UI\) 現用盡快。  
  
-   考慮如何儲存持續性資料，屬性和大型資料 BLOB \(例如點陣圖影像或視訊資料\)。  
  
     與數量的控制項沒有中繼資料，例如大型點陣圖或 AVI 檔名，需要下載方法的仔細考慮。  當控制項在背景中擷取資料時，資料的文件或頁面可以儘快變成可見，並允許使用者與網頁互動。  
  
-   撰寫有效率的常式保留程式碼大小和執行階段。  
  
     小按鈕和標籤控制項，只以位元組陣列持續性資料，適用於網際網路環境並適合在瀏覽器內的。  
  
-   考慮進度通訊至容器。  
  
     告知容器在非同步下載進度，包括使用者何時可以啟動與頁面互動和下載的方法。  容器可以顯示進度 \(例如完成百分比\) 給使用者。  
  
-   允許控制項在用戶端電腦上註冊。  
  
## 建立新的ActiveX 控制項  
 當建立新的控制項使用應用程式精靈時，您可以選擇啟用支援非同步標記以及其他最佳化。  若要加入支援到下載控制項屬性的步驟，請依照下列步驟執行:  
  
#### 使用 MFC ActiveX 控制項精靈以建立您的專案  
  
1.  按一下 **檔案** 功能表中的`New`。  
  
2.  從 Visual C\+\+ 專案選取 **MFC ActiveX Control Wizard** 並命名您的專案。  
  
3.  在 **Control Settings** 頁面上，選取 **Loads properties asynchronously**。  選取這個選項設定為就緒狀態屬性和就緒狀態變更事件。  
  
     您也可以選擇其他最佳化，例如在 [ActiveX 控制項:最佳化](../mfc/mfc-activex-controls-optimization.md)中說明的**Windowless activation**。  
  
4.  選擇 \[**完成**\] 以建立專案。  
  
#### 從 CDataPathProperty 建立的衍生類別  
  
1.  建立一個衍生自 `CDataPathProperty` 的類別。  
  
2.  在包含控制項的標頭檔的每一個原始程式檔，請在它的前面加入這個類別的標頭檔。  
  
3.  在這個類別，請覆寫 `OnDataAvailable`。  每當資料為顯示可供使用會呼叫這個函式。  當資料可用時，您可以進行呈現它處理它所選擇的任何方法，例如逐步轉譯他。  
  
     下列程式碼摘要是進度顯示編輯控制項的資料的簡單範例。  請注意使用旗標 **BSCF\_FIRSTDATANOTIFICATION** 清除編輯控制項。  
  
     [!code-cpp[NVC_MFCActiveXControl#1](../mfc/codesnippet/CPP/activex-controls-on-the-internet_1.cpp)]  
  
     請注意您必須包含 AFXCMN.H 以使用 `CListCtrl` 類別。  
  
4.  當控制項的整體狀態變更 \(例如，從載入到初始化的或使用者互動\)，呼叫 `COleControl::InternalSetReadyState`。  如果控制項只含有資料路徑屬性，將在 **BSCF\_LASTDATANOTIFICATION** 的程式碼告知容器您下載完成。  例如：  
  
     [!code-cpp[NVC_MFCActiveXControl#2](../mfc/codesnippet/CPP/activex-controls-on-the-internet_2.cpp)]  
  
5.  覆寫 `OnProgress`。  在 `OnProgress`中，您可透過所顯示的數字會顯示目前下載多遠的最大範圍和數字是。  您可以使用這些數字顯示狀態 \(例如完成百分比\)給使用者。  
  
 下一個程序將屬性加入至控制項使用衍生的類別。  
  
#### 若要加入屬性  
  
1.  在 \[**類別檢視**\] 中，以滑鼠右鍵按一下程式庫節點下的介面並選取 **加入**，再按一下 \[**加入屬性**\]。  這會啟動 **Add Property Wizard**。  
  
2.  在 **Add Property Wizard**，選取 **Set\/Get Methods** 選項按鈕，輸入 **Property Name**，例如， EditControlText，並選取 BSTR 做為 **Property type**。  
  
3.  按一下 \[**完成**\]。  
  
4.  宣告您的 `CDataPathProperty`成員變數，對您的 ActiveX 控制項類別的衍生類別。  
  
     [!code-cpp[NVC_MFCActiveXControl#3](../mfc/codesnippet/CPP/activex-controls-on-the-internet_3.h)]  
  
5.  實做 **Get\/Set** 方法。  對於 **Get**，傳回字串。  對於 `Set`，請載入屬性並呼叫 `SetModifiedFlag`。  
  
     [!code-cpp[NVC_MFCActiveXControl#4](../mfc/codesnippet/CPP/activex-controls-on-the-internet_4.cpp)]  
  
6.  在[DoPropExchange](../Topic/COleControl::DoPropExchange.md)中，加入下列程式碼行：  
  
     [!code-cpp[NVC_MFCActiveXControl#5](../mfc/codesnippet/CPP/activex-controls-on-the-internet_5.cpp)]  
  
7.  覆寫通知屬性的 [ResetData](../Topic/CDataPathProperty::ResetData.md) 將這行重設其控制項:  
  
     [!code-cpp[NVC_MFCActiveXControl#6](../mfc/codesnippet/CPP/activex-controls-on-the-internet_6.cpp)]  
  
## 決定是否要從 CDataPathProperty 或 CCachedDataPathProperty 衍生  
 上述範例說明衍生的控制項的屬性步驟從 `CDataPathProperty`。  如果經常變更的您下載執行階段資料，這是很好的選擇，如此一來，您不需要保留所有資料，不過，只有目前值。  範例是股票行情即時看板控制。  
  
 您也可以從 `CCachedDataPathProperty`衍生。  在這種情況下，下載的資料在記憶體檔案快取。  這是很好的選擇—例如，如果您需要保留所有呈現點陣圖的控制項的下載資料。  在這個案例中，類別有包含資料的 10% 成員變數:  
  
 `CMemFile m_Cache;`  
  
 在您的 ActiveX 控制項類別，您可以在 `OnDraw` 中使用這個記憶體對應檔中的資料。  在您的 ActiveX 控制項 `CCachedDataPathProperty`衍生類別，請覆寫成員函式 `OnDataAvailable` 並在呼叫基底類別實作之後無法使用控制項。  
  
 [!code-cpp[NVC_MFCActiveXControl#7](../mfc/codesnippet/CPP/activex-controls-on-the-internet_7.cpp)]  
  
## 非同步下載資料的 ActiveX 控制項  
 應該在網路上以非同步方式下載資料。  這麼做的好處是如果轉換大量資料或是連接緩慢，下載程序也不會封鎖在用戶端的其他處理序。  
  
 非同步標記提供一種方法以非同步方式在網路下載資料。  即使作業尚未完成，在非同步 Moniker 的讀取作業會立即傳回。  
  
 例如，如果只有 10 位元組可用以及讀取 1K 檔案非同步呼叫，則將不會封鎖讀取，但只會傳回目前可用的 10 個位元組。  
  
 使用 `CAsyncMonikerFile` 類別以實作 [非同步標記](../mfc/asynchronous-monikers-on-the-internet.md) 。  不過， ActiveX 控制項可以使用 `CDataPathProperty` 類別，衍生自 `CAsyncMonikerFile`，以說明實作非同步控制項屬性。  
  
 ASYNDOWN 範例示範如何設定非同步重複使用計時器讀取資料。   可從 Microsoft 下載中心下載在知識庫文件「HOWTO 詳細說明:AsyncDown 示範非同步資料下載」\(Q177244\) 中說明的ASYNDOWN 。\(如需下載的更多資訊從 Microsoft 下載中心下載檔案，查看在Microsoft 知識庫的這篇文章 \< 如何取得從 Microsoft 線上服務的支援檔案 \> \(Q119591\) \)。您可以在 MSDN Library CD\-ROM 或是在 [http:\/\/support.microsoft.com\/support](http://support.microsoft.com/support) 找到知識庫文件。  
  
 在ASYNDOWN 用來在 **CDataPathProperty::OnDataAvailable** 設定計時器的基本技術是指示當資料可供使用的時候。  當計時器收到訊息時，應用程式會寫入資料 128 位元組區塊並填入編輯控制項。  當計時器訊息被處理時，如果資料無法使用，計時器就會關閉。  如果詳細資料延遲到，則`OnDataAvailable` 會啟動計時器。  
  
## 顯示在 Web 網頁上的控制項。  
 這個物件標記和屬性的範例插入的 Web 網頁上的控制項。  
  
 `<OBJECT`  
  
 `CLASSID="clsid:FC25B780-75BE-11CF-8B01-444553540000"`  
  
 `CODEBASE="/ie/download/activex/iechart.ocx"`  
  
 `ID=chart1`  
  
 `WIDTH=400`  
  
 `HEIGHT=200`  
  
 `ALIGN=center`  
  
 `HSPACE=0`  
  
 `VSPACE=0`  
  
 `>`  
  
 `<PARAM NAME="BackColor" value="#ffffff">`  
  
 `<PARAM NAME="ForeColor" value="#0000ff">`  
  
 `<PARAM NAME="url" VALUE="/ie/controls/chart/mychart.txt">`  
  
 `</OBJECT>`  
  
## 更新現有的 OLE automation 控制項使用新的 ActiveX 控制項的功能。  
 如果您的 OLE automation 控制項以 Visual C\+\+ 4.2 之前的版本所建立的，這些是您可採取以可改善其效能並提高其功能的步驟。  如需這些功能的深入的討論變更，請參閱 [ActiveX 控制項:最佳化](../mfc/mfc-activex-controls-optimization.md)。  
  
 如果您將非同步屬性支援加入至現有的控制項，您將需要加入就緒狀態屬性和 `ReadyStateChange` 事件。  在控制項的建構函式，請加入:  
  
 [!code-cpp[NVC_MFCActiveXControl#8](../mfc/codesnippet/CPP/activex-controls-on-the-internet_8.cpp)]  
  
 您將更新就緒狀態，您的程式碼會藉由呼叫 [COleControl::InternalSetReadyState](../Topic/COleControl::InternalSetReadyState.md)下載。  您可以呼叫 `InternalSetReadyState` 的位置是從 `CDataPathProperty``OnProgress` 覆寫衍生類別。  
  
 然後，請遵循 [建立新的 ActiveX 控制項](#_core_how_do_i_create_a_new_activex_control.3f)中的步驟。  
  
## 請參閱  
 [MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)   
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)