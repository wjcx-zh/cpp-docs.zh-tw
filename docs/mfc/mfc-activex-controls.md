---
title: MFC ActiveX 控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MFC ActiveX Controls (MFC)
dev_langs:
- C++
helpviewer_keywords:
- COleControl class [MFC], MFC ActiveX controls
- ActiveX controls [MFC], MFC
- containers [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], serializing
- MFC ActiveX controls [MFC], containers
- serialization [MFC], MFC ActiveX controls
- dispatch maps [MFC], for MFC ActiveX controls
- MFC ActiveX controls [MFC], active/inactive state
- events [MFC], ActiveX controls
- MFC ActiveX controls [MFC]
ms.assetid: c911fb74-3afc-4bf3-a0f5-7922b14d9a1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1209353f10e52b13202a91ae120057ba85dfa805
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930093"
---
# <a name="mfc-activex-controls"></a>MFC ActiveX 控制項
ActiveX 控制項是可重複使用的軟體元件，以元件物件模型 (COM) 為基礎，支援各種不同的 OLE 功能並且可自訂以符合眾多軟體需求。 ActiveX 控制項的設計並適用於一般的 ActiveX 控制項容器中以及在網際網路上，在 全球資訊網網頁中。 您可以建立 ActiveX 控制項與 MFC，描述在這裡，或使用[Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md)。  
  
 ActiveX 控制項可以繪製本身在它自己的視窗中，回應事件 （例如按一下滑鼠），且會透過管理介面，其中包含屬性和方法類似於 Automation 物件。  
  
 監視或繪製的資料時，這些控制項可以進行許多用途，例如資料庫存取的開發。 除了其可攜性，ActiveX 控制項支援功能先前未提供給 ActiveX 控制項，例如與現有的 OLE 容器的相容性和整合其功能表與 OLE 容器功能表的能力。 此外，ActiveX 控制項完全支援自動化功能，可讓您控制公開可讀取 \ 寫入內容和一組控制使用者可以呼叫的方法。  
  
 您可以建立無視窗的 ActiveX 控制項和控制項，當它們變成作用中時，只能建立一個視窗。 無視窗控制項加速您的應用程式的顯示，並且讓它可以有透明及非矩形控制項。 您也可以非同步載入 ActiveX 控制項的屬性。  
  
 ActiveX 控制項被實作可用於任何 OLE 容器同處理序伺服器 （通常是小型的物件）。 請注意，ActiveX 控制項的完整功能的設計目的在能夠感知的 ActiveX 控制項的 OLE 容器內使用時，才能使用。 請參閱[其他應用程式的連接埠 ActiveX 控制項](../mfc/containers-for-activex-controls.md)支援 ActiveX 控制項容器的清單。 此容器類型，以下稱為 「 控制項容器 」，可以使用控制項的屬性和方法，來操作的 ActiveX 控制項，並從事件表單中的 ActiveX 控制項接收通知。 下圖示範這種互動。  
  
 ![ActiveX 控制項容器和控制項相互作用](../mfc/media/vc37221.gif "vc37221")  
ActiveX 控制項容器與視窗型的 ActiveX 控制項之間的互動  
  
 某些最佳化您的 ActiveX 控制項的新資訊，請參閱[MFC ActiveX 控制項： 最佳化](../mfc/mfc-activex-controls-optimization.md)。  
  
 若要建立 MFC ActiveX 控制項，請參閱[建立 ActiveX 控制項專案](../mfc/reference/mfc-activex-control-wizard.md)。  
  
 如需詳細資訊，請參閱:  
  
-   [ActiveX 控制項容器](../mfc/activex-control-containers.md)  
  
-   [主動式文件](../mfc/active-documents.md)  
  
