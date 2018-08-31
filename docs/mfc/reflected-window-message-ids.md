---
title: 反映視窗訊息 Id |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- OCM_CTLCOLORBTN
- OCM_PARENTNOTIFY
- OCM_VKEYTOITEM
- OCM_CTLCOLORSTATIC
- OCM_HSCROLL
- OCM_CHARTOITEM
- OCM_DRAWITEM
- OCM_MEASUREITEM
- OCM_COMPAREITEM
- OCM_COMMAND
- OCM_NOTIFY
- OCM_CTLCOLORMSGBOX
- OCM_DELETEITEM
- OCM_CTLCOLORLISTBOX
- OCM_CTLCOLORDLG
- OCM_CTLCOLOREDIT
- OCM_CTLCOLORSCROLLBAR
- OCM_VSCROLL
- OCM_CTLCOLOR
dev_langs:
- C++
helpviewer_keywords:
- OCM_HSCROLL message [MFC]
- OCM_PARENTNOTIFY message [MFC]
- messages, reflected
- reflected messages, window message Ids
- OCM_CTLCOLORDLG message [MFC]
- OCM_COMMAND message [MFC]
- OCM_CTLCOLORMSGBOX message [MFC]
- OCM_COMPAREITEM message [MFC]
- OCM_DRAWITEM message [MFC]
- OCM_VSCROLL message [MFC]
- OCM_CTLCOLOREDIT message [MFC]
- OCM_VKEYTOITEM message [MFC]
- OCM_CHARTOITEM message [MFC]
- OCM_CTLCOLORBTN message [MFC]
- OCM_CTLCOLORSTATIC message [MFC]
- OCM_MEASUREITEM message [MFC]
- OCM_CTLCOLOR message [MFC]
- OCM_CTLCOLORSCROLLBAR message [MFC]
- OCM_ messages
- OCM_DELETEITEM message [MFC]
- OCM_CTLCOLORLISTBOX message [MFC]
- OCM_NOTIFY message [MFC]
- reflected messages
ms.assetid: 3417ff51-ff9f-458c-bff4-17c200f00d96
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 037eaa864f4b24622fdd72e15674fb8489f9b4bb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220010"
---
# <a name="reflected-window-message-ids"></a>反映視窗訊息 ID
一種較快建立 ActiveX 控制項或其他特殊控制項的方法是子類別化一個視窗。 如需詳細資訊，請參閱 < [MFC ActiveX 控制項： 子類別化 Windows 控制項](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。  
  
 若要防止控制項的容器接收視窗訊息，由子類別化 Windows 控制項，傳送[COleControl](../mfc/reference/colecontrol-class.md)建立攔截某些視窗訊息，並將其傳回給控制項的"reflector"視窗。 控制項 (在其視窗程序中) 接著可以針對 ActiveX 控制項採取適當的動作，然後再處理這些反映訊息。  
  
 下表顯示攔截的訊息和反映程式視窗傳送的對應訊息。  
  
|由控制項傳送的訊息|反映至控制項的訊息|  
|---------------------------------|--------------------------------------|  
|[WM_COMMAND](/windows/desktop/menurc/wm-command)|OCM_COMMAND|  
|[WM_CTLCOLORBTN](/windows/desktop/Controls/wm-ctlcolorbtn)|OCM_CTLCOLORBTN|  
|[WM_CTLCOLOREDIT](/windows/desktop/Controls/wm-ctlcoloredit)|OCM_CTLCOLOREDIT|  
|[WM_CTLCOLORDLG](/windows/desktop/dlgbox/wm-ctlcolordlg)|OCM_CTLCOLORDLG|  
|[WM_CTLCOLORLISTBOX](/windows/desktop/Controls/wm-ctlcolorlistbox)|OCM_CTLCOLORLISTBOX|  
|[WM_CTLCOLORSCROLLBAR](/windows/desktop/Controls/wm-ctlcolorscrollbar)|OCM_CTLCOLORSCROLLBAR|  
|[WM_CTLCOLORSTATIC](/windows/desktop/Controls/wm-ctlcolorstatic)|OCM_CTLCOLORSTATIC|  
|[WM_DRAWITEM](/windows/desktop/Controls/wm-drawitem)|OCM_DRAWITEM|  
|[WM_MEASUREITEM](/windows/desktop/Controls/wm-measureitem)|OCM_MEASUREITEM|  
|[WM_DELETEITEM](/windows/desktop/Controls/wm-deleteitem)|OCM_DELETEITEM|  
|[WM_VKEYTOITEM](/windows/desktop/Controls/wm-vkeytoitem)|OCM_VKEYTOITEM|  
|[WM_CHARTOITEM](/windows/desktop/Controls/wm-chartoitem)|OCM_CHARTOITEM|  
|[WM_COMPAREITEM](/windows/desktop/Controls/wm-compareitem)|OCM_COMPAREITEM|  
|[時傳遞 WM_HSCROLL](/windows/desktop/Controls/wm-hscroll)|OCM_HSCROLL|  
|[WM_VSCROLL](/windows/desktop/Controls/wm-vscroll)|OCM_VSCROLL|  
|[WM_PARENTNOTIFY](/previous-versions/windows/desktop/inputmsg/wm-parentnotify)|OCM_PARENTNOTIFY|  
|[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)|OCM_NOTIFY|  
  
> [!NOTE]
>  如果控制項是在 Win32 系統上執行，有數種類型的 WM_CTLCOLOR\*它可能會收到的訊息。 如需詳細資訊，請參閱 WM_CTLCOLORBTN、 WM_CTLCOLORDLG、 WM_CTLCOLOREDIT、 WM_CTLCOLORLISTBOX、 WM_CTLCOLORMSGBOX、 WM_CTLCOLORSCROLLBAR、 WM_CTLCOLORSTATIC。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項： 子類別化 Windows 控制項](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)   
 [TN062：Windows 控制項的訊息反映](../mfc/tn062-message-reflection-for-windows-controls.md)

