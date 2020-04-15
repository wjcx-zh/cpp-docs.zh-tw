---
title: 容器：進階功能
ms.date: 11/04/2016
helpviewer_keywords:
- links [MFC], to embedded OLE objects
- containers [MFC], links to embedded OLE objects
- containers [MFC], advanced features
- container/server applications [MFC]
- embedded objects [MFC]
- OLE controls [MFC], containers
- OLE containers [MFC], advanced features
- server/container applications [MFC]
- containers [MFC], container applications
ms.assetid: 221fd99c-b138-40fa-ad6a-974e3b3ad1f8
ms.openlocfilehash: cf130bf8dead5c59548821658b979785c4d54726
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376488"
---
# <a name="containers-advanced-features"></a>容器：進階功能

本文描述將選擇性進階功能合併至現有容器應用程式中的必要步驟。 這些功能包括：

- [同時為容器和伺服器的應用程式](#_core_creating_a_container_server_application)

- [內嵌物件的 OLE 連結](#_core_links_to_embedded_objects)

## <a name="creating-a-containerserver-application"></a><a name="_core_creating_a_container_server_application"></a>建立容器/伺服器應用程式

容器/伺服器應用程式是可同時做為容器和伺服器的應用程式。 Microsoft Word for Windows 就是這種應用程式的範例。 您可以將 Word for Windows 文件內嵌於其他應用程式中，也可以在 Word for Windows 文件中內嵌項目。 將您的容器應用程式修改成可同時做為容器和完整伺服器的程序 (您無法建立容器/迷你伺服器應用程式的組合)，類似建立完整伺服器的程序。

文章[「伺服器:實現伺服器](../mfc/servers-implementing-a-server.md)」列出了實現伺服器應用程式所需的許多任務。 如果您將容器應用程式轉換成容器/伺服器應用程式，則需要執行一些相同的工作，將程式碼加入至容器。 以下列出一些重要的考量：

- 應用程式精靈所建立的容器程式碼已初始化 OLE 子系統。 您不需要變更或加入任何提供支援的項目。

- 只要文件類別的基底類別是 `COleDocument`，就將基底類別變更為 `COleServerDoc`。

- 覆寫 `COleClientItem::CanActivate`，避免正在使用伺服器就地編輯時編輯項目。

   例如,MFC OLE 範例[OCLIENT](../overview/visual-cpp-samples.md)嵌入由容器/伺服器應用程式創建的項。 您開啟 OCLIENT 應用程式，並且就地編輯您的容器/伺服器應用程式所建立的項目。 編輯應用程式的專案時,您決定要嵌入由 MFC OLE 範例[HIERSVR](../overview/visual-cpp-samples.md)創建的項。 若要這樣做，就無法使用就地啟用。 您必須完全開啟 HIERSVR 才能啟用這個項目。 因為 MFC 程式庫不支援這項 OLE 功能，因此覆寫 `COleClientItem::CanActivate` 可讓您檢查是否有這種情況，並防止應用程式中出現可能的執行階段錯誤。

如果您要建立新的應用程式，並且希望將它當做容器/伺服器應用程式執行，請在應用程式精靈的 [OLE 選項] 對話方塊中選擇該選項，如此就會自動建立這項支援。 有關詳細資訊,請參閱文章[概述:創建 ActiveX 控制件容器](../mfc/reference/creating-an-mfc-activex-control-container.md)。 有關 MFC 樣品的資訊,請參閱[MFC 樣品](../overview/visual-cpp-samples.md#mfc-samples)。

請注意，您無法將 MDI 應用程式插入至本身。 做為容器/伺服器的應用程式無法插入至本身，除非它是 SDI 應用程式。

## <a name="links-to-embedded-objects"></a><a name="_core_links_to_embedded_objects"></a>指向嵌入物件的連結

[內嵌物件的連結] 功能可讓使用者建立包含容器應用程式內部內嵌物件之 OLE 連結的文件。 例如，在文書處理器中建立包含內嵌試算表的文件。 如果您的應用程式支援內嵌物件連結，就可以將連結貼入文書處理器文件中包含的試算表內。 這項功能可讓您的應用程式使用試算表中包含的資訊，而不需要知道文書處理器從哪裡取得該資訊。

#### <a name="to-link-to-embedded-objects-in-your-application"></a>連結至應用程式中的內嵌物件

1. 從 `COleLinkingDoc` 衍生您的文件類別，而不要從 `COleDocument` 衍生。

1. 使用 OLE 開發工具附帶的類 ID 生成器為應用程式創建 OLE 類 ID **(CLSID)。**

1. 在 OLE 中註冊應用程式。

1. 建立 `COleTemplateServer` 物件做為應用程式類別的成員。

1. 在您的應用程式類別的 `InitInstance` 成員函式中，執行下列動作：

   - 藉由呼叫物件的 `COleTemplateServer` 成員函式，將 `ConnectTemplate` 物件連接至您的文件範本。

   - 調用`COleTemplateServer::RegisterAll`成員函數以將所有類物件註冊到 OLE 系統。

   - 呼叫 `COleTemplateServer::UpdateRegistry`。 如果應用程式未使用`UpdateRegistry`「/嵌入式」開關啟動,則應*OAT_CONTAINER*唯一參數。 這樣會將應用程式註冊為可支援內嵌物件連結的容器。

      如果應用程式啟動時帶有 "/Embedded" 參數，則不應該顯示其主視窗，就像伺服器應用程式一樣。

MFC OLE 範例[OCLIENT](../overview/visual-cpp-samples.md)實現了此功能。 有關如何完成此操作的範例,請參閱`InitInstance`*OCLIENT 中的函數。* 此示例應用程式的 CPP 檔。

## <a name="see-also"></a>另請參閱

[容器](../mfc/containers.md)<br/>
[伺服器](../mfc/servers.md)