-   [了解 ActiveX 控制項](http://msdn.microsoft.com/library/windows/desktop/ms693753)  
  
-   [升級要在網際網路上使用現有的 ActiveX 控制項](../mfc/upgrading-an-existing-activex-control.md)  
  
##  <a name="_core_basic_components_of_an_activex_control"></a> ActiveX 控制項的基本元件  
 ActiveX 控制項與控制項容器和與使用者有效率地互動用於數種程式設計項目。 這些是類別[COleControl](../mfc/reference/colecontrol-class.md)、 一組事件引發函式，以及分派對應。  
  
 您所開發的每個 ActiveX 控制項物件會繼承其 MFC 基底類別，一組功能強大的功能`COleControl`。 這些功能包括就地啟用和自動化邏輯。 `COleControl` MFC 視窗物件，再加上引發事件的能力與相同的功能可以提供控制項物件。 `COleControl` 也可以提供[無視窗控制項](../mfc/providing-windowless-activation.md)，其依賴其容器的某些功能的相關說明 視窗會提供 (滑鼠擷取、 鍵盤焦點、 捲動)，但提供更快的顯示。  
  
 因為控制項類別衍生自`COleControl`、 它所繼承的功能，傳送，或 「 引發 」，訊息，稱為 「 事件，當符合特定條件的控制項容器。 這些事件用來通知控制項容器時重要事項控制項中發生。 您可以傳送至控制項容器事件的詳細資訊，將參數附加至事件。 如需 ActiveX 控制項事件的詳細資訊，請參閱文章[MFC ActiveX 控制項： 事件](../mfc/mfc-activex-controls-events.md)。  
  
 最後一個元素是分派對應，用來公開一組函式 （稱為方法） 和屬性 （稱為屬性），以控制使用者。 屬性可讓控制項容器或控制使用者操作控制項以各種方式。 使用者可以變更控制項的外觀、 變更控制項的特定值或提出要求的控制項，例如存取特定控制項所維護的資料。 這個介面由控制項開發人員，並使用定義**類別檢視**。 如需 ActiveX 控制項方法和屬性的詳細資訊，請參閱文章[MFC ActiveX 控制項： 方法](../mfc/mfc-activex-controls-methods.md)和[屬性](../mfc/mfc-activex-controls-properties.md)。  
  
##  <a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a> Windows 使用的控制項和 ActiveX 控制項容器之間的互動  
 當控制項容器中使用控制項時，它會使用兩種機制來通訊： 它會公開屬性和方法，並引發事件。 下圖示範如何實作這兩種機制。  
  
 ![ActiveX 控制項與其容器通訊](../mfc/media/vc37222.gif "vc37222")  
ActiveX 控制項容器和 ActiveX 控制項之間的通訊  
  
 上圖中也會說明如何處理 （除了自動化和事件） 的其他 OLE 介面的控制項。  
  
 所有與容器控制項的通訊由執行`COleControl`。 若要處理一些容器的要求`COleControl`會呼叫控制項類別中實作的函式成員。 所有方法和某些屬性會在這種方式處理。 控制項的類別也可以藉由呼叫成員函式的起始與容器通訊`COleControl`。 以這種方式，會引發事件。  
  
##  <a name="_core_active_and_inactive_states_of_an_activex_control"></a> ActiveX 控制項的作用中和非使用中狀態  
 控制項有兩種基本狀態： 作用中和非使用中。 傳統上，這些狀態已由控制項是否具有視窗辨別。 作用中的控制項具有視窗;非現用控制項不提供支援。 無視窗啟用引入，這樣的區別不再通用的但仍適用於許多控制項。  
  
 當[無視窗控制項](../mfc/providing-windowless-activation.md)到作用中時，它會叫用滑鼠擷取、 鍵盤焦點、 捲動、 和其容器從其他視窗服務。 您也可以[提供非作用中控制項的滑鼠互動](../mfc/providing-mouse-interaction-while-inactive.md)，以及建立控制項[等到建立視窗啟動](../mfc/turning-off-the-activate-when-visible-option.md)。  
  
 當控制項與視窗變成作用中時，就可以進行完整互動控制項容器、 使用者和 Windows。 下圖示範 ActiveX 控制項，控制項容器中，與作業系統之間的通訊路徑。  
  
 ![使用中視窗的 ActiveX 控制項中的訊息處理](../mfc/media/vc37223.gif "vc37223")  
視窗型的 ActiveX 控制項 （使用時） 中處理 Windows 訊息  
  
##  <a name="_core_serializing_activex_elements"></a> 序列化  
 能夠序列化資料，有時也稱為持續性，讓控制項永續性儲存體寫入其屬性的值。 然後可以藉由從儲存體讀取物件的狀態重新建立控制項。  
  
 請注意控制項不是負責取得存取權之儲存媒體。 相反地，控制項的容器會負責提供控制項在適當的時間使用的儲存媒體。 如需序列化的詳細資訊，請參閱文章[MFC ActiveX 控制項： 序列化](../mfc/mfc-activex-controls-serializing.md)。 如需最佳化序列化資訊，請參閱[最佳化持續性和初始化](../mfc/optimizing-persistence-and-initialization.md)在 ActiveX 控制項： 最佳化。  
  
##  <a name="_core_installing_activex_control_classes_and_tools"></a> 安裝 ActiveX 控制項類別和工具  
 當您安裝 Visual c + + 時，MFC ActiveX 控制項類別和零售和偵錯執行階段 Dll 會自動安裝，如果安裝程式 （它們預設會選取） 中所選取的 ActiveX 控制項的 ActiveX 控制項。  
  
 根據預設，ActiveX 控制項類別和工具會安裝下列 \Program Files\Microsoft Visual Studio.NET 下子目錄中：  
  
-   **\Common7\Tools**  
  
     包含 （TstCon32.exe，以及其說明檔案） 的測試容器檔案。  
  
-   **\Vc7\atlmfc\include**  
  
     包含開發 ActiveX 控制項與 MFC 所需的 include 檔  
  
-   **\Vc7\atlmfc\src\mfc**  
  
     包含在 MFC 中的特定 ActiveX 控制項類別的原始程式碼  
  
-   **\Vc7\atlmfc\lib**  
  
     包含開發 ActiveX 控制項與 MFC 所需的程式庫  
  
 另外還有適用於 MFC ActiveX 控制項範例。 如需有關這些範例的詳細資訊，請參閱[控制項範例： MFC-Based ActiveX 控制項](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)
