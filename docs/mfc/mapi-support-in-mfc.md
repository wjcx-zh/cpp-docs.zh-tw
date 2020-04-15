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
ms.openlocfilehash: 3024f744407cf33c8dfad8a6f7af736e0f8061ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356993"
---
# <a name="mapi-support-in-mfc"></a>MFC 中的 MAPI 支援

MFC 為`CDocument`類 中的 Microsoft 消息應用程式介面 (MAPI) 的子集提供支援。 具體而言`CDocument`,具有確定最終使用者計算機上是否存在郵件支援的成員函數,如果是,則啟用其標準命令 ID ID_FILE_SEND_MAIL的"發送郵件"命令。 此命令的 MFC 處理程式功能允許使用者透過電子郵件發送文檔。

> [!TIP]
> 儘管 MFC 不封裝整個 MAPI 函數集,您仍然可以直接調用 MAPI 函數,就像可以直接從 MFC 程式呼叫 Win32 API 函數一樣。

在應用程式中提供「發送郵件」命令非常簡單。 MFC 提供實現,將文檔`CDocument`(即派生物件)打包為附件,並將其作為郵件發送。 此附件等效於檔保存命令,該命令將文檔的內容保存到郵件中(序列化)。 此實現要求使用者電腦上的郵件客戶端為使用者提供處理郵件和向郵件添加主題和郵件文本的機會。 使用者可以看到他們熟悉的郵件應用程式的用戶介面。 此功能由兩`CDocument`個成員函數提供:`OnFileSendMail``OnUpdateFileSendMail`與 。

MAPI 需要讀取檔才能發送附件。 如果應用程式在`OnFileSendMail`函數調用期間保持其數據檔處於打開狀態,則需要使用允許多個進程訪問該檔的共用模式打開該檔。

> [!NOTE]
> `OnFileSendMail`類重寫版本`COleDocument`可正確處理復合文檔。

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>使用 MFC 實現「發送郵件」命令

1. 使用 Visual C++ 選單編輯器添加命令 ID 為ID_FILE_SEND_MAIL的功能表項。

   此命令 ID 由 AFXRES 中的框架提供。H。 該命令可以添加到任何功能表,但它通常添加到 **「檔」** 選單中。

1. 手動將以下內容加入文件的訊息映射中:

   [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  此消息映射適用於從任一或`CDocument``COleDocument`— 在任一情況下拾取正確的基類的文檔,即使消息映射位於派生的文檔類中也是如此。

1. 生成應用程式。

如果郵件支援可用,MFC 會啟用選單項目`OnUpdateFileSendMail`, 然後使用`OnFileSendMail`處理命令 。 如果郵件支援不可用,MFC 會自動刪除您的功能表項,以便使用者不會看到它。

> [!TIP]
> 您可以使用[類嚮導](reference/mfc-class-wizard.md)將消息映射到函數,而不是手動添加前面描述的消息映射條目。 有關詳細資訊,請參閱[將消息映射到函數](../mfc/reference/mapping-messages-to-functions.md)。

有關詳細資訊,請參閱[MAPI](../mfc/mapi.md)概述。

有關啟用 MAPI`CDocument`的成員函數的詳細資訊,請參閱:

- [CDocument::在檔案傳送郵件](../mfc/reference/cdocument-class.md#onfilesendmail)

- [CDocument::更新檔案傳送郵件](../mfc/reference/cdocument-class.md#onupdatefilesendmail)

- [COle 文件::在檔案傳送郵件](../mfc/reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>另請參閱

[MAPI](../mfc/mapi.md)
