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
ms.openlocfilehash: a1c7bb070a75f4406556817163931f0707706c40
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508118"
---
# <a name="mfc-activex-controls"></a>MFC ActiveX 控制項

ActiveX 控制項是可重複使用的軟體元件，以元件物件模型 (COM) 為基礎，支援各種不同的 OLE 功能並且可自訂以符合眾多軟體需求。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需詳細資訊, 請參閱[ActiveX 控制項](activex-controls.md)。

ActiveX 控制項的設計目的是要在一般 ActiveX 控制項容器以及網際網路上的全球網頁中使用。 您可以使用 MFC (如這裡所述) 或使用[Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md)來建立 ActiveX 控制項。

ActiveX 控制項可以在自己的視窗中自行繪製、回應事件 (例如按一下滑鼠), 並透過包含類似 Automation 物件中之屬性和方法的介面來管理。

這些控制項可以針對許多用途而開發, 例如資料庫存取、資料監視或圖形。 除了其可攜性以外, ActiveX 控制項還支援 ActiveX 控制項先前無法使用的功能, 例如與現有 OLE 容器的相容性, 以及將其功能表與 OLE 容器功能表整合的能力。 此外, ActiveX 控制項完全支援 Automation, 讓控制項能夠公開讀取 \ 寫入的屬性, 以及可由控制項使用者呼叫的一組方法。

您可以建立無視窗的 ActiveX 控制項和控制項, 只有在視窗變成作用中時才會建立。 無視窗控制項可加速應用程式的顯示, 讓您可以擁有透明和非矩形控制項。 您也可以以非同步方式載入 ActiveX 控制項屬性。

ActiveX 控制項會實作為同進程伺服器 (通常是小型物件), 可在任何 OLE 容器中使用。 請注意, 只有在設計用來感知 ActiveX 控制項的 OLE 容器中使用時, 才能使用 ActiveX 控制項的完整功能。 如需支援 ActiveX 控制項的容器清單, 請參閱[將 Activex 控制項移植到其他應用程式](../mfc/containers-for-activex-controls.md)。 這個容器類型 (之後稱為「控制項容器」) 可以使用控制項的屬性和方法來操作 ActiveX 控制項, 並以事件的形式接收來自 ActiveX 控制項的通知。 下圖將示範這項互動。

![ActiveX 控制項容器和控制項的相互作用](../mfc/media/vc37221.gif "ActiveX 控制項容器和控制項的相互作用") <br/>
ActiveX 控制項容器與視窗型 ActiveX 控制項之間的互動

如需優化 ActiveX 控制項的一些最新資訊, [請參閱 MFC ActiveX 控制項:優化](../mfc/mfc-activex-controls-optimization.md)。

若要建立 MFC ActiveX 控制項, 請參閱[建立 activex 控制項專案](../mfc/reference/mfc-activex-control-wizard.md)。

如需詳細資訊，請參閱：

- [ActiveX 控制項容器](../mfc/activex-control-containers.md)

- [主動式文件](../mfc/active-documents.md)

- [瞭解 ActiveX 控制項](/windows/win32/com/activex-controls)

- [升級要在網際網路上使用的現有 ActiveX 控制項](../mfc/upgrading-an-existing-activex-control.md)

##  <a name="_core_basic_components_of_an_activex_control"></a>ActiveX 控制項的基本元件

ActiveX 控制項使用數種程式設計項目, 與控制項容器和使用者有效率地互動。 這些是類別[COleControl](../mfc/reference/colecontrol-class.md)、一組事件引發函數和一個分派對應。

您所開發的每個 ActiveX 控制項物件都會從其 MFC 基類`COleControl`繼承一組強大的功能。 這些功能包括就地啟用和自動化邏輯。 `COleControl`可以提供控制項物件與 MFC 視窗物件相同的功能, 以及引發事件的能力。 `COleControl`也可以提供[無視窗的控制項](../mfc/providing-windowless-activation.md), 其依賴其容器來協助處理視窗提供的某些功能 (滑鼠捕捉、鍵盤焦點、滾動), 但提供更快速的顯示。

因為控制項類別是衍生自`COleControl`, 所以它會在符合特定條件時, 繼承功能以傳送或「引發」訊息 (稱為事件) 給控制項容器。 這些事件是用來在控制項中發生重要的問題時, 通知控制項容器。 您可以藉由將參數附加至事件, 將事件的其他相關資訊傳送至控制項容器。 如需 ActiveX 控制項事件的詳細資訊, 請參閱[MFC activex 控制項:事件](../mfc/mfc-activex-controls-events.md)。

