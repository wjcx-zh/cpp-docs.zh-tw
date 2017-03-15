---
title: "註冊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "初始化伺服器"
  - "安裝伺服器"
  - "OLE 伺服器應用程式, 註冊伺服器"
  - "OLE, 註冊"
  - "註冊資料庫"
  - "登錄, OLE 項目資料庫"
  - "伺服器, 初始化"
  - "伺服器, 安裝"
ms.assetid: 991d5684-72c1-4f9e-a09a-9184ed12bbb9
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 註冊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當使用者要將 OLE 項目至應用程式時，建議 OLE 物件型別清單中進行選擇。  OLE 從系統註冊資料庫中取得這份清單，其中包含所有伺服器應用程式所提供的資訊。  當伺服器註冊它放入系統註冊資料庫中時，輸入 \(註冊\) 的物件，其提供副檔名和路徑的每個型別本身的，在其他資訊中。  
  
 架構和 OLE 系統動態連結程式庫 \(DLL\) 使用這個註冊決定的 OLE 項目可用的系統。  當連結或內嵌的物件啟動時，這個 OLE 系統 DLL 也使用這個註冊決定如何啟動伺服器應用程式。  
  
 本文說明每個伺服器應用程式需要，在安裝後，而且每次執行。  
  
 如需系統註冊資料庫和 .reg 檔案格式的詳細資訊用來更新它，請參閱 *OLE 程式設計人員參考*。  
  
##  <a name="_core_server_installation"></a> SQL Server 安裝  
 當您第一次安裝您的伺服器應用程式時，應該將它註冊支援 OLE 項目的所有型別。  再執行當做獨立的應用程式時，您也可以將伺服器更新系統註冊資料庫。  如果伺服器的可執行檔移動，這讓系統註冊資料庫更新。  
  
> [!NOTE]
>  當它們當做獨立的應用程式時，應用程式精靈產生的 MFC 應用程式會自動註冊。  
  
 如果您想要在安裝時登錄應用程式，請使用 RegEdit.exe 程式。\(在 Windows 95、Windows 98 和 Windows ME， RegEdit 在 Windows 目錄。  在 Windows NT 和 Windows 2000， RegEdit 在 Windows System32 目錄\)。如果包含與應用程式的安裝程式，請在安裝程式執行的 RegEdit *appname.reg*「\/S」。\(\/S 旗標表示無訊息作業，也就是說，它不會顯示報告的對話方塊命令成功完成\)。否則，請指示使用者手動執行 RegEdit。  
  
> [!NOTE]
>  應用程式精靈建立的 .reg 檔案不包含可執行檔的完整路徑。  您的安裝程式必須修改 .reg 檔案包含完整路徑到可執行檔或修改 PATH 環境變數包含安裝目錄。  
  
 RegEdit 合併 .reg 文字檔的內容至登入資料庫。  若要驗證資料庫或修復它，請使用登錄編輯程式。  請避免刪除基礎 OLE 項目。\(在 Windows 95 中， Windows 98 和 Windows ME，登錄編輯程式是 RegEdit.exe。  在 Windows NT 和 Windows 2000，它是 RegEdit32.exe\)。  
  
##  <a name="_core_server_initialization"></a> 初始化伺服器  
 當您使用應用程式精靈時的一個伺服器應用程式，精靈會自動幫您完成所有初始化工作。  本節描述您必須執行，如果您手動撰寫一個伺服器應用程式。  
  
 當伺服器應用程式由容器應用程式啟動， OLE 系統 DLL 加入至伺服器的命令列的「\/Embedding」選項。  伺服器應用程式的行為取決於它是否由容器啟動，因此，第一件事應用程式的執行，在啟動時執行檢查「\/Embedding」或「時\-在命令列使用的選項。  如果這個參數存在，請載入顯示伺服器當做是就地作用中或完全開啟的一組不同的資源。  如需詳細資訊，請參閱 [功能表和資源:伺服器加入](../mfc/menus-and-resources-server-additions.md)。  
  
 您的伺服器應用程式也應該呼叫它的 `CWinApp::RunEmbedded` 函式剖析命令列。  如果它傳回非零的值，所以應用程式不應該顯示其視窗，因為容器應用程式執行，而不是獨立的應用程式。  這個函式會在系統註冊資料庫的伺服器的輸入並呼叫您的 `RegisterAll` 成員函式，則執行個體註冊。  
  
 當您的伺服器應用程式啟動時，您必須確定它可執行執行個體註冊。  執行個體註冊通知 OLE 系統 DLL 伺服器現用和準備接收來自容器的要求。  它不會將項目加入至登入資料庫。  執行伺服器執行個體註冊呼叫 `ConnectTemplate` 成員函式定義的是 `COleTemplateServer`。  這個連接到 `COleTemplateServer` 物件的 `CDocTemplate` 物件。  
  
 `ConnectTemplate` 函式接受三個參數:伺服器的 **CLSID**、指標到 `CDocTemplate` 物件和指出伺服器是否旗標支援多個執行個體。  miniserver 一定可以支援多個執行個體，也就是說，伺服器的多個執行個體同時執行，每個容器的一定是可能的。  因此，當啟動 miniserver 時，這個旗標的傳遞 **TRUE** 。  
  
 如果您要撰寫 miniserver，它會由容器永遠根據定義啟動。  您仍應該剖析命令列檢查「\/Embedding」選項。  無法在命令列上使用這個選項表示使用者嘗試啟動 miniserver 做為獨立應用程式。  如果發生這種情況，請向系統註冊資料庫的伺服器並顯示向使用者顯示訊息方塊或從容器應用程式的 miniserver。  
  
## 請參閱  
 [OLE](../mfc/ole-in-mfc.md)   
 [伺服器](../mfc/servers.md)   
 [CWinApp::RunAutomated](../Topic/CWinApp::RunAutomated.md)   
 [CWinApp::RunEmbedded](../Topic/CWinApp::RunEmbedded.md)   
 [COleTemplateServer Class](../mfc/reference/coletemplateserver-class.md)