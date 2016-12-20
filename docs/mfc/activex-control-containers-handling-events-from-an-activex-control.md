---
title: "ActiveX 控制項容器：從 ActiveX 控制項中處理事件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項容器 [C++], 事件接收"
  - "ActiveX 控制項 [C++], 事件"
  - "BEGIN_EVENTSINK_MAP 巨集"
  - "END_EVENTSINK_MAP 巨集, 使用"
  - "事件處理常式 [C++], ActiveX 控制項"
  - "事件處理 [C++], ActiveX 控制項"
  - "事件 [C++], ActiveX 控制項"
  - "ON_EVENT 巨集"
ms.assetid: f9c106db-052f-4e32-82ad-750646aa760b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActiveX 控制項容器：從 ActiveX 控制項中處理事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文將討論使用屬性視窗來安裝 ActiveX 控制項的事件處理常式在 ActiveX 控制項容器。  事件處理常式以回應用來接收告知 \(來自控制項\) 某些事件和執行某些動作。  這個告知稱為」引發事件。  
  
> [!NOTE]
>  本文使用對話方塊架構的 ActiveX 控制項容器專案名為 Container 和內嵌控制項 \(名為\) Circ 做為範例在程序和程式碼。  
  
 使用事件按鈕在屬性視窗中，您可以在您的 ActiveX 控制項容器應用程式可能發生事件的對應。  這個對應，稱為事件接收對應，即 Visual C\+\+ 建立和維護，將事件處理常式加入至控制項容器類別時。  每個事件處理常式，實作與事件對應項目，將特定事件對容器事件處理常式成員函式。  表示指定之事件由 ActiveX 控制項物件時，會引發這個事件處理常式呼叫。  
  
 如需事件接收對應的詳細資訊，請參閱《類別 *庫參考》中的*[事件接收對應](../mfc/reference/event-sink-maps.md) 。  
  
##  <a name="_core_event_handler_modifications_to_the_project"></a> 對專案的事件處理常式中修改  
 當您使用屬性視窗加入事件處理常式時，事件接收對應於專案中宣告和定義。  第一個事件處理常式中，加入下列陳述式加入至控制項 .CPP 檔案。  這個程式碼會宣告為對話方塊類別的 \(在這個案例中， `CContainerDlg`\) 的事件接收對應:  
  
 [!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/CPP/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]  
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/CPP/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]  
  
 當您使用屬性視窗加入事件，事件對應項目 \(`ON_EVENT`\) 加入至事件接收器對應和函式加入容器之實作的事件處理常式 \(.CPP\) 檔案。  
  
 下列範例會宣告事件處理常式中，呼叫 `OnClickInCircCtrl`， Circ 控制項 **ClickIn** 的事件:  
  
 [!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/CPP/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]  
  
 此外，下列範本加入至事件處理常式成員函式的 `CContainerDlg` 類別實作 \(.CPP\) 檔案:  
  
 [!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/CPP/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]  
  
 如需事件接收巨集的詳細資訊，請參閱《類別 *庫參考》中的*[事件接收對應](../mfc/reference/event-sink-maps.md) 。  
  
#### 建立事件處理常式。  
  
1.  從類別檢視中，選取包含 ActiveX 控制項的對話方塊類別。  對於這個範例，請使用 `CContainerDlg`。  
  
2.  在 \[屬性\] 視窗中，按一下 \[**事件**\] 按鈕。  
  
3.  在屬性視窗中，選取內嵌 ActiveX 控制項的控制項 ID。  對於這個範例，請使用 `IDC_CIRCCTRL1`。  
  
     屬性視窗會顯示可供內嵌 ActiveX 控制項引發事件的清單。  會以粗體顯示的所有成員函式已經處理函式指派給它。  
  
4.  選取您要對話方塊類別中處理的事件。  對於這個範例，請選取 **Click**。  
  
5.  從右邊的下拉式清單方塊中，選取 **\<Add\> ClickCircctrl1**。  
  
6.  按兩下從類別檢視的新處理常式函式跳至 `CContainerDlg`實作 \(.CPP\) 檔案中建立事件處理常式程式碼。  
  
## 請參閱  
 [ActiveX 控制項容器](../mfc/activex-control-containers.md)