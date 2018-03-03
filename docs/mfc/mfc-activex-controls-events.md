---
title: "MFC ActiveX 控制項： 事件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- notifications [MFC], notifying containers of events
- custom events [MFC], adding to ActiveX controls
- events [MFC], mapping
- COleControl class [MFC], handling of events
- mappings [MFC], events
- stock events [MFC]
- container events [MFC]
- events [MFC], ActiveX controls
- OLE events [MFC]
ms.assetid: e1e57e0c-206b-4923-a0b5-682c26564f74
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b6760f2051542a28e78f5f8f2fa81f6937388d82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-events"></a>MFC ActiveX 控制項：事件
ActiveX 控制項使用事件通知發生有問題的控制項的容器。 事件的常見範例包含控制項時，使用鍵盤和變更控制項的狀態中輸入的資料點選。 這些動作發生時，控制項就會引發事件來警示容器。  
  
 事件也稱為訊息。  
  
 MFC 支援兩種類型的事件： 內建和自訂。 內建事件是這些類別的事件[COleControl](../mfc/reference/colecontrol-class.md)會自動處理。 內建事件完整清單，請參閱文章[MFC ActiveX 控制項： 加入內建事件](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)。 自訂事件可讓控制項以通知容器，該控制項的特定動作發生時的能力。 某些範例可能是控制項的內部狀態或某些視窗訊息回條中的變更。  
  
 才能讓控制項適當地引發事件，控制項類別必須對應到相關的事件發生時，應該呼叫成員函式的每個控制項的事件。 這項對應機制 （稱為事件對應） 集中管理事件的相關資訊，並可讓 Visual Studio 可輕易地存取及管理控制項的事件。 這個事件對應由下列巨集，位於標頭中宣告 (。H） 檔案的控制項類別宣告：  
  
 [!code-cpp[NVC_MFC_AxUI#2](../mfc/codesnippet/cpp/mfc-activex-controls-events_1.h)]  
  
 宣告事件對應之後，必須定義在您的控制項實作 (。CPP) 檔案。 下列程式碼會定義事件對應，可讓您的控制項來引發特定事件：  
  
 [!code-cpp[NVC_MFC_AxUI#3](../mfc/codesnippet/cpp/mfc-activex-controls-events_2.cpp)]  
[!code-cpp[NVC_MFC_AxUI#4](../mfc/codesnippet/cpp/mfc-activex-controls-events_3.cpp)]  
  
 如果您使用 MFC ActiveX 控制項精靈建立專案時，它會自動加入這些線條。 如果您不使用 MFC ActiveX 控制項精靈，您必須手動加入這行。  
  
 使用 類別檢視中，您可以加入類別所支援的內建事件`COleControl`或您定義的自訂事件。 針對每個新的事件類別檢視 會自動將適當項目控制項的事件對應和控制項的。IDL 檔案。  
  
 兩個其他文章中討論的詳細資料中的事件：  
  
-   [MFC ActiveX 控制項： 加入內建事件](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)  
  
-   [MFC ActiveX 控制項：新增自訂事件](../mfc/mfc-activex-controls-adding-custom-events.md)  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項： 方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl 類別](../mfc/reference/colecontrol-class.md)
