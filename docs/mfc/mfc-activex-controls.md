---
title: "MFC ActiveX 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MFC ActiveX Controls (MFC)"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項 [C++], MFC"
  - "COleControl 類別, MFC ActiveX 控制項"
  - "容器 [C++], MFC ActiveX 控制項"
  - "分派對應, MFC ActiveX 控制項的"
  - "事件 [C++], ActiveX 控制項"
  - "MFC ActiveX 控制項 [C++]"
  - "MFC ActiveX 控制項 [C++], 現用/非現用狀態"
  - "MFC ActiveX 控制項 [C++], 容器"
  - "MFC ActiveX 控制項 [C++], 序列化"
  - "序列化 [C++], MFC ActiveX 控制項"
ms.assetid: c911fb74-3afc-4bf3-a0f5-7922b14d9a1b
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ActiveX 控制項是以元件物件模型 \(Component Object Model，COM\) 為基礎的重複使用軟體元件，可支援各種不同的 OLE 功能，也能夠自訂來符合許多軟體需求。  ActiveX 控制項是設計來用於一般 ActiveX 控制項容器以及網際網路上的全球資訊網 \(World Wide Web\) 網頁中。  您可以用在此描述的 MFC，或 [Active Template Library \(ATL\)](../atl/active-template-library-atl-concepts.md)建立 ActiveX 控制項。  
  
 ActiveX 控制項可以在其視窗繪製自己，回應事件 \(例如按一下滑鼠\) 和透過 Automation 物件包含屬性和類似方法的介面來管理。  
  
 這些控制項可以開發給許多用處，例如資料庫存取，資料監視或繪圖。  除了其可攜性以外， ActiveX 控制項支援先前對 ActiveX 控制項無效的功能，例如與現有的 OLE 容器的相容性以及將其功能表與 OLE 容器功能表整合的能力。  此外， ActiveX 控制項完全支援 Automation，允許控制項公開讀取\\寫入屬性和一組可以由控制項呼叫使用者的方法。  
  
 您可以在他們啟動時建立無視窗 ActiveX 控制項和只建立視窗的控制項。  無視窗控制項加速應用程式顯示並可以讓其具有透明和非矩形控制項。  您也可以非同步地裝載 ActiveX 控制項屬性。  
  
 ActiveX 控制項實作為可用於所有 OLE 容器的同處理序伺服程式 \(通常是小型物件\)。  請注意只有在使用所設計的 OLE 容器內知道 ActiveX 控制項時， ActiveX 控制項的完整功能才可供使用。  請參閱 [將 ActiveX 控制項至其他應用程式](../mfc/containers-for-activex-controls.md) 為支援 ActiveX 控制項容器的清單。  這個容器型別，此後稱為「容器控制項」，可以使用控制項的屬性和方法操作 ActiveX 控制項，並從 ActiveX 控制項以事件的形式接收通知。  下列圖示顯示這個交互作用。  
  
 ![ActiveX 控制項容器和控制項相互作用](../mfc/media/vc37221.png "vc37221")  
ActiveX 控制項容器和視窗型 ActiveX 控制項之間的互動  
  
 如需最佳化 ActiveX 控制項的一些最新資訊，請參閱 [MFC ActiveX 控制項:最佳化](../mfc/mfc-activex-controls-optimization.md)。  
  
 若要建立 MFC ActiveX 控制項，請參閱 [建立 ActiveX 控制項專案](../mfc/reference/mfc-activex-control-wizard.md)。  
  
 如需詳細資訊，請參閱：  
  
-   [ActiveX 控制項容器](../mfc/activex-control-containers.md)  
  
-   [主動式文件](../mfc/active-documents.md)  
  
-   [使用 ActiveX 控制項](../data/ado-rdo/using-activex-controls.md)  
  
-   [\<caps:sentence id\="tgt23" sentenceid\="e07c7a1ebdac21120a91f75018670c81" class\="tgtSentence"\>了解 ActiveX 控制項\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms693753)  
  
-   [升級現有的網際網路使用 ActiveX 控制項](../mfc/upgrading-an-existing-activex-control.md)  
  
##  <a name="_core_basic_components_of_an_activex_control"></a> ActiveX 控制項的基本元件  
 ActiveX 控制項使用幾個程式設計項目有效地與控制項容器和使用者互動。  這些是 [COleControl](../mfc/reference/colecontrol-class.md)類別，一組事件引發函式和分派對應。  
  
 您正在開發的每一個 ActiveX 控制項物件從 MFC 基底類別 `COleControl`繼承強大的功能集。  這些功能包括就地啟動和 Automation 邏輯。  `COleControl` 可提供控制物件與 MFC Windows 物件相同的功能，再加上能夠引發事件的能力。  `COleControl` 也可以提供 [無視窗控制項](../mfc/providing-windowless-activation.md)，取決於其說明的容器與某些功能視窗提供 \(滑鼠捕捉，鍵盤焦點，移動\)，不過提供更快的顯示。  
  
 由於控制項類別衍生自 `COleControl`，它會繼承功能傳送或「發射」訊息，呼叫事件，在符合特定條件時加入至容器控制項。  當控制項中發生重要的事時，這些事件被用來通知控制項容器。  您可以藉由將參數加入至事件傳送有關事件的其他資訊至控制項容器。  如需 ActiveX 控制項事件的詳細資訊，請參閱本文件的 [MFC ActiveX 控制項:事件](../mfc/mfc-activex-controls-events.md)。  
  
 最後一個項目是分派對應，用來公開一組函式 \(呼叫方法\) 和屬性 \(稱為特性\) 至使用者控制項。  屬性允許控制項容器或控制項使用者管理以各種方式操縱控制項。  使用者可以變更控制項的外觀，變更控制項的某些值或提出要求控制項，例如存取控制維護資料的特定項目。  這個介面由控制項開發人員決定並使用 \[**類別檢視**\]定義。  如需 ActiveX 控制項的方法和屬性的詳細資訊，請參閱文件 [MFC ActiveX 控制項:方法](../mfc/mfc-activex-controls-methods.md) 和 [屬性](../mfc/mfc-activex-controls-properties.md)。  
  
