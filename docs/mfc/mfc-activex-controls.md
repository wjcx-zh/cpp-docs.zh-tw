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
ms.openlocfilehash: e9cc38eebed0b1f8e0932e89ef1452261aefd7dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365446"
---
# <a name="mfc-activex-controls"></a>MFC ActiveX 控制項

ActiveX 控制項是可重複使用的軟體元件，以元件物件模型 (COM) 為基礎，支援各種不同的 OLE 功能並且可自訂以符合眾多軟體需求。

>[!IMPORTANT]
> ActiveX 是一種不應用於新開發的傳統技術。 有關詳細資訊,請參閱[ActiveX 控制件](activex-controls.md)。

ActiveX 控制件設計用於普通 ActiveX 控制容器和 Internet、萬維網頁面。 您可以使用此處描述的 MFC 或[使用活動範本庫 (ATL)](../atl/active-template-library-atl-concepts.md)創建 ActiveX 控制件。

ActiveX 控制件可以在自己的視窗中繪製自身,回應事件(如滑鼠單擊),並透過包含類似於自動化物件的屬性和方法的介面進行管理。

這些控制項可以開發用於多種用途,例如資料庫存取、資料監視或圖形繪製。 除了可移植性外,ActiveX 控制支援以前對 ActiveX 控制件不可用的功能,例如與現有 OLE 容器的相容性以及將其功能表與 OLE 容器功能表整合的能力。 此外,ActiveX 控制項完全支援自動化,它允許控制項公開讀取\write 屬性和一組控制項用戶可以調用的方法。

您可以創建無視窗的 ActiveX 控制件和控制項,這些控制項和控制項僅在視窗變為活動時創建視窗。 無視窗控制項可加快應用程式的顯示速度,並可以具有透明和非矩形控制元件。 您還可以非同步載入 ActiveX 控制件屬性。

ActiveX 控制項作為可在任何 OLE 容器中使用的進程內伺服器(通常是小物件)實現。 請注意,ActiveX 控制件的全部功能僅在旨在瞭解 ActiveX 控件的 OLE 容器中使用時才可用。 有關支援 ActiveX 控制檔的容器清單,請參閱[將 ActiveX 控制套件到其他應用程式](../mfc/containers-for-activex-controls.md)。 此容器類型(以下簡稱"控制容器")可以使用控制項的屬性和方法操作 ActiveX 控制項,並接收來自 ActiveX 控制項的通知(事件形式)。 下圖演示了此交互。

![ActiveX 控制項容器和控制項相互作用](../mfc/media/vc37221.gif "ActiveX 控制項容器和控制項相互作用") <br/>
ActiveX 控制容器與窗動 X 控制元件之間的互動

有關優化 ActiveX 控制件的一些最新資訊,請參閱[MFC ActiveX 控制項:優化](../mfc/mfc-activex-controls-optimization.md)。

要建立 MFC ActiveX 控制件,請參閱[建立 ActiveX 控制件專案](../mfc/reference/mfc-activex-control-wizard.md)。

如需詳細資訊，請參閱

- [ActiveX 控制項容器](../mfc/activex-control-containers.md)

- [主動式文件](../mfc/active-documents.md)

- [瞭解 ActiveX 控制項](/windows/win32/com/activex-controls)

- [升級要在網際網路上使用的現有 ActiveX 控制項](../mfc/upgrading-an-existing-activex-control.md)

## <a name="basic-components-of-an-activex-control"></a><a name="_core_basic_components_of_an_activex_control"></a>ActiveX 控制項的基本元件

ActiveX 控制件使用多個程式設計元素與控制項容器和使用者進行有效互動。 這些是[COleControl](../mfc/reference/colecontrol-class.md)類、一組事件觸發函數和調度映射。

您開發的每個 ActiveX 控制件物件都繼承其 MFC`COleControl`基類中 一組強大的功能。 這些功能包括就地啟動和自動化邏輯。 `COleControl`可以為控制項物件提供與 MFC 視窗物件相同的功能,以及觸發事件的能力。 `COleControl`也可以提供[無視窗控制件](../mfc/providing-windowless-activation.md),這些控制式依賴於其容器來幫助視窗提供的一些功能(滑鼠捕獲、鍵盤焦點、滾動),但顯示速度要快得多。

由於控件類派生自`COleControl`,因此它繼承了在滿足某些條件時向控件容器發送或"fire"消息(稱為事件)的功能。 當控件中發生重要情況時,這些事件用於通知控件容器。 通過將參數附加到事件,可以將有關事件的其他資訊發送到控制項容器。 有關 ActiveX 控制事件的詳細資訊,請參閱文章[MFC ActiveX 控制項:事件](../mfc/mfc-activex-controls-events.md)。

