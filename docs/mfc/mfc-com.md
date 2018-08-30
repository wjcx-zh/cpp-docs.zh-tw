---
title: MFC COM |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MFC COM (MFC)
dev_langs:
- C++
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e8c3af361e1ffb5928132727fa124f03a99e81e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205645"
---
# <a name="mfc-com"></a>MFC COM
MFC 的子集專門設計來支援 COM，而大部分的 Active Template Library (ATL) 設計為 COM 程式設計。 本節的主題描述 COM 的 MFC 支援  
  
 Active 技術 （例如 ActiveX 控制項、 使用中文件內含項目、 OLE 和等等） 使用元件物件模型 (COM)，以便在網路上的環境中，不論它們是語言與彼此互動的軟體元件建立。 Active 技術可用來建立在桌面或網際網路執行的應用程式。 如需詳細資訊，請參閱[COM 簡介](../atl/introduction-to-com.md)或是[元件物件模型](/windows/desktop/com/the-component-object-model)。  
  
 Active 技術包括用戶端和伺服器技術，包括下列：  
  
-   [主動式文件內含項目](../mfc/active-document-containment.md)、 支援 MFC 版本 4.2 和更新版本，可讓使用者檢視[主動式文件](../mfc/active-documents.md)（例如 Microsoft Excel 或 Word 檔案） 並啟用文件的原生的整個介面應用程式的整個工作區[主動式文件容器](../mfc/active-document-containers.md)例如 Microsoft Office Binder 或 Microsoft Internet Explorer。 所提供的文件時，用戶端，作為容器[作用中的文件伺服程式](../mfc/active-document-servers.md)。 如需有關如何使用主動式文件中的網際網路應用程式的詳細資訊，請參閱：[在網際網路上的主動式文件](../mfc/active-documents-on-the-internet.md)。  
  
-   ActiveX 控制項是可用的網站等容器中的互動式物件。 如需有關 ActiveX 控制項的詳細資訊，請參閱：  
  
    -   [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)  
  
    -   [網際網路上的 ActiveX 控制項](../mfc/activex-controls-on-the-internet.md)  
  
    -   [概觀： 網際網路](../mfc/mfc-internet-programming-basics.md)  
  
    -   [升級要在網際網路上使用現有的 ActiveX 控制項](../mfc/upgrading-an-existing-activex-control.md)  
  
    -   [偵錯 ActiveX 控制項](/visualstudio/debugger/how-to-debug-an-activex-control)  
  
-   動態指令碼可控制從瀏覽器或伺服器的一或多個 ActiveX 控制項的整合式的行為。 如需有關如何使用指令碼的詳細資訊，請參閱[網際網路上的 Active 技術](../mfc/active-technology-on-the-internet.md)。  
  
-   [自動化](../mfc/automation.md)（先前稱為 OLE Automation） 可讓一個應用程式操作另一個的應用程式中實作的物件，或 「 公開 」 物件以便可以操作。  
  
     自動化的物件可以是本機或遠端 （在另一部電腦透過網路存取）。 Aurotmation 可供 OLE 和 COM 物件使用。  
  
-   本章節也提供有關如何撰寫使用 MFC，例如，在 COM 元件的資訊[連接點](../mfc/connection-points.md)。  
  
 如功能仍會呼叫 OLE 與現在所謂 active 技術的討論，請參閱主題[OLE](../mfc/ole-in-mfc.md)。  
  
 此外，請參閱知識庫文章 Q248019： 如何： 防止伺服器忙線中對話方塊方塊從出現在長時間 COM 作業。  
  
## <a name="in-this-section"></a>本節內容  
 [主動式文件內含項目](../mfc/active-document-containment.md)  
  
 [Automation](../mfc/automation.md)  
  
 [連接點](../mfc/connection-points.md)  
  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)  
  
## <a name="see-also"></a>另請參閱  
 [概念](../mfc/mfc-concepts.md)

