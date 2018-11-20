---
title: MFC ActiveX 控制項
ms.date: 11/19/2018
f1_keywords:
- MFC ActiveX Controls (MFC)
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
ms.openlocfilehash: 10ad0645e873a1a745168be9b839bbf97a1c05a6
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52174860"
---
# <a name="mfc-activex-controls"></a>MFC ActiveX 控制項

ActiveX 控制項是可重複使用的軟體元件，以元件物件模型 (COM) 為基礎，支援各種不同的 OLE 功能並且可自訂以符合眾多軟體需求。

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需詳細資訊，請參閱 < [ActiveX 控制項](activex-controls.md)。

ActiveX 控制項的設計適用於一般的 ActiveX 控制項容器中以及在網際網路上，全球資訊網網頁中。 您可以建立 ActiveX 控制項與 MFC，此處說明，或使用[Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md)。

ActiveX 控制項可以繪製本身在它自己的視窗中，回應事件 （例如滑鼠點按），且可透過管理介面，其中包含屬性和方法類似於 Automation 物件。

監視或圖形的資料時，這些控制項可以進行許多用途，例如資料庫存取的開發。 除了其可攜性，ActiveX 控制項支援 ActiveX 控制項，例如與現有的 OLE 容器的相容性以及能夠整合其功能表與 OLE 容器功能表先前無法使用的功能。 此外，ActiveX 控制項完全支援自動化功能，這可讓控制項公開讀取 \ 寫入屬性和一組可以控制使用者所呼叫的方法。

您可以建立無視窗的 ActiveX 控制項和當它們變成作用中時，只有建立視窗的控制項。 無視窗控制項加速您的應用程式的顯示，並使它可以有透明且非矩形控制項。 您也可以以非同步方式載入 ActiveX 控制項的屬性。

ActiveX 控制項會實作為可用於任何 OLE 容器同處理序伺服器 （通常是小型物件）。 請注意，ActiveX 控制項的完整功能的設計目的是要注意的 ActiveX 控制項的 OLE 容器內使用時，才能使用。 請參閱[其他應用程式的連接埠 ActiveX 控制項](../mfc/containers-for-activex-controls.md)取得一份支援 ActiveX 控制項的容器。 這種容器類型，以下稱為 「 控制容器 」，可以使用控制項的屬性和方法，執行 ActiveX 控制項，並從事件表單中的 ActiveX 控制項接收通知。 下圖示範這種互動。

![ActiveX 控制項容器和控制項相互作用](../mfc/media/vc37221.gif "相互作用的 ActiveX 控制項容器和控制項") <br/>
ActiveX 控制項容器與視窗型 ActiveX 控制項之間的互動

最佳化您的 ActiveX 控制項的一些新資訊，請參閱[MFC ActiveX 控制項： 最佳化](../mfc/mfc-activex-controls-optimization.md)。

若要建立 MFC ActiveX 控制項，請參閱[建立 ActiveX 控制項專案](../mfc/reference/mfc-activex-control-wizard.md)。

如需詳細資訊，請參閱:

- [ActiveX 控制項容器](../mfc/activex-control-containers.md)

- [主動式文件](../mfc/active-documents.md)

- [了解 ActiveX 控制項](/windows/desktop/com/activex-controls)

- [升級要在網際網路上使用現有的 ActiveX 控制項](../mfc/upgrading-an-existing-activex-control.md)

##  <a name="_core_basic_components_of_an_activex_control"></a> ActiveX 控制項的基本元件

ActiveX 控制項會同時使用數個程式設計項目，在控制項容器與使用者有效率地互動。 這些是類別[COleControl](../mfc/reference/colecontrol-class.md)、 一組事件引發函式，以及分派對應。

您所開發的每個 ActiveX 控制項物件會繼承其 MFC 基底類別中的一組強大的功能`COleControl`。 這些功能包括在就地啟用，以及自動化邏輯。 `COleControl` 可以提供相同的功能，為 MFC 視窗物件，還能夠引發事件的控制項物件。 `COleControl` 也可以提供[無視窗控制項](../mfc/providing-windowless-activation.md)，其依賴其容器的某些功能的相關說明 視窗提供 (擷取滑鼠、 鍵盤焦點捲動)，但提供更快速的顯示。

因為控制項類別衍生自`COleControl`、 它所繼承的功能，若要傳送，或 「 觸發 」、 訊息，稱為 「 事件，以符合特定條件時的控制項容器。 這些事件用來通知控制項容器時重要的項目控制項中發生。 您可以將參數附加至事件至控制項容器的檔案，以傳送事件的其他資訊。 如需 ActiveX 控制項事件的詳細資訊，請參閱文章[MFC ActiveX 控制項： 事件](../mfc/mfc-activex-controls-events.md)。

