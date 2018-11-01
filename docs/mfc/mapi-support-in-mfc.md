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
ms.openlocfilehash: 564ce185758d25682a88f18a23b0b11afc84a4d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567138"
---
# <a name="mapi-support-in-mfc"></a>MFC 中的 MAPI 支援

MFC 提供的一小部分的 Microsoft 訊息應用程式介面 (MAPI) 類別中支援`CDocument`。 具體來說，`CDocument`已判斷 mail 支援是否存在於使用者的電腦上的成員函式，如果是這樣，啟用標準命令 ID 是 ID_FILE_SEND_MAIL 傳送郵件命令。 MFC 處理常式函式，此命令可讓使用者傳送電子郵件透過文件。

> [!TIP]
>  雖然 MFC 不會封裝整個 MAPI 函式集，您仍然可以呼叫 MAPI 函式直接，只需時，就可以直接從 MFC 程式中呼叫 Win32 API 函式。

提供 「 傳送郵件應用程式中的命令都不困難。 MFC 提供封裝文件的實作 (亦即`CDocument`-衍生物件) 做為附件並將它傳送為 mail。 這個附件就相當於儲存檔案的命令，來儲存 （序列化） 至郵件訊息的文件的內容。 此實作會呼叫郵件用戶端使用者的電腦上，若要授與使用者有機會處理郵件，並新增至郵件訊息的主旨和訊息文字。 使用者會看到其熟悉的郵件應用程式的使用者介面。 這項功能由兩個所提供`CDocument`成員函式：`OnFileSendMail`和`OnUpdateFileSendMail`。

MAPI 需要讀取要傳送附件的檔案。 如果應用程式保持其資料檔案為開啟狀態期間`OnFileSendMail`函式呼叫必須以可讓多個處理序存取檔案共用模式開啟檔案。

> [!NOTE]
>  覆寫的新版`OnFileSendMail`類別`COleDocument`正確處理複合文件。

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>實作傳送郵件命令與 MFC

1. 使用 Visual c + + 功能表編輯器中加入命令 ID 是 ID_FILE_SEND_MAIL 功能表項目。

   這個命令識別碼是在 AFXRES framework 所提供。H. 此命令可新增至任何功能表上，但它通常會加入至**檔案**功能表。

1. 手動加入您的文件訊息對應中加入下列內容：

   [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  此訊息對應適用於從其中衍生的文件`CDocument`或`COleDocument`— 它會取得正確的基底類別，在任一情況下，即使是在衍生的文件類別中的訊息對應。

1. 建置您的應用程式。

如果郵件的支援功能，MFC 可讓您使用的功能表項目`OnUpdateFileSendMail`與後續處理指令及`OnFileSendMail`。 如果找不到郵件支援，MFC 將會自動移除您的功能表項目讓使用者將不會看到它。

> [!TIP]
>  而不是以手動方式新增訊息對應項目，如先前所述，您可以使用類別的 [屬性] 視窗，將訊息對應至函式。 如需詳細資訊，請參閱 <<c0> [ 將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md)。

如需相關資訊，請參閱[MAPI](../mfc/mapi.md)概觀。

如需詳細資訊`CDocument`成員函式可讓 MAPI，請參閱：

- [CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)

- [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>另請參閱

[MAPI](../mfc/mapi.md)

