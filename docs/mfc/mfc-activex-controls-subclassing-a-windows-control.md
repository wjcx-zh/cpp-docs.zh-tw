---
title: "MFC ActiveX 控制項： 子類別化 Windows 控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- precreatewindow
- IsSubclassed
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3e41eefdf1c1be2d0e91061e0efce5f5408c1848
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>MFC ActiveX 控制項：子類別化 Windows 控制項
本文說明子類別化通用 Windows 控制項以建立 ActiveX 控制項的流程。 子類別化現有的 Windows 控制項是一種可快速開發 ActiveX 控制項的方式。 新的控制項將會具有已子類別化之 Windows 控制項的能力，例如繪製和回應滑鼠點選動作。 MFC ActiveX 控制項範例[按鈕](../visual-cpp-samples.md)是子類別化 Windows 控制項的範例。  
  
 若要子類別化 Windows 控制項，請完成下列工作：  
  
-   [覆寫 COleControl 的 IsSubclassedControl 和 PreCreateWindow 成員函式](#_core_overriding_issubclassedcontrol_and_precreatewindow)  
  
-   [修改 OnDraw 成員函式](#_core_modifying_the_ondraw_member_function)  
  
-   [處理任何的 ActiveX 控制項訊息 (OCM) 反映至控制項](#_core_handling_reflected_window_messages)  
  
    > [!NOTE]
    >  這項工作為您完成大部分的 ActiveX 控制項精靈如果您選取要使用進行子類別化控制項**選取父視窗類別**下拉式清單上的**控制設定**頁面。  
  
 如需子類別化控制項的詳細資訊，請參閱知識庫文章 Q243454。  
  
##  <a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a>覆寫 IsSubclassedControl 和 PreCreateWindow  
 若要覆寫 `PreCreateWindow` 和 `IsSubclassedControl`，請將下列程式碼加入至控制項類別宣告的 `protected` 區段：  
  
 [!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]  
  
 在控制項實作檔 (.CPP) 中，加入下列程式碼以實作兩個覆寫的函式：  
  
 [!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]  
  
 請注意，在此範例中，Windows 按鈕控制項是在 `PreCreateWindow` 中指定。 不過，所有標準的 Windows 控制項都可以進行子類別化。 如需標準 Windows 控制項的詳細資訊，請參閱[控制項](../mfc/controls-mfc.md)。  
  
 當子類別化 Windows 控制項，您可能想要指定特定的視窗樣式 (**WS_**) 或延伸視窗樣式 (**WS_EX_**) 旗標，以用來建立控制項的視窗。 您可以設定這些參數中的值`PreCreateWindow`成員函式，藉由修改**cs.style**和**cs.dwExStyle**結構欄位。 若要修改這些欄位，您應使用 `OR` 運算，保存由類別 `COleControl` 所設定的預設旗標。 例如，如果控制項是要子類別化 BUTTON 控制項，而且您想要讓控制項顯示為核取方塊，請將下列程式碼插入至 `CSampleCtrl::PreCreateWindow` 實作中 return 陳述式之前：  
  
 [!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]  
  
 此操作會將**BS_CHECKBOX**樣式旗標，但保留預設樣式旗標 (**WS_CHILD**) 類別的`COleControl`保持不變。  
  
##  <a name="_core_modifying_the_ondraw_member_function"></a>修改 OnDraw 成員函式  
 如果您希望子類別化後的控制項保留與對應之 Windows 控制項的相同外觀，控制項的 `OnDraw` 成員函式應該只包含對 `DoSuperclassPaint` 成員函式的呼叫，如下列範例所示：  
  
 [!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]  
  
 `DoSuperclassPaint` 成員函式 (由 `COleControl` 所實作) 會在指定的裝置內容中使用 Windows 控制項的視窗程序將控制項繪製在周框矩形之內。 如此可讓控制項即使並未處於作用中也會成為可見狀態。  
  
> [!NOTE]
>  `DoSuperclassPaint`成員函式只會使用允許做為傳遞裝置內容的控制項類型**wParam**的`WM_PAINT`訊息。 這包含的一些標準 Windows 控制項，例如**捲軸**和**按鈕**，和所有的通用控制項。 對於不支援這個行為的控制項，您必須提供自己的程式碼以便正確顯示非現用控制項。  
  
##  <a name="_core_handling_reflected_window_messages"></a>處理反映視窗訊息  
 Windows 控制項通常會將某些視窗訊息傳送給其父視窗。 其中某些訊息，例如**WM_COMMAND**，提供使用者執行動作的通知。 其他訊息 (例如 `WM_CTLCOLOR`) 是用來取得父視窗的資訊。 ActiveX 控制項通常會透過其他方法與父視窗進行通訊。 通知是藉由引發事件 (傳送事件通知) 進行通訊，而控制項容器的相關資訊則是藉由存取容器的環境屬性取得。 由於這些通訊技術的存在，ActiveX 控制項容器不應該處理控制項所傳送的任何視窗訊息。  
  
 為了要防止容器接收已子類別化之 Windows 控制項所傳送的視窗訊息，`COleControl` 會建立一個額外的視窗做為控制項的父代。 這個額外的視窗 (稱為「反映程式」) 只會針對子類別化 Windows 控制項的 ActiveX 控制項而建立，同時其大小和位置會與控制項視窗相同。 反映程式視窗會攔截某些視窗訊息，並將其傳送回控制項。 控制項 (在其視窗程序中) 接著便可以採取適用於 ActiveX 控制項的動作 (例如，引發事件)，以處理這些反映的訊息。 請參閱[反映視窗訊息 Id](../mfc/reflected-window-message-ids.md)取得一份已攔截視窗訊息，而且其對應反映訊息。  
  
 ActiveX 控制項容器可能會設計為自行執行訊息反映，如此便不需要讓 `COleControl` 建立反映程式視窗，同時並可降低子類別化之 Windows 控制項的執行階段負荷。 `COleControl`偵測容器是否支援這項功能，藉由檢查 MessageReflect 環境屬性值為**TRUE**。  
  
 若要處理反映的視窗訊息，請新增一個項目至控制項訊息對應，並實作處理函式。 由於反映的訊息並不是由 Windows 定義的一套標準訊息，因此 [類別檢視] 不支援加入這類訊息處理常式。 不過，手動加入處理常式並不困難。  
  
 若要為反映的 Windows 訊息手動加入訊息處理常式，請執行下列動作：  
  
-   在控制項類別的 .H 檔案中，宣告處理常式函式。 函式應該有傳回類型為**LRESULT**和具有類型的兩個參數**WPARAM**和**LPARAM**分別。 例如:   
  
     [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]  
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]  
  
-   在控制項類別的 .CPP 檔案中，將 `ON_MESSAGE` 項目加入至訊息對應。 這個項目的參數應該是訊息識別項和處理常式函式的名稱。 例如:   
  
     [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]  
  
-   此外，在。CPP 檔案實作**OnOcmCommand**成員函式來處理反映的訊息。 **WParam**和**lParam**參數都是一樣的原始視窗訊息。  
  
 如需如何的範例處理反映訊息，請參閱 MFC ActiveX 控制項範例[按鈕](../visual-cpp-samples.md)。 它會示範**OnOcmCommand**偵測到的處理常式**BN_CLICKED**通知程式碼並透過引發 （傳送） 回應 Click 事件。  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)