最後一個元素是一個分派對應, 用來向控制項使用者公開一組函式 (稱為「方法」) 和屬性 (稱為「屬性」 (property))。 屬性可讓控制項容器或控制項使用者以各種方式操作控制項。 使用者可以變更控制項的外觀、變更控制項的特定值, 或提出控制項的要求, 例如存取控制項維護的特定資料片段。 這個介面是由控制項開發人員決定, 而且是使用**類別檢視**所定義。 如需 ActiveX 控制項方法和屬性的詳細資訊, 請參閱[MFC ActiveX 控制項:方法](../mfc/mfc-activex-controls-methods.md)和[屬性](../mfc/mfc-activex-controls-properties.md)。

##  <a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a>使用 Windows 和 ActiveX 控制項容器的控制項之間的互動

控制項容器中使用控制項時, 會使用兩種機制來進行通訊: 它會公開屬性和方法, 並引發事件。 下圖將示範如何實作為這兩種機制。

![ActiveX 控制項與其容器通訊](../mfc/media/vc37222.gif "ActiveX 控制項與其容器通訊") <br/>
ActiveX 控制項容器和 ActiveX 控制項之間的通訊

上圖也說明其他 OLE 介面 (除了自動化和事件以外) 如何由控制項處理。

所有與容器的控制項通訊都是由`COleControl`所執行。 若要處理容器的某些要求, `COleControl`將會呼叫在控制項類別中實作用的成員函式。 所有方法和部分屬性都會以這種方式處理。 控制項的類別也可以藉由呼叫的成員`COleControl`函式, 起始與容器的通訊。 事件會以這種方式引發。

##  <a name="_core_active_and_inactive_states_of_an_activex_control"></a>ActiveX 控制項的現用和非作用中狀態

控制項有兩個基本狀態: [作用中] 和 [非作用中]。 傳統上, 這些狀態是由控制項是否有視窗來區分。 現用控制項有一個視窗;非作用中的控制項不是。 隨著無視窗啟用的推出, 這項區別已不再通用, 但仍適用于許多控制項。

當[無視窗控制項](../mfc/providing-windowless-activation.md)變成作用中時, 它會從其容器叫用滑鼠捕捉、鍵盤焦點、滾動和其他視窗服務。 您也可以[將滑鼠互動提供給非](../mfc/providing-mouse-interaction-while-inactive.md)作用中的控制項, 並建立控制項來[等候啟動以建立視窗](../mfc/turning-off-the-activate-when-visible-option.md)。

當具有視窗的控制項變成作用中狀態時, 它就能夠完全與控制項容器、使用者和視窗互動。 下圖說明 ActiveX 控制項、控制項容器和作業系統之間通訊的路徑。

![Active 視窗型 ActiveX 控制項中的訊息處理](../mfc/media/vc37223.gif "Active 視窗型 ActiveX 控制項中的訊息處理") <br/>
視窗型 ActiveX 控制項中的 Windows 訊息處理 (作用時)

##  <a name="_core_serializing_activex_elements"></a>串列

序列化資料 (有時稱為持續性) 的功能可讓控制項將其屬性的值寫入持續性儲存體。 接著, 您可以從儲存體讀取物件的狀態, 以重新建立控制項。

請注意, 控制項不負責取得儲存媒體的存取權。 相反地, 控制項的容器會負責提供具有儲存媒體的控制項, 以便在適當的時間使用。 如需序列化的詳細資訊, 請參閱[MFC ActiveX 控制項:序列化](../mfc/mfc-activex-controls-serializing.md)。 如需優化序列化的詳細資訊, 請參閱在 ActiveX 控制項中[優化持續性和初始化](../mfc/optimizing-persistence-and-initialization.md):優化.

##  <a name="_core_installing_activex_control_classes_and_tools"></a>安裝 ActiveX 控制項類別和工具

當您安裝 Visual C++時, 如果在安裝程式中選取了 activex 控制項, 則會自動安裝 MFC ActiveX 控制項類別和零售和 debug activex 控制項執行時間 dll (預設會選取)。

根據預設, ActiveX 控制項類別和工具會安裝在 \Program Files\Microsoft Visual Studio .NET 下的下列子目錄:

- **\Common7\Tools**

   包含測試容器檔案 (TstCon32 和其說明檔)。

- **\Vc7\atlmfc\include**

   包含使用 MFC 開發 ActiveX 控制項所需的 include 檔案

- **\Vc7\atlmfc\src\mfc**

   包含 MFC 中特定 ActiveX 控制項類別的原始程式碼

- **\Vc7\atlmfc\lib**

   包含使用 MFC 開發 ActiveX 控制項所需的程式庫

MFC ActiveX 控制項也有範例。 如需這些範例的詳細資訊, [請參閱控制項範例:以 MFC 為基礎的 ActiveX 控制項](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>另請參閱

[使用者介面元素](../mfc/user-interface-elements-mfc.md)
