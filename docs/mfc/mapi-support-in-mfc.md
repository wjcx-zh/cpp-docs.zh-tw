---
title: MFC 中的 MAPI 支援
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, MAPI support
- MAPI support in MFC
- CDocument class [MFC], and MAPI
- OnUpdateFileSendMail method [MFC]
- MAPI, MFC
- OnFileSendMail method [MFC]
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
ms.openlocfilehash: 7eff22b2a7b4c838f2967fb5217b9dec96903d0e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625574"
---
# <a name="mapi-support-in-mfc"></a>MFC 中的 MAPI 支援

MFC 提供類別中 Microsoft 訊息應用程式介面（MAPI）子集的支援 `CDocument` 。 具體而言， `CDocument` 有成員函式可判斷使用者電腦上是否有郵件支援，若是如此，請啟用其標準命令識別碼為 ID_FILE_SEND_MAIL 的傳送郵件命令。 此命令的 MFC 處理常式函式可讓使用者透過電子郵件傳送檔。

> [!TIP]
> 雖然 MFC 不會封裝整個 MAPI 函數集，但您仍然可以直接呼叫 MAPI 函式，就像您可以直接從 MFC 程式呼叫 WIN32 API 函式一樣。

在您的應用程式中提供 [傳送郵件] 命令非常簡單。 MFC 提供了將檔（也就是 `CDocument` 衍生的物件）封裝成附件，並以 mail 的形式傳送的執行。 這個附件相當於 [檔案] [儲存] 命令，可將檔的內容儲存（序列化）至郵件訊息。 這個執行會在使用者電腦上的郵件用戶端上呼叫，讓使用者有機會處理郵件，並將主旨和郵件內文新增到郵件訊息中。 使用者會看到他們熟悉的郵件應用程式使用者介面。 這項功能是由兩個成員函式所提供 `CDocument` ： `OnFileSendMail` 和 `OnUpdateFileSendMail` 。

MAPI 必須讀取檔案，才能傳送附件。 如果應用程式在函式呼叫期間讓其資料檔保持開啟，檔案就必須以 `OnFileSendMail` 共用模式開啟，讓多個進程能夠存取該檔案。

> [!NOTE]
> 適用于類別的覆寫版本會 `OnFileSendMail` `COleDocument` 正確地處理複合檔案。

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>使用 MFC 來執行傳送郵件命令

1. 使用 [Visual C++] 功能表編輯器，新增其命令識別碼為 ID_FILE_SEND_MAIL 的功能表項目。

   此命令識別碼是由 AFXRES.H 中的架構提供。H. 命令可以新增至任何功能表，但通常會新增**至 [檔案**] 功能表。

1. 以手動方式將下列內容新增至檔的訊息對應：

   [!code-cpp[NVC_MFCDocView#9](codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  這個訊息對應適用于衍生自或的檔 `CDocument` ， `COleDocument` 即使訊息對應是在您的衍生檔類別中，它還是會在任一情況下收取正確的基類。

1. 建立您的應用程式。

如果有可用的郵件支援，MFC 會啟用您的功能表項目， `OnUpdateFileSendMail` 並接著使用來處理命令 `OnFileSendMail` 。 如果無法使用郵件支援，MFC 會自動移除您的功能表項目，讓使用者看不到它。

> [!TIP]
> 您可以使用類別[類別 Wizard](reference/mfc-class-wizard.md)將訊息對應至函式，而不像先前所述手動新增訊息對應專案。 如需詳細資訊，請參閱[將訊息對應至](reference/mapping-messages-to-functions.md)函式。

如需相關資訊，請參閱[MAPI](mapi.md)總覽。

如需啟用 MAPI 之成員函式的詳細資訊 `CDocument` ，請參閱：

- [CDocument：： OnFileSendMail](reference/cdocument-class.md#onfilesendmail)

- [CDocument：： OnUpdateFileSendMail](reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument：： OnFileSendMail](reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>另請參閱

[MAPI](mapi.md)
