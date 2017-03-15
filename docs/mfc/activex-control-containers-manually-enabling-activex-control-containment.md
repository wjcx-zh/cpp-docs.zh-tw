---
title: "ActiveX 控制項容器：手動啟用 ActiveX 控制項內含項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項容器 [C++], 啟用"
  - "ActiveX 控制項 [C++], 啟用容器"
  - "AfxEnableControlContainer 方法"
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# ActiveX 控制項容器：手動啟用 ActiveX 控制項內含項目
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您未啟用 ActiveX 控制項支援，當您使用 MFC 應用程式精靈產生的應用程式，您必須手動將這項支援。  本文說明手動加入的 ActiveX 控制項內含項目流程到現有的 OLE 容器應用程式。  如果您預先知道您想要在您的 OLE 容器的 ActiveX 控制項支援，請參閱本文件的 [建立 MFC ActiveX 控制項容器](../mfc/reference/creating-an-mfc-activex-control-container.md)。  
  
> [!NOTE]
>  本文使用對話方塊架構的 ActiveX 控制項容器專案名為 Container 和內嵌控制項 \(名為\) Circ 做為範例在程序和程式碼。  
  
 若要支援 ActiveX 控制項，您必須將程式碼加入至兩個您的專案檔案。  
  
-   由呼叫的 MFC 應用程式精靈來修改主對話方塊的 `InitInstance` 函式 \(位於 CONTAINER.CPP\) 對 [AfxEnableControlContainer](../Topic/AfxEnableControlContainer.md)，如下列範例所示:  
  
     [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/CPP/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]  
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/CPP/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]  
  
-   將下列加入至項目的 STDAFX.H 標頭檔:  
  
     [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/CPP/activex-control-containers-manually-enabling-activex-control-containment_3.h)]  
  
 在您完成這些步驟之後，按一下 \[**組建**\] 重新建置您的專案按一下 \[**組建**\] 功能表。  
  
## 請參閱  
 [ActiveX 控制項容器](../mfc/activex-control-containers.md)