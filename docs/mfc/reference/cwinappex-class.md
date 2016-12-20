---
title: "CWinAppEx Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinAppEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinAppEx class"
ms.assetid: a3d3e053-3e22-463f-9444-c73abb1bb9d7
caps.latest.revision: 37
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWinAppEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CWinAppEx` 管理應用程式狀態，儲存狀態至登錄，從登錄載入狀態，初始化應用程式管理器，並提供這些相同應用程式管理員。  
  
## 語法  
  
```  
class CWinAppEx : public CWinApp  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CWinAppEx::CWinAppEx](../Topic/CWinAppEx::CWinAppEx.md)|建構 `CWinAppEx` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CWinAppEx::CleanState](../Topic/CWinAppEx::CleanState.md)|從 Windows 登錄移除應用程式的相關資訊。|  
|[CWinAppEx::EnableLoadWindowPlacement](../Topic/CWinAppEx::EnableLoadWindowPlacement.md)|指定應用程式是否要從登錄載入主框架視窗的初始大小和位置。|  
|[CWinAppEx::EnableTearOffMenus](../Topic/CWinAppEx::EnableTearOffMenus.md)|啟用 Tear\-Off 應用程式的功能表。|  
|[CWinAppEx::EnableUserTools](../Topic/CWinAppEx::EnableUserTools.md)|讓使用者能夠在應用程式中的自訂命令。|  
|[CWinAppEx::ExitInstance](../Topic/CWinAppEx::ExitInstance.md)|呼叫框架從 `Run` 成員函式內關閉應用程式的執行個體。  \(覆寫 [CWinApp::ExitInstance](../Topic/CWinApp::ExitInstance.md)\)。|  
|[CWinAppEx::GetBinary](../Topic/CWinAppEx::GetBinary.md)|讀取與指定的登錄值的二進位資料。|  
|[CWinAppEx::GetContextMenuManager](../Topic/CWinAppEx::GetContextMenuManager.md)|傳回指向全域 [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) 物件。|  
|[CWinAppEx::GetDataVersion](../Topic/CWinAppEx::GetDataVersion.md)||  
|[CWinAppEx::GetDataVersionMajor](../Topic/CWinAppEx::GetDataVersionMajor.md)|傳回在 Windows 登錄中儲存應用程式的主要版本。|  
|[CWinAppEx::GetDataVersionMinor](../Topic/CWinAppEx::GetDataVersionMinor.md)|傳回在 Windows 登錄中儲存應用程式的次要版本。|  
|[CWinAppEx::GetInt](../Topic/CWinAppEx::GetInt.md)|讀取與從登錄中所指定的資料。|  
|[CWinAppEx::GetKeyboardManager](../Topic/CWinAppEx::GetKeyboardManager.md)|傳回指向全域 [CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md) 物件。|  
|[CWinAppEx::GetMouseManager](../Topic/CWinAppEx::GetMouseManager.md)|傳回指向全域 [CMouseManager](../../mfc/reference/cmousemanager-class.md) 物件。|  
|[CWinAppEx::GetObject](../Topic/CWinAppEx::GetObject.md)|讀取 `CObject`\-與從登錄中指定的衍生資料。|  
|[CWinAppEx::GetRegSectionPath](../Topic/CWinAppEx::GetRegSectionPath.md)|傳回與登錄機碼路徑的字串。  這個路徑串連具有應用程式路徑中提供的相對路徑。|  
|[CWinAppEx::GetRegistryBase](../Topic/CWinAppEx::GetRegistryBase.md)|傳回應用程式的登錄路徑。|  
|[CWinAppEx::GetSectionBinary](../Topic/CWinAppEx::GetSectionBinary.md)|讀取與指定之索引鍵和值是從註冊的二進位資料。|  
|[CWinAppEx::GetSectionInt](../Topic/CWinAppEx::GetSectionInt.md)|從登錄讀取資料是否與指定的索引鍵和值。|  
|[CWinAppEx::GetSectionObject](../Topic/CWinAppEx::GetSectionObject.md)|讀取與指定之索引鍵和值是從註冊的 `CObject` 資料。|  
|[CWinAppEx::GetSectionString](../Topic/CWinAppEx::GetSectionString.md)|讀取與指定之索引鍵和值是從註冊的字串資料。|  
|[CWinAppEx::GetShellManager](../Topic/CWinAppEx::GetShellManager.md)|傳回指向全域 [CShellManager](../../mfc/reference/cshellmanager-class.md) 物件。|  
|[CWinAppEx::GetString](../Topic/CWinAppEx::GetString.md)|讀取與已註冊之指定的字串資料。|  
|[CWinAppEx::GetTooltipManager](../Topic/CWinAppEx::GetTooltipManager.md)|傳回指向全域 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) 物件。|  
|[CWinAppEx::GetUserToolsManager](../Topic/CWinAppEx::GetUserToolsManager.md)|傳回指向全域 [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md) 物件。|  
|[CWinAppEx::InitContextMenuManager](../Topic/CWinAppEx::InitContextMenuManager.md)|初始化 `CContextMenuManager` 物件。|  
|[CWinAppEx::InitKeyboardManager](../Topic/CWinAppEx::InitKeyboardManager.md)|初始化 `CKeyboardManager` 物件。|  
|[CWinAppEx::InitMouseManager](../Topic/CWinAppEx::InitMouseManager.md)|初始化 `CMouseManager` 物件。|  
|[CWinAppEx::InitShellManager](../Topic/CWinAppEx::InitShellManager.md)|初始化類別 `CShellManager`|  
|[CWinAppEx::InitTooltipManager](../Topic/CWinAppEx::InitTooltipManager.md)|初始化 `CTooltipManager` 類別。|  
|[CWinAppEx::IsResourceSmartUpdate](../Topic/CWinAppEx::IsResourceSmartUpdate.md)||  
|[CWinAppEx::IsStateExists](../Topic/CWinAppEx::IsStateExists.md)|指出指定的按鍵是否為已註冊。|  
|[CWinAppEx::LoadState](../Topic/CWinAppEx::LoadState.md)|從登錄載入應用程式狀態。|  
|[CWinAppEx::OnAppContextHelp](../Topic/CWinAppEx::OnAppContextHelp.md)|呼叫框架，在 \[**自訂**\] 對話方塊的使用者要求內容說明。|  
|[CWinAppEx::OnViewDoubleClick](../Topic/CWinAppEx::OnViewDoubleClick.md)|當使用者在應用程式中，按兩下呼叫使用者定義的命令。|  
|[CWinAppEx::OnWorkspaceIdle](../Topic/CWinAppEx::OnWorkspaceIdle.md)||  
|[CWinAppEx::SaveState](../Topic/CWinAppEx::SaveState.md)|寫入 Windows 登錄的應用程式架構的狀態。|  
|[CWinAppEx::SetRegistryBase](../Topic/CWinAppEx::SetRegistryBase.md)|設定預設登錄機碼的路徑。  這個金鑰是用來做為支援所有後續登錄呼叫服務。|  
|[CWinAppEx::ShowPopupMenu](../Topic/CWinAppEx::ShowPopupMenu.md)|顯示快顯功能表。|  
|[CWinAppEx::WriteBinary](../Topic/CWinAppEx::WriteBinary.md)|將指定的登錄值寫入二進位資料。|  
|[CWinAppEx::WriteInt](../Topic/CWinAppEx::WriteInt.md)|將指定的登錄值寫入資料。|  
|[CWinAppEx::WriteObject](../Topic/CWinAppEx::WriteObject.md)|將 [CObject Class](../../mfc/reference/cobject-class.md) 衍生至指定的登錄值的資料。|  
|[CWinAppEx::WriteSectionBinary](../Topic/CWinAppEx::WriteSectionBinary.md)|將指定的登錄機碼的值寫入二進位資料。|  
|[CWinAppEx::WriteSectionInt](../Topic/CWinAppEx::WriteSectionInt.md)|將指定的登錄機碼的值寫入資料。|  
|[CWinAppEx::WriteSectionObject](../Topic/CWinAppEx::WriteSectionObject.md)|從衍生的 `CObject` 寫入資料類別為指定的登錄機碼的值。|  
|[CWinAppEx::WriteSectionString](../Topic/CWinAppEx::WriteSectionString.md)|將指定的登錄機碼的值寫入字串資料。|  
|[CWinAppEx::WriteString](../Topic/CWinAppEx::WriteString.md)|將指定的登錄值寫入字串資料。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CWinAppEx::LoadCustomState](../Topic/CWinAppEx::LoadCustomState.md)|呼叫框架，在應用程式狀態載入。|  
|[CWinAppEx::LoadWindowPlacement](../Topic/CWinAppEx::LoadWindowPlacement.md)|呼叫框架，當從登錄載入應用程式的大小和位置。  載入資料時包含主要畫面格的大小和位置的關閉您的應用程式時。|  
|[CWinAppEx::OnClosingMainFrame](../Topic/CWinAppEx::OnClosingMainFrame.md)|呼叫框架，其在框架視窗 \(Main Frame Window\) 處理 `WM_CLOSE`。|  
|[CWinAppEx::PreLoadState](../Topic/CWinAppEx::PreLoadState.md)|呼叫以在應用程式狀態之前的框架中載入。|  
|[CWinAppEx::PreSaveState](../Topic/CWinAppEx::PreSaveState.md)|呼叫以在應用程式狀態之前的框架中。|  
|[CWinAppEx::ReloadWindowPlacement](../Topic/CWinAppEx::ReloadWindowPlacement.md)|重新載入提供的視窗的大小和位置從登錄中|  
|[CWinAppEx::SaveCustomState](../Topic/CWinAppEx::SaveCustomState.md)|呼叫框架，則會對登錄之後寫入應用程式狀態。|  
|[CWinAppEx::StoreWindowPlacement](../Topic/CWinAppEx::StoreWindowPlacement.md)|呼叫框架寫入登錄主要畫面格的大小和位置。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CWinAppEx::m\_bForceImageReset](../Topic/CWinAppEx::m_bForceImageReset.md)|指定架構是否會重設所有工具列影像，當包含工具列的框架視窗載入。|  
  