##  <a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a> 視窗控制項和 ActiveX 控制項容器之間的互動  
 當控制在控制項容器內部使用時，它會使用兩個機制通訊:它會公開屬性和方法，然後引發事件。  下圖示範這兩種機制如何實作。  
  
 ![ActiveX 控制項與其容器通訊](../mfc/media/vc37222.png "vc37222")  
ActiveX 控制項容器和 ActiveX 控制項之間的通訊。  
  
 先前的圖也會說明其他 OLE 介面 \(除了自動化和事件以外\) 如何由控制項處理。  
  
 所有與容器控制項的通訊由 `COleControl`實作。  若要處理某些容器的要求， **COleControl** 會呼叫控制項類別實作的成員函式。  所有方法和某些屬性以這種方式處理。  控制項的類別可以透過呼叫 `COleControl`的成員函式來初始與容器的通訊。  事件會引發。  
  
##  <a name="_core_active_and_inactive_states_of_an_activex_control"></a> ActiveX 控制項的現用及非現用狀態。  
 控制項有兩種基本的狀態:現用及非現用。  傳統上，這些狀態分別由是否具有視窗的控制項區別。  現用控制項具有視窗;非現用控制項沒有。  無視窗啟動的簡介，這分別不再是通用的，不過仍適用於許多控制項。  
  
 當 [無視窗控制項](../mfc/providing-windowless-activation.md) 移至作用中時，它會從它的容器叫用滑鼠捕捉、鍵盤焦點、捲動和其他 Windows 服務。  您也可以 [提供滑鼠互動給非現用控制項](../mfc/providing-mouse-interaction-while-inactive.md)，以及 [等待直到啟動建立視窗](../mfc/turning-off-the-activate-when-visible-option.md)中建立控制項。  
  
 當有視窗的控制項變為作用中時，可以使用控制項容器、使用者和視窗完全互動。  下圖示範 ActiveX 控制項、控制項容器和作業系統之間的通訊路徑。  
  
 ![視窗化之 ActiveX 控制項中的訊息處理流程](../mfc/media/vc37223.png "vc37223")  
處理視窗型 ActiveX 控制項的視窗訊息 \(當作用中\)  
  
##  <a name="_core_serializing_activex_elements"></a> 序列化  
 還原序列化能力的資料，有時稱為持續性，允許控制項給持續性儲存體寫入其屬性的值。  控制項可以讀取從儲存區物件狀態然後重新建立。  
  
 請注意控制項不負責取得存放媒體的存取。  相反地，控制項的容器負責提供對控制項存放媒體使用在適當的時間。  如需序列化的詳細資訊，請參閱本文件的 [MFC ActiveX 控制項:序列化](../mfc/mfc-activex-controls-serializing.md)。  如需最佳化序列化的詳細資訊，請參閱在 ActiveX 控制項的 [最佳化持續性和初始化](../mfc/optimizing-persistence-and-initialization.md) :最佳化。  
  
##  <a name="_core_installing_activex_control_classes_and_tools"></a> 安裝 ActiveX 控制項類別和工具  
 當您安裝 Visual C\+\+ 時， 如果 ActiveX 控制項設定預設 \(它們被選取選取\)，MFC ActiveX 控制項類別和零售和偵錯執行階段 DLL 將被自動安裝。  
  
 根據預設， ActiveX 控制項類別和工具安裝在下列子目錄\\ Program Files \\ Microsoft Visual Studio .NET:  
  
-   **\\ Common7 \\ Tools**  
  
     包含測試容器檔案 \(TstCon32.exe，以及其說明檔\)。  
  
-   **\\ Vc7 \\ atlmfc \\ include**  
  
     包含需要以 MFC 開發的 ActiveX 控制項  
  
-   **\\ Vc7 \\ atlmfc \\ src \\ mfc**  
  
     包含在 MFC 中特定的 ActiveX 控制項類別的原始程式碼  
  
-   **\\ Vc7 \\ atlmfc \\ lib**  
  
     包含要求以 MFC 開發 ActiveX 控制項的程式庫  
  
 也有 MFC ActiveX 控制項的範例。  如需這些範例的詳細資訊，請參閱 [控制項範例:MFC 架構的 ActiveX 控制項](../top/visual-cpp-samples.md)  
  
## 請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)