最後一個元素是調度映射,用於向控制項使用者公開一組函數(稱為方法)和屬性(稱為屬性)。 屬性允許控制項容器或控制使用者以各種方式操作控制項。 用戶可以更改控制項的外觀、更改控制項的某些值或發出控制項的請求,例如存取控制項維護的特定資料段。 此介面由控件開發人員確定,並使用**類視圖**定義。 有關 ActiveX 控制項方法和屬性的詳細資訊,請參閱文章[MFC ActiveX 控制項:方法和](../mfc/mfc-activex-controls-methods.md)[屬性](../mfc/mfc-activex-controls-properties.md)。

## <a name="interaction-between-controls-with-windows-and-activex-control-containers"></a><a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a>控制器與 Windows 和 ActiveX 控制容器之間的互動

當在控制容器中使用控制項時,它使用兩種機制進行通訊:它公開屬性和方法,並觸發事件。 下圖演示了如何實現這兩個機制。

![ActiveX 控制項與其容器通訊](../mfc/media/vc37222.gif "ActiveX 控制項與其容器通訊") <br/>
ActiveX 控制容器與 ActiveX 控制元件之間的通訊

上圖還說明瞭控制檔如何處理其他 OLE 介面(除了自動化和事件)。

控制項與容器的所有通訊都由執行`COleControl`。 要處理容器的某些請求,`COleControl`將呼叫在控制項類別中實現的成員函數。 所有方法和某些屬性都以這種方式處理。 控制項類別的類別還可以透過呼叫的成員函數啟動與容器的`COleControl`通訊 。 事件以這種方式觸發。

## <a name="active-and-inactive-states-of-an-activex-control"></a><a name="_core_active_and_inactive_states_of_an_activex_control"></a>活動X控制器的活躍與非活動狀態

控件有兩個基本狀態:活動狀態和非活動狀態。 傳統上,這些狀態以控件是否具有視窗來區分。 活動控件有一個視窗;非活動控件沒有。 引入無窗口啟動后,這種區別不再普遍,但仍適用於許多控件。

當[無視窗控制器](../mfc/providing-windowless-activation.md)處處於活動狀態時,它將從容器調用滑鼠捕獲、鍵盤焦點、滾動和其他視窗服務。 您還可以[為非活動控制件提供滑鼠互動](../mfc/providing-mouse-interaction-while-inactive.md),以及建立[等待啟動以建立視窗的](../mfc/turning-off-the-activate-when-visible-option.md)控制項。

當具有視窗的控制項變為活動時,它能夠與控制項容器、使用者和 Windows 完全互動。 下圖演示了 ActiveX 控制件、控制容器和作業系統之間的通信路徑。

![視窗化之 ActiveX 控制項中的訊息處理流程](../mfc/media/vc37223.gif "視窗化之 ActiveX 控制項中的訊息處理流程") <br/>
窗動 X 控制檔中的 Windows 訊息處理(啟用時)

## <a name="serialization"></a><a name="_core_serializing_activex_elements"></a>序列化

序列化資料(有時稱為持久性)的能力允許控件將其屬性的值寫入持久存儲。 然後,可以通過從存儲中讀取物件的狀態來重新創建控制項。

請注意,控件不負責獲取對存儲介質的訪問。 相反,控制件的容器負責為控制項提供在適當時間使用的儲存媒體。 有關序列化的詳細資訊,請參閱文章[MFC ActiveX 控制件:序列化](../mfc/mfc-activex-controls-serializing.md)。 有關優化序列化的資訊,請參閱 ActiveX 控件[中的優化持久性和初始化](../mfc/optimizing-persistence-and-initialization.md):優化。

## <a name="installing-activex-control-classes-and-tools"></a><a name="_core_installing_activex_control_classes_and_tools"></a>安裝 ActiveX 控制類別和工具

安裝 Visual C++ 時,如果在安裝程式中選擇 ActiveX 控制件(預設情況下選擇它們),則會自動安裝 MFC ActiveX 控制件類以及零售和調試 ActiveX 控制件運行時 DLL。

預設情況下,ActiveX 控制項類別和工具安裝在 [程式檔]Microsoft Visual Studio .NET 下的以下子目錄中:

- **[公共7]工具**

   包含測試容器檔(TstCon32.exe 及其幫助檔)。

- **[Vc7]atlmfc_包括**

   包含 MFC 開發 ActiveX 控制檔的包含檔案

- **[Vc7]atlmfc\src\mfc**

   包含 MFC 中特定 ActiveX 控制類別的原始碼

- **[Vc7]atlmfc_lib**

   包含 MFC 開發 ActiveX 控制項所需的庫

還有 MFC ActiveX 控制件的範例。 有關這些範例的詳細資訊,請參閱[控制項範例:基於 MFC 的 ActiveX 控制件](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>另請參閱

[使用者介面項目](../mfc/user-interface-elements-mfc.md)
