---
title: 容器：實作容器
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
ms.openlocfilehash: 0ba8d4aea6b69fdbfeedfba59449d0d30433eb94
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623219"
---
# <a name="containers-implementing-a-container"></a>容器：實作容器

本文摘要說明實作容器的程序，並指向提供詳細說明實作容器之其他文件。 它也會列出您可以實作的選擇性 OLE 功能，以及描述這些功能的文件。

#### <a name="to-prepare-your-cwinapp-derived-class"></a>若要準備您的 CWinApp 衍生類別

1. 藉由在成員函式中呼叫來初始化 OLE 程式庫 `AfxOleInit` `InitInstance` 。

1. 在 `CDocTemplate::SetContainerInfo` 中呼叫 `InitInstance`，指派當內嵌項目就地啟動時使用的功能表和快速鍵資源。 如需本主題的詳細資訊，請參閱[啟用](activation-cpp.md)。

當您使用 MFC 應用程式精靈建立容器應用程式時，這些功能會自動為您提供。 請參閱[建立 MFC EXE 程式](reference/mfc-application-wizard.md)。

#### <a name="to-prepare-your-view-class"></a>若要準備您的檢視類別

1. 藉由維護所選項目的指標或指標清單 (如果支援多重選取)，追蹤所選項目。 您的 `OnDraw` 函式必須繪製所有 OLE 項目。

1. 覆寫 `IsSelected` 以確認傳遞給它的項目目前是否已選取。

1. 執行 `OnInsertObject` 訊息處理常式，以顯示 [**插入物件**] 對話方塊。

1. 實作 `OnSetFocus` 訊息處理常式以從檢視將焦點移至就地啟動 OLE 內嵌項目。

1. 實作 `OnSize` 訊息處理常式以通知 OLE 內嵌項目，需要變更其矩形以反映它的包含檢視的大小變更。

由於這些功能的實作在應用程式之間大幅不同，應用程式精靈只提供基本實作。 您可能必須自訂這些函式，才能讓您的應用程式正常運作。 如需這項工作的範例，請參閱[容器](../overview/visual-cpp-samples.md)範例。

#### <a name="to-handle-embedded-and-linked-items"></a>若要處理內嵌和連結項目

1. 從[COleClientItem](reference/coleclientitem-class.md)衍生類別。 這個類別的物件代表已內嵌或連結至您的 OLE 文件的項目。

1. 覆寫 `OnChange` 、 `OnChangeItemPosition` 和 `OnGetItemPosition` 。 這些函式處理調整大小、定位和修改內嵌和連結項目。

應用程式精靈將會為您衍生類別，但您可能需要在前述程式 `OnChange` 的步驟2中，覆寫和其中所列的其他功能。 因為這些函式的實作每個應用程式都不同，需要對大部分的應用程式自訂基本架構實作。 如需這項工作的範例，請參閱 MFC 範例[DRAWCLI](../overview/visual-cpp-samples.md)和[CONTAINER](../overview/visual-cpp-samples.md)。

您必須將多個項目加入至容器應用程式的功能表結構以支援 OLE。 如需這些專案的詳細資訊，請參閱[功能表和資源：容器新增](menus-and-resources-container-additions.md)。

您可能也要在您的容器應用程式中支援下列某些功能：

- 於編輯內嵌項目時就地啟用。

   如需詳細資訊，請參閱[啟用](activation-cpp.md)。

- 透過從伺服器應用程式中拖放選取範圍，建立 OLE 項目。

   如需詳細資訊，請參閱[OLE 拖放](drag-and-drop-ole.md)。

- 內嵌物件或組合容器/伺服器應用程式的連結。

   如需詳細資訊，請參閱[容器： Advanced Features](containers-advanced-features.md)。

## <a name="see-also"></a>另請參閱

[容器](containers.md)<br/>
[容器：用戶端項目](containers-client-items.md)