最後一個項目是用來公開一組函式 （稱為方法） 和屬性 （稱為屬性） 來控制使用者的分派對應。 屬性可讓控制項容器或控制使用者操作控制項，以各種方式。 使用者可以變更控制項的外觀、 變更控制項的特定值或提出要求的控制項，例如存取特定的一種控制項會維護的資料。 這個介面由控制項開發人員，並使用**類別檢視**。 如需有關 ActiveX 控制項方法和屬性的詳細資訊，請參閱文章[MFC ActiveX 控制項： 方法](../mfc/mfc-activex-controls-methods.md)並[屬性](../mfc/mfc-activex-controls-properties.md)。

##  <a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a> 使用 Windows 控制項和 ActiveX 控制項容器之間的互動

控制項容器中使用控制項時，它會使用兩種機制來進行通訊： 它會公開屬性和方法，以及它就會引發事件。 下圖示範如何實作這兩種機制。

![ActiveX 控制項與其容器通訊](../mfc/media/vc37222.gif "ActiveX 控制項與其容器通訊") <br/>
ActiveX 控制項容器和 ActiveX 控制項之間的通訊

上圖也說明 （除了自動化和事件） 的其他 OLE 介面控制項的處理方式。

所有的控制項與容器之間的通訊由執行`COleControl`。 若要處理一些容器的要求，`COleControl`會呼叫成員函式，會在控制項類別中實作。 這種方式處理所有方法和一些屬性。 您的控制項類別也可以藉由呼叫成員函式的起始與容器通訊`COleControl`。 以這種方式，會引發事件。

##  <a name="_core_active_and_inactive_states_of_an_activex_control"></a> ActiveX 控制項的作用中和非作用中狀態

控制項有兩種基本的狀態： 作用中和非使用中。 傳統上，這些狀態已由控制項是否具有視窗來辨別。 作用中的控制項有視窗;非現用控制項不提供支援。 推出的無視窗啟用之後，這項區別不再是通用的但仍適用於許多控制項。

當[無視窗控制項](../mfc/providing-windowless-activation.md)會作用中，它會叫用滑鼠擷取、 鍵盤焦點、 捲動和其他視窗服務從其容器。 您也可以[提供滑鼠互動控制項非作用中](../mfc/providing-mouse-interaction-while-inactive.md)，以及建立控制項[等候，直到建立視窗啟動](../mfc/turning-off-the-activate-when-visible-option.md)。

使用中視窗的控制項時，就能夠完全互動的控制項容器、 使用者和 Windows。 下圖示範 ActiveX 控制項、 控制項容器中，與作業系統之間的通訊的路徑。

![作用中的視窗型 ActiveX 控制項中的訊息處理](../mfc/media/vc37223.gif "作用中的視窗型 ActiveX 控制項中的訊息處理") <br/>
Windows 中的訊息處理視窗型 ActiveX 控制項 （當使用中時）

##  <a name="_core_serializing_activex_elements"></a> 序列化

能夠序列化資料，有時稱為持續性，可讓您控制其屬性的值寫入永續性儲存體。 然後可以藉由從儲存體讀取物件的狀態重新建立控制項。

請注意，控制項不負責取得之儲存媒體的存取。 相反地，控制項的容器會負責在適當的時間使用的儲存媒體提供給控制項。 如需有關序列化的詳細資訊，請參閱文章[MFC ActiveX 控制項： 序列化](../mfc/mfc-activex-controls-serializing.md)。 如需序列化最佳化，請參閱[最佳化持續性和初始化](../mfc/optimizing-persistence-and-initialization.md)在 ActiveX 控制項： 最佳化。

##  <a name="_core_installing_activex_control_classes_and_tools"></a> 安裝 ActiveX 控制項類別和工具

當您安裝 Visual c + + 時，MFC ActiveX 控制項類別和零售和偵錯執行階段 Dll 會自動安裝，如果在安裝程式 （它們預設會選取） 中選取的 ActiveX 控制項的 ActiveX 控制項。

根據預設，ActiveX 控制項類別和工具會安裝下列子目錄下 \Program Files\Microsoft Visual Studio.NET 中：

- **\Common7\Tools**

   包含 （TstCon32.exe，以及它的說明檔案） 的測試容器檔案。

- **\Vc7\atlmfc\include**

   包含開發 ActiveX 控制項與 MFC 所需的 include 檔案

- **\Vc7\atlmfc\src\mfc**

   包含在 MFC 中的特定 ActiveX 控制項類別的原始程式碼

- **\Vc7\atlmfc\lib**

   包含開發 ActiveX 控制項與 MFC 所需的程式庫

另外還有範例 MFC ActiveX 控制項。 如需有關這些範例的詳細資訊，請參閱[控制項範例： MFC-Based ActiveX 控制項](../visual-cpp-samples.md)

## <a name="see-also"></a>另請參閱

[使用者介面項目](../mfc/user-interface-elements-mfc.md)
