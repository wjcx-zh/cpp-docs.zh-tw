---
title: "ActiveX 控制項容器： 檢視和修改控制項屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- properties [MFC], viewing and modifying
- ActiveX control containers [MFC], viewing and modifying properties
- resource editors, viewing and modifying ActiveX controls
- ActiveX controls [MFC], properties
- controls [MFC], properties
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 90e866d1a3be4600b3b98e542caff6ed793f4226
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>ActiveX 控制項容器：檢視和修改控制項屬性
當您將 ActiveX 控制項插入至專案時，檢視和變更 ActiveX 控制項支援的屬性會很有幫助。 本文將討論如何使用 Visual C++ 資源編輯器來進行此動作。  
  
 如果 ActiveX 控制項容器應用程式使用內嵌控制項，您可以在資源編輯器中檢視和修改控制項的屬性。 您也可以在設計階段使用資源編輯器來設定屬性值。 資源編輯器會自動將這些值儲存在專案的資源檔中。 控制項的所有執行個體接著會將其屬性初始化為這些值。  
  
 這個程序假設您已將控制項插入專案中。 如需資訊，請參閱[ActiveX 控制項容器： 插入控制項至控制項容器應用程式中](../mfc/inserting-a-control-into-a-control-container-application.md)。  
  
 檢視控制項屬性的第一步是將控制項的執行個體加入至專案的對話方塊範本。  
  
### <a name="to-view-the-properties-of-a-control"></a>檢視控制項的屬性  
  
1.  在資源檢視中，開啟**對話方塊**資料夾。  
  
2.  開啟您的主要對話方塊範本。  
  
3.  插入 ActiveX 控制項使用**插入 ActiveX 控制項** 對話方塊。 如需詳細資訊，請參閱[檢視及加入 ActiveX 控制項加入至對話方塊](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)。  
  
4.  在對話方塊中，選取 ActiveX 控制項。  
  
5.  從 [屬性] 視窗中，按一下 [**屬性**] 按鈕。  
  
 使用**屬性**對話方塊來修改並立即測試新的屬性。  
  
## <a name="see-also"></a>另請參閱  
 [ActiveX 控制項容器](../mfc/activex-control-containers.md)

