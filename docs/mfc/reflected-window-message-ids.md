---
title: "反映視窗訊息 Id |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 54b8f0fc8c58ea70a1499104e28a0e0a09bd4fee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="reflected-window-message-ids"></a>反映視窗訊息 ID
一種較快建立 ActiveX 控制項或其他特殊控制項的方法是子類別化一個視窗。 如需詳細資訊，請參閱[MFC ActiveX 控制項： 子類別化 Windows 控制項](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。  
  
 若要防止控制項的容器接收子類別化 Windows 控制項，所傳送的視窗訊息[COleControl](../mfc/reference/colecontrol-class.md)建立 「 反映程式 」 視窗攔截某些視窗訊息，並將其傳回至控制項。 控制項 (在其視窗程序中) 接著可以針對 ActiveX 控制項採取適當的動作，然後再處理這些反映訊息。  
  
 下表顯示攔截的訊息和反映程式視窗傳送的對應訊息。  
  
|由控制項傳送的訊息|反映至控制項的訊息|  
|---------------------------------|--------------------------------------|  
|[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)|**OCM_COMMAND**|  
|[WM_CTLCOLORBTN](http://msdn.microsoft.com/library/windows/desktop/bb761849)|**OCM_CTLCOLORBTN**|  
|[WM_CTLCOLOREDIT](http://msdn.microsoft.com/library/windows/desktop/bb761691)|**OCM_CTLCOLOREDIT**|  
|[WM_CTLCOLORDLG](http://msdn.microsoft.com/library/windows/desktop/ms645417)|**OCM_CTLCOLORDLG**|  
|[WM_CTLCOLORLISTBOX](http://msdn.microsoft.com/library/windows/desktop/bb761360)|**OCM_CTLCOLORLISTBOX**|  
|[WM_CTLCOLORSCROLLBAR](http://msdn.microsoft.com/library/windows/desktop/bb787573)|**OCM_CTLCOLORSCROLLBAR**|  
|[WM_CTLCOLORSTATIC](http://msdn.microsoft.com/library/windows/desktop/bb787524)|**OCM_CTLCOLORSTATIC**|  
|[WM_DRAWITEM](http://msdn.microsoft.com/library/windows/desktop/bb775923)|**OCM_DRAWITEM**|  
|[WM_MEASUREITEM](http://msdn.microsoft.com/library/windows/desktop/bb775925)|**OCM_MEASUREITEM**|  
|[WM_DELETEITEM](http://msdn.microsoft.com/library/windows/desktop/bb761362)|**OCM_DELETEITEM**|  
|[WM_VKEYTOITEM](http://msdn.microsoft.com/library/windows/desktop/bb761364)|**OCM_VKEYTOITEM**|  
|[WM_CHARTOITEM](http://msdn.microsoft.com/library/windows/desktop/bb761358)|**OCM_CHARTOITEM**|  
|[WM_COMPAREITEM](http://msdn.microsoft.com/library/windows/desktop/bb775921)|**OCM_COMPAREITEM**|  
|[WM_HSCROLL](http://msdn.microsoft.com/library/windows/desktop/bb787575)|**OCM_HSCROLL**|  
|[WM_VSCROLL](http://msdn.microsoft.com/library/windows/desktop/bb787577)|**OCM_VSCROLL**|  
|[WM_PARENTNOTIFY](https://msdn.microsoft.com/library/ms632638.aspx)|**OCM_PARENTNOTIFY**|  
|[WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)|**OCM_NOTIFY**|  
  
> [!NOTE]
>  如果控制項是在 Win32 系統上執行，有數種**WM_CTLCOLOR\*** 它可能會收到的訊息。 如需詳細資訊，請參閱**WM_CTLCOLORBTN**， **WM_CTLCOLORDLG**， **WM_CTLCOLOREDIT**， **WM_CTLCOLORLISTBOX**， **WM_CTLCOLORMSGBOX**， **WM_CTLCOLORSCROLLBAR**， **WM_CTLCOLORSTATIC**。  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項： 子類別化 Windows 控制項](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)   
 [TN062：Windows 控制項的訊息反映](../mfc/tn062-message-reflection-for-windows-controls.md)

