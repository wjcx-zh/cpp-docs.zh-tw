---
title: "訊息對應 (MFC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "訊息對應 [C++], MFC"
  - "訊息 [C++], Windows"
  - "MFC [C++], 訊息"
  - "Windows 訊息 [C++], 訊息對應"
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 訊息對應 (MFC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

參考這個部分列出所有 [訊息對應巨集](../../mfc/reference/message-map-macros-mfc.md) 和所有 [CWnd](../../mfc/reference/cwnd-class.md) 訊息對應項目與對應的成員函式原型：  
  
|分類|說明|  
|--------|--------|  
|[WM\_COMMAND 訊息處理常式](../../mfc/reference/wm-command-message-handler.md)|控制使用者選取功能表項目或功能表便捷鍵產生的 **WM\_COMMAND** 之訊息。|  
|[子視窗通知訊息處理常式](../../mfc/reference/child-window-notification-message-handlers.md)|從子視窗處理通知訊息。|  
|[WM\_ 訊息處理常式](../../mfc/reference/handlers-for-wm-messages.md)|處理 **WM\_** 訊息，例如 `WM_PAINT`。|  
|[使用者定義的訊息處理常式](../../mfc/reference/user-defined-handlers.md)|處理使用者定義的訊息。|  
  
 \(此參考中使用之術語和慣例詞彙的說明，請參閱 [如何使用訊息對應交互參考](../../mfc/reference/how-to-use-the-message-map-cross-reference.md)\)。  
  
 因為 Windows 為訊息導向作業系統，Windows 環境上在程式設計方面有很大的部分牽涉到訊息處理。  每次一事件 \(例如按鍵或滑鼠點選\) 發生，訊息會傳送至必須接著處理事件的應用程式。  
  
 MFC 程式庫提供訊息架構程式設計用來最佳化的程式設計模型。  在這個模型中，「訊息對應」用於指定哪些函式處理特定類別的各種訊息。  訊息對應中包含指定那些訊息須由那些函式處理的一或多個巨集。  例如， 包含 `ON_COMMAND` 巨集的訊息對應可能看起來像這樣：  
  
 [!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/CPP/message-maps-mfc_1.cpp)]  
  
 `ON_COMMAND` 巨集用來處理由功能表、按鈕和快速鍵所產生的命令訊息。  可使用[巨集](../../mfc/reference/message-map-macros-mfc.md) 對應下列：  
  
## Windows 訊息  
  
-   控制通知  
  
-   使用者定義的訊息  
  
## 命令訊息  
  
-   註冊使用者定義的訊息  
  
-   使用者介面更新訊息  
  
## 訊息的範圍  
  
-   命令  
  
-   更新處理常式訊息  
  
-   控制通知  
  
 雖然訊息對應巨集很重要，但您通常不需要直接使用。  這是因為，當您使用其關聯之訊息處理函式與訊息時，屬性視窗會自動在您的原始程式檔建立的訊息對應項目。  在您要編輯或加入訊息對應項目時，您可以使用屬性視窗。  
  
> [!NOTE]
>  屬性視窗不支援訊息對應範圍。  您必須自己寫入這些訊息對應項目。  
  
 不過，訊息對應是 MFC 程式庫的重要部分。  有提供它們的文件，您應該了解它們在做什麼。  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)