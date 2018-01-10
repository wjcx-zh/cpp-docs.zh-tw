---
title: "非現用時提供滑鼠互動 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: MFC ActiveX controls [MFC], mouse interaction
ms.assetid: b09106bf-44c7-4b9b-a6d9-0d624f16f5b3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a2f8991b6cc827c35c94b0989ef82e32422fd5c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="providing-mouse-interaction-while-inactive"></a>非現用時提供滑鼠互動
如果未立即啟動您的控制項，您可能仍然希望它處理`WM_SETCURSOR`和`WM_MOUSEMOVE`訊息，即使控制項有沒有自己的視窗。 這可藉由啟用`COleControl`的實作`IPointerInactive`介面，預設會停用。 (請參閱*ActiveX SDK*此介面的說明。)若要啟用它，包括`pointerInactive`旗標所傳回的集合中的旗標[Clippaintdc](../mfc/reference/colecontrol-class.md#getcontrolflags):  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_3.cpp)]  
  
 如果您選取，將自動產生納入這個旗標的程式碼**滑鼠指標告知時非使用中**選項[控制設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md)頁面與建立控制項時**MFC ActiveX 控制項精靈**。  
  
 當`IPointerInactive`介面已啟用，容器委派`WM_SETCURSOR`和`WM_MOUSEMOVE`給它的訊息。 `COleControl`實作`IPointerInactive`適當調整滑鼠座標之後，會透過控制項的訊息對應的訊息分派。 您可以將對應的項目新增至訊息對應處理的訊息，就像一般視窗訊息一樣。 在您為這些訊息的處理常式，請避免使用`m_hWnd`成員變數 （或任何成員函式，會使用它），其值不是先檢查**NULL**。  
  
 您也可以做為 OLE 拖放作業的目標非現用控制項。 這需要在使用者拖曳物件時，啟動控制項，使控制項的視窗可以登錄為置放目標。 若要使啟用時，拖曳，覆寫[COleControl::GetActivationPolicy](../mfc/reference/colecontrol-class.md#getactivationpolicy)，並傳回**POINTERINACTIVE_ACTIVATEONDRAG**旗標：  
  
 [!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_4.cpp)]  
  
 啟用`IPointerInactive`介面通常表示您想要能夠隨時處理滑鼠訊息的控制項。 若要取得這項行為並不支援的容器中`IPointerInactive`介面，您必須擁有控制項一律啟動時顯示，表示控制項應該包含**OLEMISC_ACTIVATEWHENVISIBLE**之間加上旗標其他的旗標。 不過，若要避免這個旗標從生效的容器中，支援`IPointerInactive`，您也可以指定**OLEMISC_IGNOREACTIVATEWHENVISIBLE**旗標：  
  
 [!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_5.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)

