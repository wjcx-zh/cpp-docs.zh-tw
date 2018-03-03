---
title: "建立 OLE 應用程式的作業順序 |Microsoft 文件"
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
- OLE applications [MFC], creating
- OLE applications [MFC]
- applications [OLE], creating
- applications [OLE]
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db3b5b9a5f4f62fa71cffa37b30a89aee41fe56f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="sequence-of-operations-for-creating-ole-applications"></a>建立 OLE 應用程式的作業順序
下表顯示您的角色和架構的角色建立 OLE 連結和內嵌的應用程式。 這些代表可用的選項而不是一連串的步驟執行。  
  
### <a name="creating-ole-applications"></a>建立 OLE 應用程式  
  
|工作|您會做|架構會做|  
|----------|------------|------------------------|  
|建立 COM 元件。|執行 MFC 應用程式精靈。 選擇**全伺服器**或**迷你伺服器**中**複合文件支援** 索引標籤。|架構會啟用 COM 元件的功能產生基本架構應用程式。 所有的 COM 功能可以傳輸到只稍微修改一下您現有的應用程式。|  
|從頭開始建立容器應用程式。|執行 MFC 應用程式精靈。 選擇**容器**中**複合文件支援**] 索引標籤。使用 [類別檢視，請移至原始程式碼編輯器。 填入 COM 的處理常式函式的程式碼。|架構會產生可以插入由 COM 元件 （伺服器） 應用程式建立的 COM 物件的基本架構應用程式。|  
|建立全新支援自動化的應用程式。|執行 MFC 應用程式精靈。 選擇**自動化**從**進階功能**] 索引標籤。您可以使用 [類別檢視來公開方法和自動化應用程式中的屬性。|架構會產生可以啟動並自動由其他應用程式的基本架構應用程式。|  
  
## <a name="see-also"></a>請參閱  
 [在架構上建置](../mfc/building-on-the-framework.md)   
 [建置 MFC 應用程式的作業順序](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [一系列的作業，用於建立 ActiveX 控制項](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [建立資料庫應用程式的作業順序](../mfc/sequence-of-operations-for-creating-database-applications.md)