## 備註  
 MFC 架構所提供的許多功能取決於 `CWinAppEx` 類別。  您可以用兩種方式來合併 `CWinAppEx` 類別加入至您的應用程式:  
  
-   建構在主執行緒上 `CWinAppEx` 類別。  
  
-   從 `CWinAppEx`衍生自主應用程式類別。  
  
 當您合併 `CWinAppEx` 加入至您的應用程式之後，您可以使用任何一種應用程式管理員。  在您使用一個應用程式管理器之前，您必須呼叫適當初始化其初始設定方法。  若要取得指標對於特定處理常式中，呼叫關聯的取得方法。  `CWinAppEx` 類別處理下列應用程式處理常式: [CMouseManager Class](../../mfc/reference/cmousemanager-class.md)、 [CContextMenuManager Class](../../mfc/reference/ccontextmenumanager-class.md)、 [CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md)、 [CUserToolsManager Class](../../mfc/reference/cusertoolsmanager-class.md)和 [CMenuTearOffManager Class](../../mfc/reference/cmenutearoffmanager-class.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 [CWinApp](../../mfc/reference/cwinapp-class.md)  
  
 [CWinAppEx](../../mfc/reference/cwinappex-class.md)  
  
## 需求  
 **標題:** afxwinappex.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)   
 [CMouseManager Class](../../mfc/reference/cmousemanager-class.md)   
 [CContextMenuManager Class](../../mfc/reference/ccontextmenumanager-class.md)   
 [CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md)   
 [CUserToolsManager Class](../../mfc/reference/cusertoolsmanager-class.md)