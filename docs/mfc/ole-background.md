---
title: "OLE 背景 | Microsoft Docs"
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
  - "OLE, 關於 OLE"
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE 背景
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

OLE 是可讓使用者建立和編輯包含由多個應用程式建立的項目或「物件」的文件。  
  
> [!NOTE]
>  OLE 最初是物件連結與嵌入的縮寫。  不過，它現在稱為 OLE。  OLE 與連結和內嵌無關的部分現在是 Active 技術的一部分。  
  
 OLE 文件，以往稱為複合文件，完美整合資料的各種類別或元件。  音效的目錄、報表和點陣圖是 OLE 文件中找到之元件的典型的例子。  在您的應用程式中支援 OLE 讓您的使用者使用 OLE 時不需考慮不同應用程式之間的切換；OLE會幫您作切換。  
  
 您可以使用一個容器應用程式建立複合文件和一個伺服器應用程式或元件應用程式在容器文件內建立項目。  您撰寫的應用程式可以是容器、伺服器或兩者。  
  
 OLE 合併許多不同的概念，工作往完美互動的目標在應用程式之間。  這些區域包含下列：  
  
 連結和內嵌  
 連結和內嵌是儲存一個由其它應用程式建立的 OLE 文件內的項目的兩種方法。  如需兩者之間差異的一般資訊，請參閱本文件的 [OLE 背景:連結和內嵌](../mfc/ole-background-linking-and-embedding.md)。  如需詳細資訊，請參閱文件 [容器](../mfc/containers.md) 和 [伺服器](../mfc/servers.md)。  
  
 就地啟動 \(視覺化編輯\)  
 在容器文件中啟動內嵌項目被稱為就地啟動或視覺化編輯。  容器應用程式的介面變更合併建立內嵌項目元件應用程式的功能。  連結項目永遠不就地啟動，因為實際資料項目在個別的檔案中，在包含這個連結的應用程式的內容之外。  如需就地啟動的詳細資訊，請參閱本文件的 [啟動](../mfc/activation-cpp.md)。  
  
> [!NOTE]
>  連結和內嵌和就地啟動提供主要功能的 OLE 視覺化編輯。  
  
 Automation  
 Automation 讓應用程式驅動其他應用程式。  驅動應用程式稱為 Automation 用戶端，然後，被驅動的應用程式稱為 Automation 伺服器或 Automation 元件。  如需 Automation 的詳細資訊，請參閱文件 [Automation 用戶端](../mfc/automation-clients.md) 和 [Automation 伺服程式](../mfc/automation-servers.md)。  
  
> [!NOTE]
>  Automation 在 OLE 和 Active 技術內容都能運作。  您可以以 COM 為基礎的自動化所有物件。  
  
 複合檔案  
 複合檔案提供簡化結構化儲存 OLE 應用程式的複合文件的標準的檔案格式。  在複合檔案內，儲存體具有許多目錄的功能，而且資料流有許多檔案的功能。  這個技術也稱為結構化儲存體。  如需複合檔案的詳細資訊，請參閱本文件的 [容器:複合檔案](../mfc/containers-compound-files.md)。  
  
 制式資料傳輸  
 制式資料傳輸 \(UDT\) 是允許資料以標準模式傳送和接收的一組介面，不管選擇傳送資料的實際方法。  UDT 由拖放表單為資料傳輸的基礎。  UDT 現在做為現有 Windows 資料傳輸，例如剪貼簿和動態資料交換 \(DDE\)。  如需 UDT 的詳細資訊，請參閱本文件的 [資料物件和資料來源 \(Object Linking and Embedding，OLE\)](../mfc/data-objects-and-data-sources-ole.md)。  
  
 拖放  
 拖放功能是傳輸資料一個容易使用、直接在應用程式中、在應用程式中的視窗中甚至在應用程式中的單一視窗內管理的技術。  選取並拖曳要轉送的資料至想要的目的。  根據一致的資料傳輸拖放。  如需拖放的詳細資訊，請參閱本文件的 [拖放](../mfc/drag-and-drop-ole.md)。  
  
 元件物件模型  
 在 OLE 物件彼此通訊時，元件物件模型 \(COM\) 提供基礎結構使用。  MFC OLE 類別為程式設計人員的簡化 COM。  因為 COM 物件構成 OLE 和 Active 技術，所以 COM 是 Active 技術的一部分。  如需 COM 的詳細資訊，請參閱 [Active Template Library \(ATL\)](../atl/active-template-library-atl-concepts.md) 主題。  
  
 一些更重要的 OLE 主題在下列文章中包括：  
  
-   [OLE 背景：連結與內嵌](../mfc/ole-background-linking-and-embedding.md)  
  
-   [OLE 背景：容器和伺服器](../mfc/ole-background-containers-and-servers.md)  
  
-   [OLE 背景：實作策略](../mfc/ole-background-implementation-strategies.md)  
  
-   [OLE 背景：MFC 實作](../mfc/ole-background-mfc-implementation.md)  
  
 對於一般不在上述文章中的 OLE 資訊，搜尋 MSDN 的 OLE。  
  
## 請參閱  
 [OLE](../mfc/ole-in-mfc.md)