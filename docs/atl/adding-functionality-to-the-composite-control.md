---
title: "將功能加入至複合控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6dcf3ffa0c3168c2f96a3ad9bed13ab1213f63da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="adding-functionality-to-the-composite-control"></a>將功能加入至複合控制項
一旦您已插入任何必要的控制項複合控制項，牽涉到下一個步驟，加入新的功能。 這項新功能通常分為兩類：  
  
-   支援其他介面，以及自訂複合控制項與其他特定功能的行為。  
  
-   處理從包含 ActiveX 控制項 （或控制項） 的事件。  
  
 用途和本文的範圍，如本節的其餘部分著重於僅處理事件從 ActiveX 控制項。  
  
> [!NOTE]
>  如果您需要處理來自 Windows 控制項的訊息，請參閱[實作視窗](../atl/implementing-a-window.md)如需有關在 ATL 中處理的訊息  
  
 插入 ActiveX 控制項對話方塊資源，以滑鼠右鍵按一下控制項，然後按一下**加入事件處理常式**。 選取您想要處理，並按一下該的事件**新增和編輯**。 事件處理常式程式碼會加入至控制項的.h 檔案。  
  
 複合控制項上的 ActiveX 控制項的連接點會自動連線及中斷連線透過呼叫[CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)。  
  
## <a name="see-also"></a>請參閱  
 [複合控制項基本概念](../atl/atl-composite-control-fundamentals.md)

