---
title: 容器： 實作容器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46fa8b115dd01a9ee11442a0701cd719cc6d389e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394357"
---
# <a name="containers-implementing-a-container"></a>容器：實作容器

本文摘要說明實作容器的程序，並指向提供詳細說明實作容器之其他文件。 它也會列出您可以實作的選擇性 OLE 功能，以及描述這些功能的文件。

#### <a name="to-prepare-your-cwinapp-derived-class"></a>若要準備您的 CWinApp 衍生類別

1. 呼叫以初始化 OLE 程式庫`AfxOleInit`在`InitInstance`成員函式。

1. 在 `CDocTemplate::SetContainerInfo` 中呼叫 `InitInstance`，指派當內嵌項目就地啟動時使用的功能表和快速鍵資源。 如需有關本主題的詳細資訊，請參閱 <<c0> [ 啟用](../mfc/activation-cpp.md)。

當您使用 MFC 應用程式精靈建立容器應用程式時，這些功能會自動為您提供。 請參閱[建立 MFC EXE 程式](../mfc/reference/mfc-application-wizard.md)。

#### <a name="to-prepare-your-view-class"></a>若要準備您的檢視類別

1. 藉由維護所選項目的指標或指標清單 (如果支援多重選取)，追蹤所選項目。 您的 `OnDraw` 函式必須繪製所有 OLE 項目。

1. 覆寫 `IsSelected` 以確認傳遞給它的項目目前是否已選取。

1. 實作`OnInsertObject`訊息處理常式，以顯示**插入物件** 對話方塊。

1. 實作 `OnSetFocus` 訊息處理常式以從檢視將焦點移至就地啟動 OLE 內嵌項目。

1. 實作 `OnSize` 訊息處理常式以通知 OLE 內嵌項目，需要變更其矩形以反映它的包含檢視的大小變更。

由於這些功能的實作在應用程式之間大幅不同，應用程式精靈只提供基本實作。 您可能必須自訂這些函式，才能讓您的應用程式正常運作。 這個範例，請參閱[容器](../visual-cpp-samples.md)範例。

#### <a name="to-handle-embedded-and-linked-items"></a>若要處理內嵌和連結項目

1. 衍生的類別[COleClientItem](../mfc/reference/coleclientitem-class.md)。 這個類別的物件代表已內嵌或連結至您的 OLE 文件的項目。

1. 覆寫`OnChange`， `OnChangeItemPosition`，和`OnGetItemPosition`。 這些函式處理調整大小、定位和修改內嵌和連結項目。

應用程式精靈 將衍生類別，但您可能需要覆寫`OnChange`和其他函式在之前程序中的步驟 2 一起列出。 因為這些函式的實作每個應用程式都不同，需要對大部分的應用程式自訂基本架構實作。 這個範例，請參閱 MFC 範例[DRAWCLI](../visual-cpp-samples.md)並[容器](../visual-cpp-samples.md)。

您必須將多個項目加入至容器應用程式的功能表結構以支援 OLE。 如需這些的詳細資訊，請參閱[功能表和資源： 容器新增](../mfc/menus-and-resources-container-additions.md)。

您可能也要在您的容器應用程式中支援下列某些功能：

- 於編輯內嵌項目時就地啟用。

     如需詳細資訊，請參閱 <<c0> [ 啟用](../mfc/activation-cpp.md)。

- 透過從伺服器應用程式中拖放選取範圍，建立 OLE 項目。

     如需詳細資訊，請參閱 <<c0> [ 拖放 (OLE)](../mfc/drag-and-drop-ole.md)。

- 內嵌物件或組合容器/伺服器應用程式的連結。

     如需詳細資訊，請參閱 <<c0> [ 容器： 進階功能](../mfc/containers-advanced-features.md)。

## <a name="see-also"></a>另請參閱

[容器](../mfc/containers.md)<br/>
[容器：用戶端項目](../mfc/containers-client-items.md)

