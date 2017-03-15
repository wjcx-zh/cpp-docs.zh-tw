---
title: "OLE 背景：MFC 實作 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IMarshall"
  - "IMoniker"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IMarshall 類別"
  - "IMoniker 介面, MFC"
  - "MFC 程式庫, 實作"
  - "OLE IMarshal 介面"
  - "OLE IMoniker 介面"
  - "OLE IUnknown"
  - "OLE MFC 程式庫實作"
  - "OLE, 複合檔案"
ms.assetid: 2b67016a-d78e-4d60-925f-c28ec8fb6180
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# OLE 背景：MFC 實作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由於原始 OLE 應用程式開發介面的大小和複雜度，直接呼叫它寫 OLE 應用程式可以非常耗時。  OLE 的 MFC 程式庫實作的目標是要減少完成寫入完整的工作量， OLE 功能的應用程式。  
  
 本文說明未實作的內部 MFC OLE 應用程式開發介面的一部分。  討論如何解釋為實作的對應至 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 OLE 部分。  
  
##  <a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a> 類別庫中實作的 OLE 的部分  
 MFC 不會直接提供一些 OLE 介面和功能。  如果您要使用這些功能，您可以直接呼叫 OLE 應用程式開發介面。  
  
 IMoniker 介面  
 `IMoniker` 介面是由類別庫所實作 \(例如， `COleServerItem` 類別\)，但先前未公開給程式設計人員。  如需這個介面的詳細資訊，請參閱 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 OLE 部分的 OLE Moniker 實作。  不過，也請參閱 [CMonikerFile](../mfc/reference/cmonikerfile-class.md) 和 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)。  
  
 IUnknown 和 IMarshal 介面  
 **IUnknown** 介面是由類別庫所實作，但不會公開給程式設計人員。  **IMarshal** 沒有任何介面是由類別庫所實作，而是在內部使用。  使用類別庫所建置的 Automation 伺服程式已經有封送處理功能內建。  
  
 Docfiles \(複合檔案\)  
 複合檔案由類別庫部分支援。  直接操作在建立之外的複合檔案的函式都不支援。  MFC 使用把 **COleFileStream** 支援資料流的操作和標準資料的函式。  如需詳細資訊，請參閱文件 [容器:複合檔案](../mfc/containers-compound-files.md)。  
  
 同處理序伺服程式和物件處理常式  
 同處理序伺服程式和物件處理常式在動態連結程式庫 \(DLL\) \(DLL\) 中允許編輯資料或完整元件物件模型 \(COM\) \(COM\) 物件的視覺化的實作。  若要這樣做，您可以直接呼叫 OLE 應用程式開發介面實作您的 DLL。  然而，如果您正在撰寫 Automation 伺服程式，且您的伺服程式沒有使用者介面，您可以使用 AppWizard 將您的伺服程式製作成為一個同處理序伺服程式，並將其完整地置入 DLL 裡。  如需這些主題的詳細資訊，請參閱 [Automation 伺服程式](../mfc/automation-servers.md)。  
  
> [!TIP]
>  最簡單的方法實作 Automation 伺服程式將放置在 DLL。  MFC 支援這個方法。  
  
 如需 MFC OLE 類別如何運作的詳細資訊實作 OLE 介面，請參閱 MFC 技術提示 [38](../mfc/tn038-mfc-ole-iunknown-implementation.md)、 [39](../mfc/tn039-mfc-ole-automation-implementation.md)和 [40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md)。  
  
## 請參閱  
 [OLE 背景](../mfc/ole-background.md)   
 [OLE 背景：實作策略](../mfc/ole-background-implementation-strategies.md)