---
title: "在 MFC 的 MAPI 支援 |Microsoft 文件"
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
- MFC, MAPI support
- MAPI support in MFC
- CDocument class [MFC], and MAPI
- OnUpdateFileSendMail method [MFC]
- MAPI, MFC
- OnFileSendMail method [MFC]
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a6cc1670559354628127729724300399d5f003ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mapi-support-in-mfc"></a>MFC 中的 MAPI 支援
MFC 提供支援的 Microsoft 訊息應用程式介面 (MAPI) 類別中的子集**CDocument**。 具體來說， **CDocument**了郵件支援是否存在於使用者的電腦上的成員函式，如果是，允許標準命令 ID 是一個傳送郵件命令**ID_FILE_SEND_MAIL**. MFC 處理常式函式，此命令可讓使用者透過電子郵件將文件傳送。  
  
> [!TIP]
>  雖然 MFC 不會封裝整個 MAPI 函數集，您可以仍然呼叫 MAPI 函式直接，只需時，就可以直接從 MFC 程式中呼叫 Win32 API 函式。  
  
 提供 「 傳送郵件應用程式中的命令是非常簡單。 MFC 提供封裝文件的實作 (亦即**CDocument**-衍生物件) 做為附件和傳送郵件。 此附件相當於將儲存的檔案儲存命令 （序列化） 至郵件訊息的文件的內容。 此實作會呼叫使用者的電腦上讓使用者有機會處理郵件，並新增至郵件訊息的主旨和訊息文字的郵件用戶端。 使用者會看到其熟悉的郵件應用程式的使用者介面。 這項功能由兩個提供**CDocument**成員函式：`OnFileSendMail`和`OnUpdateFileSendMail`。  
  
 MAPI 需要讀取要傳送附件的檔案。 如果應用程式保持其資料檔案為開啟狀態期間`OnFileSendMail`函式呼叫，必須以允許多個處理程序存取檔案共用模式開啟檔案。  
  
> [!NOTE]
>  覆寫版本的`OnFileSendMail`類別`COleDocument`控點正確複合文件。  
  
#### <a name="to-implement-a-send-mail-command-with-mfc"></a>實作傳送郵件命令與 MFC  
  
1.  若要加入功能表項目的命令 ID 是使用 Visual c + + 功能表編輯器**ID_FILE_SEND_MAIL**。  
  
     此命令 ID 是由的 framework AFXRES 中提供。H. 這個命令可以加入任何功能表上，但它通常會加入至**檔案**功能表。  
  
2.  手動新增下列文件的訊息對應至：  
  
     [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]  
  
    > [!NOTE]
    >  此訊息對應適用於文件，從其中衍生**CDocument**或**COleDocument** — 它挑選正確的基底類別，在任一情況下，即使是衍生的文件類別中的訊息對應。  
  
3.  建置您的應用程式。  
  
 如果 mail 支援功能，MFC 可讓您的功能表項目與`OnUpdateFileSendMail`及後續處理命令並搭配`OnFileSendMail`。 如果找不到郵件支援，MFC 將會自動移除您的功能表項目，使用者將不會看到它。  
  
> [!TIP]
>  而不是以手動方式新增訊息對應項目，如先前所述，您可以使用類別的 [屬性] 視窗，將訊息對應到函式。 如需詳細資訊，請參閱[訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md)。  
  
 如需相關資訊，請參閱[MAPI](../mfc/mapi.md)概觀。  
  
 如需有關**CDocument**成員函式可讓 MAPI，請參閱：  
  
-   [CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)  
  
-   [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)  
  
-   [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)  
  
## <a name="see-also"></a>請參閱  
 [MAPI](../mfc/mapi.md)

