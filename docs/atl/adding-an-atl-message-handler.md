---
title: 加入 ATL 訊息處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handlers [C++]
- ATL, windows
- message handling [C++], ATL message handler
- windows [C++], ATL
- ATL, message handlers
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e79598b79ccbad13ad98c7fc1284808fe1b05cfc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="adding-an-atl-message-handler"></a>加入 ATL 訊息處理常式
若要加入至控制項的訊息處理常式 （成員函式會處理 Windows 訊息），第一次在 類別檢視選取的控制項。 然後開啟**屬性**視窗中，選取**訊息**圖示，並按一下下拉箭號控制相反必要的訊息方塊中。 這會將訊息處理常式的宣告中控制項的標頭檔和控制項的.cpp 檔案中的處理常式的基本架構實作。 它也會新增訊息對應，並新增處理常式項目。  
  
 加入 ATL 中的訊息處理常式是類似於 MFC 類別將訊息處理常式。 請參閱[加入 MFC 訊息處理常式](../mfc/reference/adding-an-mfc-message-handler.md)如需詳細資訊。  
  
 在下列情況只適用於加入 ATL 訊息處理常式：  
  
-   訊息處理常式會遵循與 MFC 的相同命名慣例。  
  
-   新的訊息對應項目會加入到主訊息對應。 精靈無法辨識其他的訊息對應和鏈結。  
  
## <a name="see-also"></a>另請參閱  
 [實作視窗](../atl/implementing-a-window.md)

