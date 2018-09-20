---
title: 伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE server applications [MFC]
- OLE server applications [MFC], activation
- full-server
- servers
- mini-server
- OLE server applications [MFC], server types
- server applications [MFC]
ms.assetid: e45172e8-eae3-400a-8139-0fa009a42fdc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dee0fd14e2e2d87155bfafefca6fa17e1d77135f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375381"
---
# <a name="servers"></a>伺服器

伺服器應用程式 （或元件應用程式） 建立 OLE 項目 （或元件） 供容器應用程式。 視覺化編輯伺服器應用程式也支援視覺化編輯或就地啟用。 是 OLE 伺服器的另一種[automation 伺服程式](../mfc/automation-servers.md)。 某些伺服器應用程式支援只建立內嵌項目;有些則可支援建立內嵌和連結的項目。 部分支援的連結，雖然這個狀況非常罕見。 所有伺服器應用程式必須都支援啟動容器應用程式，當使用者想要編輯的項目。 應用程式可以同時為容器和伺服器。 換句話說，它可以同時將資料合併到其文件，並建立可以做為項目合併到其他應用程式的文件的資料。

迷你伺服程式是一種特殊的伺服器應用程式，只能由容器啟動。 Microsoft 繪製和 Microsoft Graph 是迷你伺服程式的範例。 迷你伺服程式不會儲存為檔案在磁碟上的文件。 相反地，它會讀取來自其文件，並寫入屬於容器的文件中的項目。 如此一來，miniserver 支援內嵌，不連結。

完整的伺服器可以執行為獨立的應用程式，或啟動容器應用程式。 完整的伺服器可以將文件儲存在磁碟上的檔案。 它可以支援內嵌，這兩個內嵌和連結，或只連結。 容器應用程式的使用者可以選擇剪下 或 複製 命令在伺服器和容器中的 貼上 命令，以建立內嵌項目。 選擇容器中的伺服器中的 複製 命令並貼上連結 命令建立連結的項目。 或者，使用者可以建立使用 [插入物件] 對話方塊中的內嵌或連結項目。

下表摘要說明不同類型的伺服器的特性：

### <a name="server-characteristics"></a>伺服器特性

|伺服器類型|支援多個執行個體|每個文件的項目|每個執行個體的文件|
|--------------------|---------------------------------|------------------------|----------------------------|
|迷你伺服程式|是|1|1|
|SDI 完整伺服器|是|1 (如果支援連結，1 個以上)|1|
|MDI 完整伺服器|否 （非必要）|1 (如果支援連結，1 個以上)|0 或更多|

伺服器應用程式應該同時支援多個容器的多個容器將會用來編輯內嵌或連結項目。 如果伺服器是 SDI 應用程式 （或與對話方塊介面 miniserver），則必須能夠同時執行多個伺服器執行個體。 這可讓應用程式處理每個容器要求的個別執行個體。

如果伺服器是 MDI 應用程式，它可以在每次需要編輯項目容器時建立新的 MDI 子視窗。 如此一來，在應用程式的單一執行個體可以支援多個容器。

您的伺服器應用程式必須如果一個伺服器執行個體已在執行另一個容器要求其服務時該怎麼辦通知 OLE 系統 Dll： 是否應該啟動之伺服器的新執行個體或所有的容器將要求導向到一個執行個體伺服器。

如需伺服器的詳細資訊，請參閱：

- [伺服器：實作伺服器](../mfc/servers-implementing-a-server.md)

- [伺服器：實作伺服器文件](../mfc/servers-implementing-server-documents.md)

- [伺服器：實作就地編輯框架視窗](../mfc/servers-implementing-in-place-frame-windows.md)

- [伺服器：伺服器項目](../mfc/servers-server-items.md)

- [伺服器：使用者介面問題](../mfc/servers-user-interface-issues.md)

## <a name="see-also"></a>另請參閱

[OLE](../mfc/ole-in-mfc.md)<br/>
[容器](../mfc/containers.md)<br/>
[容器：進階功能](../mfc/containers-advanced-features.md)<br/>
[功能表和資源 (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[註冊](../mfc/registration.md)<br/>
[Automation 伺服程式](../mfc/automation-servers.md)

