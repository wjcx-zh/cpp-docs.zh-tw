---
title: MFC ActiveX 控制項：子類別化 Windows 控制項
ms.date: 09/12/2018
f1_keywords:
- precreatewindow
- IsSubclassed
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- subclassing
- DoSuperclassPaint method [MFC]
- subclassing Windows controls
- subclassing, Windows controls
- reflected messages, in ActiveX controls
- PreCreateWindow method, overriding
- MFC ActiveX controls [MFC], subclassed controls
- MFC ActiveX controls [MFC], creating
- IsSubclassed method [MFC]
ms.assetid: 3236d4de-401f-49b7-918d-c84559ecc426
ms.openlocfilehash: ccebbad22be92b84fa2fd84434f788484d332cce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376002"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>MFC ActiveX 控制項：子類別化 Windows 控制項

本文說明子類別化通用 Windows 控制項以建立 ActiveX 控制項的流程。 子類別化現有的 Windows 控制項是一種可快速開發 ActiveX 控制項的方式。 新的控制項將會具有已子類別化之 Windows 控制項的能力，例如繪製和回應滑鼠點選動作。 MFC ActiveX 控制件範例[BUTTON](../overview/visual-cpp-samples.md)是對 Windows 控制件進行子類化的範例。

>[!IMPORTANT]
> ActiveX 是一種不應用於新開發的傳統技術。 有關取代 ActiveX 的現代技術的詳細資訊,請參閱[ActiveX 控制件](activex-controls.md)。

若要子類別化 Windows 控制項，請完成下列工作：

- [覆寫 COleControl 的 IsSubclassedControl 和 PreCreateWindow 成員函式](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [修改 OnDraw 成員函式](#_core_modifying_the_ondraw_member_function)

- [處理所有反映至控制項的 ActiveX 控制項訊息 (OCM)](#_core_handling_reflected_window_messages)

   > [!NOTE]
   > 如果選擇控制項使用 **「控制項設定」** 頁上**的「選擇父視窗類**」下拉清單進行子分類,則大部分工作由 ActiveX 控制件精靈完成。

## <a name="overriding-issubclassedcontrol-and-precreatewindow"></a><a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a>重寫是子類控制並預建立視窗

要重寫`PreCreateWindow``IsSubclassedControl`和,請向控制項類聲明的**受保護**部分添加以下行代碼:

[!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

在控制項實作檔 (.CPP) 中，加入下列程式碼以實作兩個覆寫的函式：

[!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

請注意，在此範例中，Windows 按鈕控制項是在 `PreCreateWindow` 中指定。 不過，所有標準的 Windows 控制項都可以進行子類別化。 有關標準 Windows 控制件的詳細資訊,請參閱[控制項](../mfc/controls-mfc.md)。

子類別化 Windows 控制項時，您可能會想要指定特定的視窗樣式 (WS_) 或延伸視窗樣式 (WS_EX_) 旗標，以便在建立控制項的視窗時使用。 您可以通過修改`PreCreateWindow``cs.style``cs.dwExStyle`和結構欄位在成員函數中設置這些參數的值。 應使用**OR**操作對這些欄位進行修改,以保留`COleControl`由 類設置的默認標誌。 例如，如果控制項是要子類別化 BUTTON 控制項，而且您想要讓控制項顯示為核取方塊，請將下列程式碼插入至 `CSampleCtrl::PreCreateWindow` 實作中 return 陳述式之前：

[!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

此操作將添加BS_CHECKBOX樣式標誌,同時保留類`COleControl`的預設樣式標誌(WS_CHILD)。

## <a name="modifying-the-ondraw-member-function"></a><a name="_core_modifying_the_ondraw_member_function"></a>修改 OnDraw 成員函數

如果您希望子類別化後的控制項保留與對應之 Windows 控制項的相同外觀，控制項的 `OnDraw` 成員函式應該只包含對 `DoSuperclassPaint` 成員函式的呼叫，如下列範例所示：

[!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

`DoSuperclassPaint` 成員函式 (由 `COleControl` 所實作) 會在指定的裝置內容中使用 Windows 控制項的視窗程序將控制項繪製在周框矩形之內。 如此可讓控制項即使並未處於作用中也會成為可見狀態。

> [!NOTE]
> 成員`DoSuperclassPaint`函數將僅適用於那些允許將設備上下文作為WM_PAINT消息的*wParam*傳遞的控制項類型。 這些控制項類型包括一些標準的 Windows 控制項，例如 SCROLLBAR 和 BUTTON，以及所有通用控制項。 對於不支援這個行為的控制項，您必須提供自己的程式碼以便正確顯示非現用控制項。

## <a name="handling-reflected-window-messages"></a><a name="_core_handling_reflected_window_messages"></a>處理反射視窗訊息

Windows 控制項通常會將某些視窗訊息傳送給其父視窗。 這些訊息中的某些訊息 (例如 WM_COMMAND) 是由使用者提供動作的通知。 其他(如WM_CTLCOLOR)用於從父窗口獲取資訊。 ActiveX 控制項通常會透過其他方法與父視窗進行通訊。 通知是藉由引發事件 (傳送事件通知) 進行通訊，而控制項容器的相關資訊則是藉由存取容器的環境屬性取得。 由於這些通訊技術的存在，ActiveX 控制項容器不應該處理控制項所傳送的任何視窗訊息。

為了要防止容器接收已子類別化之 Windows 控制項所傳送的視窗訊息，`COleControl` 會建立一個額外的視窗做為控制項的父代。 這個額外的視窗 (稱為「反映程式」) 只會針對子類別化 Windows 控制項的 ActiveX 控制項而建立，同時其大小和位置會與控制項視窗相同。 反映程式視窗會攔截某些視窗訊息，並將其傳送回控制項。 控制項 (在其視窗程序中) 接著便可以採取適用於 ActiveX 控制項的動作 (例如，引發事件)，以處理這些反映的訊息。 有關截獲的視窗消息及其相應的反射消息的清單,請參閱[反射視窗消息文檔。](../mfc/reflected-window-message-ids.md)

ActiveX 控制項容器可能會設計為自行執行訊息反映，如此便不需要讓 `COleControl` 建立反映程式視窗，同時並可降低子類別化之 Windows 控制項的執行階段負荷。 `COleControl`通過檢查值為**TRUE**的 MessageReflect 環境屬性,檢測容器是否支援此功能。

若要處理反映的視窗訊息，請新增一個項目至控制項訊息對應，並實作處理函式。 由於反映的訊息並不是由 Windows 定義的一套標準訊息，因此 [類別檢視] 不支援加入這類訊息處理常式。 不過，手動加入處理常式並不困難。

若要為反映的 Windows 訊息手動加入訊息處理常式，請執行下列動作：

- 在控制項類別的 .H 檔案中，宣告處理常式函式。 該函數應具有**LRESULT**的傳回類型和兩個參數,分別具有**WPARAM**和**LPARAM**類型。 例如：

   [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- 在控制類中。CPP 檔,向消息映射添加ON_MESSAGE條目。 這個項目的參數應該是訊息識別項和處理常式函式的名稱。 例如：

   [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- 也在 。CPP 檔案`OnOcmCommand`, 實現成員函數來處理反射的消息。 *wParam*和*lParam*參數與原始視窗訊息的參數相同。

有關如何處理反射消息的範例,請參閱 MFC ActiveX 控制件範例[BUTTON](../overview/visual-cpp-samples.md)。 它演示了`OnOcmCommand`一個處理程式,該處理程序檢測BN_CLICKED通知代碼並通過觸發(發送`Click`) 事件進行回應。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)
