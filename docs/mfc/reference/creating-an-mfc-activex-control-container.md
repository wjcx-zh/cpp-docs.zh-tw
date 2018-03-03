---
title: "建立 MFC ActiveX 控制項容器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.activex.container
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], containers
- ActiveX control containers [MFC], creating
- containers [MFC], creating
- OLE controls [MFC], containers
ms.assetid: ec70e137-7c14-4940-bd0e-fd4edcc63ea5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2054a11365cc6f9db7a5608f0b056d0d85ff117d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-an-mfc-activex-control-container"></a>建立 MFC ActiveX 控制項容器
ActiveX 控制項容器是父程式，提供 ActiveX (先前稱為 OLE) 控制項執行環境。 您可以建立應用程式能夠包含 ActiveX 控制項，不論 MFC，但更容易使用 MFC 進行。  
  
 建立 MFC 容器使用的程式[MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)可讓您存取由 MFC 和 ActiveX 類別實作的許多功能的 ActiveX 控制項和自動化。 這些功能包括視覺化編輯，自動化、 建立複合檔案，以及支援的控制項。 父程式將支援的 MFC 應用程式精靈視覺化編輯選項包括建立容器、 迷你伺服器、 全伺服器和容器和伺服器的程式。  
  
-   **新的 MFC 應用程式**。 若要建立新的 MFC 程式包含自動化，視覺化編輯，複合檔案，或控制支援、 使用 MFC 應用程式精靈以及選擇適當的自動化選項。  
  
-   **現有的 MFC 應用程式**。 如果您要將控制項內含項目加入現有的 MFC 應用程式，請參閱[OLE 控制項容器： 手動啟用 OLE 控制項內含項目](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)。  
  
### <a name="to-create-an-activex-container-for-any-of-the-following-types-of-applications"></a>若要建立 ActiveX 容器任何下列類型的應用程式  
  
1.  [容器](../../mfc/containers.md)  
  
2.  [視覺化編輯](../../mfc/ole-mfc.md)  
  
3.  [MFC ActiveX 控制項](../../mfc/mfc-activex-controls.md)  
  
## <a name="see-also"></a>請參閱  
 [Visual C++ 專案類型](../../ide/visual-cpp-project-types.md)

