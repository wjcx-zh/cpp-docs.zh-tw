---
title: "容器：實作容器 | Microsoft Docs"
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
  - "應用程式 [OLE], OLE 容器"
  - "OLE 容器, 實作"
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 容器：實作容器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文摘要說明實作容器的方法並指向您要提供有關實作之容器的詳細說明的其他文件。  它也會列出您可以實作和描述這些功能的文件的可選擇 OLE 功能。  
  
#### 準備您的 CWinApp 衍生的類別  
  
1.  藉由呼叫 `InitInstance` 成員函式的 **AfxOleInit** 初始化 OLE 程式庫。  
  
2.  當內嵌項目就地啟動時，呼叫 `InitInstance` 的 `CDocTemplate::SetContainerInfo` 指派功能表，然後使用加速資源。  如需關於此主題的詳細資訊，請參閱 [啟用](../mfc/activation-cpp.md)。  
  
 當您使用 MFC 應用程式精靈建立容器應用程式時，這些功能會自動為您提供。  請參閱 [建立 MFC EXE 程式](../mfc/reference/mfc-application-wizard.md)。  
  
#### 準備您的檢視類別。  
  
1.  保持追蹤藉由維護指標選取了指標項目，如果支援多重選取，則為對所選取的項目的指標清單。  您的 `OnDraw` 函式必須繪製所有 OLE 項目。  
  
2.  覆寫 `IsSelected` 確認項目傳遞給它目前是否已選取。  
  
3.  實作 **OnInsertObject** 訊息處理常式以顯示 **Insert Object** 對話方塊。  
  
4.  實作 `OnSetFocus` 訊息處理常式以從檢視將焦點移至就地啟動 OLE 內嵌項目。  
  
5.  實作 `OnSize` 訊息處理常式以通知 OLE 內嵌項目需要變更其矩形以反映它包含的檢視的大小變更。  
  
 由於這些功能的實作會大幅不同於相異應用程式，應用程式精靈只提供基底實作。  您可能必須自訂這些函式才能讓您的應用程式正常運作。  如需這些的範例，請參閱 [CONTAINER](../top/visual-cpp-samples.md) 範例。  
  
#### 處理內嵌和連結的項目。  
  
1.  從 [COleClientItem](../mfc/reference/coleclientitem-class.md) 衍生一個類別  這個類別物件代表已內嵌或連結至您的 OLE 文件的項目。  
  
2.  覆寫 **OnChange**、 `OnChangeItemPosition`和 `OnGetItemPosition`。  這些函式處理縮放，定位和修改內嵌和連結的項目。  
  
 應用程式精靈將為您衍生類別，不過，您可能需要覆寫 **OnChange** 和其他函式與其它在先前程序中的步驟 2 的清單。  因為這些函式實作每個應用程式都不同，基本架構實作需要對大部分的應用程式自訂。  以此範例，請參閱 MFC 範例 [DRAWCLI](../top/visual-cpp-samples.md) 和 [容器](../top/visual-cpp-samples.md)。  
  
 您必須將多個項目加入至容器應用程式的功能表結構以支援 OLE。  如需這些功能的詳細資訊，請參閱 [功能表和資源:加入容器](../mfc/menus-and-resources-container-additions.md)。  
  
 您可能也要支援下列某些在您的容器應用程式的功能:  
  
-   於編輯內嵌項目時就地啟動。  
  
     如需詳細資訊，請參閱 [啟動](../mfc/activation-cpp.md)。  
  
-   OLE 項目的建立透過拖放伺服器應用程式中的選項。  
  
     如需詳細資訊，請參閱 [拖放功能 \(OLE\)](../mfc/drag-and-drop-ole.md)。  
  
-   內嵌物件或組合容器\/伺服器應用程式的連結。  
  
     如需詳細資訊，請參閱 [容器:進階功能](../mfc/containers-advanced-features.md)。  
  
## 請參閱  
 [容器](../mfc/containers.md)   
 [容器：用戶端項目](../mfc/containers-client-items.md)