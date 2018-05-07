---
title: 註冊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- servers [MFC], initializing
- initializing servers [MFC]
- OLE, registration
- installing servers [MFC]
- registry [MFC], OLE item database
- registration databases [MFC]
- servers [MFC], installing
- OLE server applications [MFC], registering servers
ms.assetid: 991d5684-72c1-4f9e-a09a-9184ed12bbb9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ab5bd34098ee1126e015e2a8368ef5b3c48fdbd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="registration"></a>註冊
當使用者要將 OLE 項目插入至應用程式時，OLE 會顯示物件類型清單以供選擇。 OLE 會從系統註冊資料庫中取得此清單，其中包含所有伺服器應用程式提供的資訊。 當伺服器註冊其本身時，其放入系統註冊資料庫的項目 (登錄) 會說明其所提供的每個物件類型、副檔名和通往的路徑，以及其他資訊。  
  
 架構和 OLE 系統動態連結程式庫 (DLL) 會使用此登錄，來決定什麼類型的 OLE 項目可在系統上使用。 當啟用連結的或內嵌的物件時，OLE 系統 DLL 也會使用此登錄，來決定如何啟動伺服器應用程式。  
  
 本文說明各個伺服器在安裝後以及每次執行時所需的應用程式。  
  
 如需系統註冊資料庫和用來更新它的.reg 檔案格式的詳細資訊，請參閱*OLE 程式設計人員參考*。  
  
##  <a name="_core_server_installation"></a> 伺服器安裝  
 當您第一次安裝您的伺服器應用程式時，應用程式應該會註冊其支援的所有 OLE 項目類型。 您也可以讓伺服器在每次作為獨立應用程式執行時，更新系統註冊資料庫。 如果伺服器的可執行檔移動的話，如此可讓系統註冊資料庫保持最新。  
  
> [!NOTE]
>  應用程式精靈產生的 MFC 應用程式在用做獨立的應用程式執行時，會自動自我註冊。  
  
 如果您想要在安裝期間註冊應用程式，請使用 RegEdit.exe 程式  如果您的應用程式中包含的安裝程式，讓安裝程式執行"RegEdit /S *appname*.reg"。 (/S 旗標表示無訊息作業，也就是說，不會顯示對話方塊報告命令成功完成)。否則，請指示使用者手動執行 RegEdit。  
  
> [!NOTE]
>  應用程式精靈建立的 .reg 檔案不包含可執行檔的完整路徑。 您的安裝程式必須將 .reg 檔案修改為包含可執行檔的完整路徑，或者將 PATH 環境變數修改為包含安裝目錄。  
  
 RegEdit 會合併 .reg 文字檔的內容至註冊資料庫。 若要驗證或修復資料庫，請使用登錄編輯程式。 請避免刪除必要的 OLE 項目   
  
##  <a name="_core_server_initialization"></a> 伺服器初始化  
 當您使用應用程式精靈建立伺服器應用程式時，精靈自動為您完成所有初始化工作。 本節說明手動撰寫伺服器應用程式時必須做的事情。  
  
 當容器應用程式啟動伺服器應用程式時，OLE 系統 DLL 會將「/Embedding」選項加入至伺服器的命令列中。 伺服器應用程式的行為會視其由容器啟動與否而有所不同，因此，應用程式開始執行時應做的第一件事就是檢查命令列的「/Embedding」或「-Embedding」選項。 如果此參數存在，請載入一組將伺服器顯示為就地啟動或完全開啟的不同資源。 如需詳細資訊，請參閱[功能表和資源： 伺服器加入](../mfc/menus-and-resources-server-additions.md)。  
  
 您的伺服器應用程式也應該呼叫其 `CWinApp::RunEmbedded` 函式來剖析命令列。 如果傳回非零的值，則應用程式不應該顯示其視窗，因為其是從容器應用程式而非獨立的應用程式執行。 此函式會更新在系統註冊資料庫中的伺服器項目，並為您呼叫 `RegisterAll` 成員函式，以執行執行個體註冊。  
  
 當您的伺服器應用程式啟動時，您必須確保應用程式可執行執行個體註冊。 執行個體註冊會通知 OLE 系統 DLL，伺服器為使用中並且準備接收來自容器的要求。 它不會將項目加入至註冊資料庫。 呼叫 `ConnectTemplate` 定義的 `COleTemplateServer` 成員函式，以執行伺服器的執行個體註冊。 這會將 `CDocTemplate` 物件連線到 `COleTemplateServer` 物件。  
  
 `ConnectTemplate`函式接受三個參數： 伺服器的**CLSID**，指標`CDocTemplate`物件和旗標，指出伺服器是否支援多個執行個體。 miniserver 必須能夠支援多個執行個體，也就是它必須能夠同時執行伺服器的多個執行個體，每個容器一個執行個體。 因此，傳遞**TRUE**啟動 miniserver 時，此旗標。  
  
 如果您要撰寫 miniserver，根據定義將始終由容器啟動。 您仍應該剖析命令列以檢查「/Embedding」選項。 這個選項不在命令列上表示使用者已嘗試啟動 miniserver 做為獨立應用程式。 如果發生這種情況，請向系統註冊資料庫註冊伺服器，然後向使用者顯示訊息方塊通知使用者，從容器應用程式啟動 miniserver。  
  
## <a name="see-also"></a>另請參閱  
 [OLE](../mfc/ole-in-mfc.md)   
 [伺服器](../mfc/servers.md)   
 [CWinApp::RunAutomated](../mfc/reference/cwinapp-class.md#runautomated)   
 [CWinApp::RunEmbedded](../mfc/reference/cwinapp-class.md#runembedded)   
 [COleTemplateServer 類別](../mfc/reference/coletemplateserver-class.md)
