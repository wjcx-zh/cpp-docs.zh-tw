---
title: 伺服器 |Microsoft 文件
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
ms.openlocfilehash: 7d153d73889520deaff12b64da36567a8b9a4087
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381773"
---
# <a name="servers"></a>伺服器
伺服器應用程式 （或元件應用程式） 建立 OLE 項目 （或元件） 供容器應用程式。 視覺化編輯伺服應用程式也支援視覺化編輯或就地啟用。 OLE 伺服器的另一種是[automation 伺服程式](../mfc/automation-servers.md)。 某些伺服器應用程式支援只建立內嵌項目。其他支援內嵌和連結項目的建立。 部分支援的連結，雖然這個狀況非常罕見。 所有伺服器應用程式必須都支援啟動容器應用程式，當使用者想要編輯的項目。 應用程式可以同時為容器和伺服器。 換句話說，它可以同時將資料合併至其文件，並建立可以做為項目合併至其他應用程式的文件的資料。  
  
 迷你伺服程式是一種特殊型別的只由容器啟動的伺服器應用程式。 Microsoft 繪製和 Microsoft Graph 是迷你伺服程式的範例。 迷你伺服程式不會儲存為檔案在磁碟上的文件。 相反地，它會讀取從其文件，並將它們寫入屬於容器的文件中的項目。 如此一來，迷你伺服程式支援，內嵌不連結。  
  
 完整的伺服器可以執行為獨立的應用程式，或由容器應用程式啟動。 完整的伺服器可以將文件儲存為磁碟上的檔案。 它可以支援內嵌，這兩個內嵌和連結，或只連結。 容器應用程式的使用者可以選擇在伺服器和貼上的 命令，在容器中剪下或複製命令，以建立內嵌項目。 選擇容器中的伺服器中的 [複製] 命令並貼上連結命令會建立連結的項目。 或者，使用者可以建立內嵌或連結項目使用 [插入物件] 對話方塊。  
  
 下表摘要說明不同類型的伺服器的特性：  
  
### <a name="server-characteristics"></a>伺服器的特徵  
  
|伺服器類型|支援多個執行個體|每個文件的項目|每個執行個體的文件|  
|--------------------|---------------------------------|------------------------|----------------------------|  
|迷你伺服程式|[是]|1|1|  
|SDI 完整伺服器|[是]|1 (如果支援連結 1 個以上)|1|  
|MDI 完整伺服器|否 （非必要）|1 (如果支援連結 1 個以上)|0 或更多|  
  
 伺服器應用程式應同時支援多個容器的多個容器將用來編輯內嵌或連結項目。 如果伺服器是 SDI 應用程式 （或迷你伺服程式的對話方塊介面），則必須能夠同時執行多個伺服器執行個體。 這可讓個別的執行個體的應用程式來處理每個容器的要求。  
  
 如果伺服器是 MDI 應用程式，它可以在每次需要編輯項目容器時建立新的 MDI 子視窗。 如此一來，應用程式的單一執行個體可以支援多個容器。  
  
 您的伺服器應用程式必須如果一個伺服器執行個體已在執行另一個容器要求其服務時，該怎麼辦通知 OLE 系統 Dll： 它應該啟動之伺服器的新執行個體或所有容器將要求導向到一個執行個體伺服器。  
  
 如需在伺服器上的詳細資訊，請參閱：  
  
-   [伺服器：實作伺服器](../mfc/servers-implementing-a-server.md)  
  
-   [伺服器：實作伺服器文件](../mfc/servers-implementing-server-documents.md)  
  
-   [伺服器：實作就地編輯框架視窗](../mfc/servers-implementing-in-place-frame-windows.md)  
  
-   [伺服器：伺服器項目](../mfc/servers-server-items.md)  
  
-   [伺服器：使用者介面問題](../mfc/servers-user-interface-issues.md)  
  
## <a name="see-also"></a>另請參閱  
 [OLE](../mfc/ole-in-mfc.md)   
 [容器](../mfc/containers.md)   
 [容器： 進階的功能](../mfc/containers-advanced-features.md)   
 [功能表和資源 (OLE)](../mfc/menus-and-resources-ole.md)   
 [註冊](../mfc/registration.md)   
 [Automation 伺服程式](../mfc/automation-servers.md)

