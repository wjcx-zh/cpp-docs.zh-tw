---
title: "MFC 中的 MAPI 支援 | Microsoft Docs"
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
  - "CDocument 類別, 與 MAPI"
  - "MFC 中的 MAPI 支援"
  - "MAPI, MFC"
  - "MFC, MAPI 支援"
  - "OnFileSendMail 方法"
  - "OnUpdateFileSendMail 方法"
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 中的 MAPI 支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 提供支援 Microsoft 訊息應用程式 Interface \(MAPI\) 的子集在類別 **CDocument**的。  具體來說， **CDocument** 會判斷的成員函式郵件支援是否出現在使用者的電腦，然後，如果有，則讓標準命令 ID 是 **ID\_FILE\_SEND\_MAIL**的傳送郵件命令。  這個命令的 MFC 處理函式允許使用者透過電子郵件傳送文件。  
  
> [!TIP]
>  雖然 MFC 不封裝整個 MAPI 函式集，您可以直接仍會呼叫 MAPI 函式，就可以呼叫 Win32 API 函式直接從 MFC 程式。  
  
 提供在應用程式中傳送郵件命令是非常容易。  MFC 提供實作包裝資料 \(即 **CDocument**衍生物件\) 做為附件及傳送為郵件。  這個附件與儲存的檔案儲存命令相當於 \(序列化\) 文件的內容至郵件訊息。  這個實作需要使用者電腦的郵件用戶端讓使用者有機會處理郵件和加入主旨和訊息文字至郵件訊息。  使用者看到熟悉的郵件應用程式的使用者介面。  兩個 **CDocument** 成員函式提供這項功能: `OnFileSendMail` 和 `OnUpdateFileSendMail`。  
  
 MAPI 需要讀取傳送檔案附件。  如果應用程式保持其資料檔案開啟在 `OnFileSendMail` 函式呼叫期間，檔案需要開啟在允許多個處理序存取的檔案共用模式。  
  
> [!NOTE]
>  `OnFileSendMail` 表示要覆寫版本類別的 `COleDocument` 正確處理複合文件。  
  
#### 若要實作傳送郵件命令與 MFC  
  
1.  使用 Visual C\+\+ 功能表編輯器加入命令 ID 是 **ID\_FILE\_SEND\_MAIL**的功能表項目。  
  
     這個命令 ID 是由 AFXRES.H. 的框架提供。  命令可以加入至任何功能表，不過，通常會加入至檔案功能表。  
  
2.  請手動將下列加入至文件的訊息對應:  
  
     [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/CPP/mapi-support-in-mfc_1.cpp)]  
  
    > [!NOTE]
    >  這個訊息對應為從 **CDocument** 或 **COleDocument** 衍生的文件運作—它仍會正確的基底類別，因此，即使訊息對應至衍生的資料類別。  
  
3.  建置您的應用程式。  
  
 如果郵件支援可用， MFC 啟用與 `OnUpdateFileSendMail` 的功能表項目和後續處理與 `OnFileSendMail`的命令。  如果郵件支援可用， MFC 會自動將您的功能表項目，讓使用者不會看到它。  
  
> [!TIP]
>  而非如前所述手動加入訊息對應項目，您可以使用類別屬性視窗將訊息傳遞至函式。  如需詳細資訊，請參閱[將訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md)。  
  
 如需相關資訊，請參閱 [MAPI](../mfc/mapi.md) 概觀。  
  
 如需啟用 MAPI **CDocument** 的成員函式的詳細資訊，請參閱:  
  
-   [CDocument::OnFileSendMail](../Topic/CDocument::OnFileSendMail.md)  
  
-   [CDocument::OnUpdateFileSendMail](../Topic/CDocument::OnUpdateFileSendMail.md)  
  
-   [COleDocument::OnFileSendMail](../Topic/COleDocument::OnFileSendMail.md)  
  
## 請參閱  
 [MAPI](../mfc/mapi.md)