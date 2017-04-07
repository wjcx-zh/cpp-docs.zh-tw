---
title: "CWinAppEx 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinAppEx
- AFXWINAPPEX/CWinAppEx
- AFXWINAPPEX/CWinAppEx::CWinAppEx
- AFXWINAPPEX/CWinAppEx::CleanState
- AFXWINAPPEX/CWinAppEx::EnableLoadWindowPlacement
- AFXWINAPPEX/CWinAppEx::EnableTearOffMenus
- AFXWINAPPEX/CWinAppEx::EnableUserTools
- AFXWINAPPEX/CWinAppEx::ExitInstance
- AFXWINAPPEX/CWinAppEx::GetBinary
- AFXWINAPPEX/CWinAppEx::GetContextMenuManager
- AFXWINAPPEX/CWinAppEx::GetDataVersion
- AFXWINAPPEX/CWinAppEx::GetDataVersionMajor
- AFXWINAPPEX/CWinAppEx::GetDataVersionMinor
- AFXWINAPPEX/CWinAppEx::GetInt
- AFXWINAPPEX/CWinAppEx::GetKeyboardManager
- AFXWINAPPEX/CWinAppEx::GetMouseManager
- AFXWINAPPEX/CWinAppEx::GetObject
- AFXWINAPPEX/CWinAppEx::GetRegSectionPath
- AFXWINAPPEX/CWinAppEx::GetRegistryBase
- AFXWINAPPEX/CWinAppEx::GetSectionBinary
- AFXWINAPPEX/CWinAppEx::GetSectionInt
- AFXWINAPPEX/CWinAppEx::GetSectionObject
- AFXWINAPPEX/CWinAppEx::GetSectionString
- AFXWINAPPEX/CWinAppEx::GetShellManager
- AFXWINAPPEX/CWinAppEx::GetString
- AFXWINAPPEX/CWinAppEx::GetTooltipManager
- AFXWINAPPEX/CWinAppEx::GetUserToolsManager
- AFXWINAPPEX/CWinAppEx::InitContextMenuManager
- AFXWINAPPEX/CWinAppEx::InitKeyboardManager
- AFXWINAPPEX/CWinAppEx::InitMouseManager
- AFXWINAPPEX/CWinAppEx::InitShellManager
- AFXWINAPPEX/CWinAppEx::InitTooltipManager
- AFXWINAPPEX/CWinAppEx::IsResourceSmartUpdate
- AFXWINAPPEX/CWinAppEx::IsStateExists
- AFXWINAPPEX/CWinAppEx::LoadState
- AFXWINAPPEX/CWinAppEx::OnAppContextHelp
- AFXWINAPPEX/CWinAppEx::OnViewDoubleClick
- AFXWINAPPEX/CWinAppEx::OnWorkspaceIdle
- AFXWINAPPEX/CWinAppEx::SaveState
- AFXWINAPPEX/CWinAppEx::SetRegistryBase
- AFXWINAPPEX/CWinAppEx::ShowPopupMenu
- AFXWINAPPEX/CWinAppEx::WriteBinary
- AFXWINAPPEX/CWinAppEx::WriteInt
- AFXWINAPPEX/CWinAppEx::WriteObject
- AFXWINAPPEX/CWinAppEx::WriteSectionBinary
- AFXWINAPPEX/CWinAppEx::WriteSectionInt
- AFXWINAPPEX/CWinAppEx::WriteSectionObject
- AFXWINAPPEX/CWinAppEx::WriteSectionString
- AFXWINAPPEX/CWinAppEx::WriteString
- AFXWINAPPEX/CWinAppEx::LoadCustomState
- AFXWINAPPEX/CWinAppEx::LoadWindowPlacement
- AFXWINAPPEX/CWinAppEx::OnClosingMainFrame
- AFXWINAPPEX/CWinAppEx::PreLoadState
- AFXWINAPPEX/CWinAppEx::PreSaveState
- AFXWINAPPEX/CWinAppEx::ReloadWindowPlacement
- AFXWINAPPEX/CWinAppEx::SaveCustomState
- AFXWINAPPEX/CWinAppEx::StoreWindowPlacement
- AFXWINAPPEX/CWinAppEx::m_bForceImageReset
dev_langs:
- C++
helpviewer_keywords:
- CWinAppEx class
ms.assetid: a3d3e053-3e22-463f-9444-c73abb1bb9d7
caps.latest.revision: 37
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: b471749e1e0e2c3ed7b1d8913122c4758276e166
ms.lasthandoff: 03/31/2017

---
# <a name="cwinappex-class"></a>CWinAppEx 類別
`CWinAppEx`處理應用程式狀態、 儲存狀態至登錄、 從登錄載入狀態、 初始化應用程式管理員和提供連結，這些相同的應用程式管理員。  
  
## <a name="syntax"></a>語法  
  
```  
class CWinAppEx : public CWinApp  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CWinAppEx::CWinAppEx](#cwinappex)|建構 `CWinAppEx` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CWinAppEx::CleanState](#cleanstate)|從 Windows 登錄移除應用程式的相關資訊。|  
|[CWinAppEx::EnableLoadWindowPlacement](#enableloadwindowplacement)|指定應用程式是否會載入初始大小和主框架視窗的位置，登錄中。|  
|[CWinAppEx::EnableTearOffMenus](#enabletearoffmenus)|可讓 tear-off 功能表應用程式。|  
|[CWinAppEx::EnableUserTools](#enableusertools)|可讓使用者在應用程式中建立自訂的功能表命令。|  
|[CWinAppEx::ExitInstance](#exitinstance)|由架構呼叫從`Run`成員函式來結束應用程式的這個執行個體。 (覆寫[CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)。)|  
|[CWinAppEx::GetBinary](#getbinary)|讀取指定的登錄值相關聯的二進位資料。|  
|[CWinAppEx::GetContextMenuManager](#getcontextmenumanager)|將指標傳回至全域[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)物件。|  
|[CWinAppEx::GetDataVersion](#getdataversion)||  
|[CWinAppEx::GetDataVersionMajor](#getdataversionmajor)|傳回儲存在 Windows 登錄中的應用程式的主要版本。|  
|[CWinAppEx::GetDataVersionMinor](#getdataversionminor)|傳回儲存在 Windows 登錄中的應用程式的次要版本。|  
|[CWinAppEx::GetInt](#getint)|讀取登錄從指定的值相關聯的數值資料。|  
|[CWinAppEx::GetKeyboardManager](#getkeyboardmanager)|將指標傳回至全域[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)物件。|  
|[CWinAppEx::GetMouseManager](#getmousemanager)|將指標傳回至全域[CMouseManager](../../mfc/reference/cmousemanager-class.md)物件。|  
|[CWinAppEx::GetObject](#getobject)|讀取`CObject`-衍生從登錄指定的值相關聯的資料。|  
|[CWinAppEx::GetRegSectionPath](#getregsectionpath)|傳回的是登錄機碼路徑的字串。 此路徑會串連提供與應用程式路徑的相對路徑。|  
|[CWinAppEx::GetRegistryBase](#getregistrybase)|傳回應用程式的登錄路徑。|  
|[CWinAppEx::GetSectionBinary](#getsectionbinary)|讀取登錄值與指定之索引鍵相關聯的二進位資料。|  
|[CWinAppEx::GetSectionInt](#getsectionint)|從指定索引鍵和值相關聯的登錄讀取數值資料。|  
|[CWinAppEx::GetSectionObject](#getsectionobject)|讀取`CObject`從登錄值與指定之索引鍵相關聯的資料。|  
|[CWinAppEx::GetSectionString](#getsectionstring)|讀取字串登錄值與指定之索引鍵相關聯的資料。|  
|[CWinAppEx::GetShellManager](#getshellmanager)|將指標傳回至全域[CShellManager](../../mfc/reference/cshellmanager-class.md)物件。|  
|[CWinAppEx::GetString](#getstring)|讀取登錄從指定的值相關聯的字串資料。|  
|[CWinAppEx::GetTooltipManager](#gettooltipmanager)|將指標傳回至全域[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)物件。|  
|[CWinAppEx::GetUserToolsManager](#getusertoolsmanager)|將指標傳回至全域[CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)物件。|  
|[CWinAppEx::InitContextMenuManager](#initcontextmenumanager)|初始化`CContextMenuManager`物件。|  
|[CWinAppEx::InitKeyboardManager](#initkeyboardmanager)|初始化`CKeyboardManager`物件。|  
|[CWinAppEx::InitMouseManager](#initmousemanager)|初始化`CMouseManager`物件。|  
|[CWinAppEx::InitShellManager](#initshellmanager)|初始化`CShellManager`類別|  
|[Cwinappex:: Inittooltipmanager](#inittooltipmanager)|初始化`CTooltipManager`類別。|  
|[CWinAppEx::IsResourceSmartUpdate](#isresourcesmartupdate)||  
|[CWinAppEx::IsStateExists](#isstateexists)|指出是否在登錄中指定之索引鍵。|  
|[CWinAppEx::LoadState](#loadstate)|從登錄載入應用程式狀態。|  
|[CWinAppEx::OnAppContextHelp](#onappcontexthelp)|由架構呼叫，當使用者要求的內容說明**自訂** 對話方塊。|  
|[CWinAppEx::OnViewDoubleClick](#onviewdoubleclick)|當使用者按兩下應用程式中的任何位置，請呼叫使用者定義的命令。|  
|[CWinAppEx::OnWorkspaceIdle](#onworkspaceidle)||  
|[CWinAppEx::SaveState](#savestate)|應用程式架構的狀態寫入 Windows 登錄中。|  
|[CWinAppEx::SetRegistryBase](#setregistrybase)|設定預設的登錄機碼的路徑。 此金鑰將做為所有後續的登錄呼叫的根。|  
|[CWinAppEx::ShowPopupMenu](#showpopupmenu)|顯示快顯功能表。|  
|[CWinAppEx::WriteBinary](#writebinary)|寫入指定的登錄值的二進位資料。|  
|[CWinAppEx::WriteInt](#writeint)|寫入指定的登錄值的數值資料。|  
|[CWinAppEx::WriteObject](#writeobject)|寫入資料衍生自[CObject 類別](../../mfc/reference/cobject-class.md)為指定的登錄值。|  
|[CWinAppEx::WriteSectionBinary](#writesectionbinary)|二進位資料寫入指定的登錄機碼的值。|  
|[CWinAppEx::WriteSectionInt](#writesectionint)|數字的資料寫入指定的登錄機碼的值。|  
|[CWinAppEx::WriteSectionObject](#writesectionobject)|將衍生自資料寫入`CObject`類別將值指定的登錄機碼。|  
|[CWinAppEx::WriteSectionString](#writesectionstring)|字串資料寫入指定的登錄機碼的值。|  
|[CWinAppEx::WriteString](#writestring)|寫入指定的登錄值的字串資料。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CWinAppEx::LoadCustomState](#loadcustomstate)|在載入應用程式的狀態時由架構呼叫。|  
|[CWinAppEx::LoadWindowPlacement](#loadwindowplacement)|從登錄載入的大小和位置的應用程式時由架構呼叫。 載入的資料包含的大小和位置的主要畫面格，在您的應用程式上次關閉的時間。|  
|[CWinAppEx::OnClosingMainFrame](#onclosingmainframe)|當處理主框架視窗時，由架構呼叫`WM_CLOSE`。|  
|[CWinAppEx::PreLoadState](#preloadstate)|立即之前由架構呼叫應用程式狀態為 loaded。|  
|[CWinAppEx::PreSaveState](#presavestate)|由架構呼叫的前面會儲存應用程式狀態。|  
|[CWinAppEx::ReloadWindowPlacement](#reloadwindowplacement)|重新載入的大小和位置的登錄中提供的視窗|  
|[CWinAppEx::SaveCustomState](#savecustomstate)|應用程式狀態寫入登錄之後，由架構呼叫。|  
|[CWinAppEx::StoreWindowPlacement](#storewindowplacement)|由架構呼叫以登錄中寫入的大小和位置的主要畫面格。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CWinAppEx::m_bForceImageReset](#m_bforceimagereset)|指定是否架構將會重設所有工具列影像載入時將包含工具列的框架視窗。|  
  
## <a name="remarks"></a>備註  
 MFC 架構所提供的功能大多取決於`CWinAppEx`類別。 您可以合併`CWinAppEx`到您的應用程式中有兩種類別︰  
  
-   建構`CWinAppEx`主執行緒中的類別。  
  
-   衍生的主應用程式類別`CWinAppEx`。  
  
 您將合併之後`CWinAppEx`至您的應用程式，您可以初始化其中一個應用程式管理員。 使用應用程式管理員之前，您必須透過呼叫適當的 initialize 方法來進行初始化。 若要取得特定經理的指標，呼叫相關聯的 get 方法。 `CWinAppEx`類別會管理下列應用程式管理員︰ [CMouseManager 類別](../../mfc/reference/cmousemanager-class.md)， [CContextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)， [CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)， [CUserToolsManager 類別](../../mfc/reference/cusertoolsmanager-class.md)，和[CMenuTearOffManager 類別](../../mfc/reference/cmenutearoffmanager-class.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 [CWinApp](../../mfc/reference/cwinapp-class.md)  
  
 [CWinAppEx](../../mfc/reference/cwinappex-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxwinappex.h  
  
##  <a name="cleanstate"></a>CWinAppEx::CleanState  
 從 Windows 登錄移除應用程式的所有資訊。  
  
```  
virtual BOOL CleanState(LPCTSTR lpszSectionName=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszSectionName`  
 包含的登錄機碼路徑的字串。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果該方法成功。否則便是 0。  
  
### <a name="remarks"></a>備註  
 這個方法會清除從登錄的特定區段的應用程式資料。 您可以指定要使用參數清除區段`lpszSectionName`。 如果`lpszSectionName`是`NULL`，這個方法會使用儲存在預設登錄路徑`CWinAppEx`物件。 若要取得預設的登錄路徑，請使用[CWinAppEx::GetRegistryBase](#getregistrybase)。  
  
##  <a name="cwinappex"></a>CWinAppEx::CWinAppEx  
 建構 `CWinAppEx` 物件。  
  
```  
CWinAppEx(BOOL bResourceSmartUpdate = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bResourceSmartUpdate`  
 布林值參數，指定工作區物件是否應該偵測和處理資源更新。  
  
### <a name="remarks"></a>備註  
 `CWinAppEx`類別有初始設定方法、 提供功能來儲存及載入至登錄，應用程式資訊和控制全域應用程式設定。 它也可讓您使用全域管理員，例如[CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)和[CUserToolsManager 類別](../../mfc/reference/cusertoolsmanager-class.md)。 每個應用程式可以有只有一個執行個體`CWinAppEx`類別。  
  
##  <a name="enableloadwindowplacement"></a>CWinAppEx::EnableLoadWindowPlacement  
 指定應用程式是否會載入初始大小和主框架視窗的位置，登錄中。  
  
```  
void EnableLoadWindowPlacement(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 指定應用程式從登錄是否載入的初始大小和位置的主框架視窗。  
  
### <a name="remarks"></a>備註  
 根據預設的大小和位置的主要畫面格是從搭配其他應用程式設定的登錄載入。 期間發生此錯誤[CWinAppEx::LoadState](#loadstate)。 如果不想從登錄載入視窗的初始位置，呼叫這個方法與`bEnable`設`false`。  
  
##  <a name="enabletearoffmenus"></a>CWinAppEx::EnableTearOffMenus  
 建立並初始化[CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md)物件。  
  
```  
BOOL EnableTearOffMenus(
    LPCTSTR lpszRegEntry,  
    const UINT uiCmdFirst,  
    const UINT uiCmdLast);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszRegEntry`  
 字串，包含路徑的登錄機碼。 應用程式會使用此登錄機碼來儲存資訊 tear-off 功能表。  
  
 [in] `uiCmdFirst`  
 第一個功能表關閉終止識別碼。  
  
 [in] `uiCmdLast`  
 最後一個終止功能表識別碼。  
  
### <a name="return-value"></a>傳回值  
 `True`如果`CMenuTearOffManager`建立並初始化成功。`false`如果發生錯誤，或如果`CMenuTearOffManager`已經存在。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式來啟用應用程式中的 tear-off 功能表。 您應該呼叫此函式，從`InitInstance`。  
  
##  <a name="enableusertools"></a>CWinAppEx::EnableUserTools  
 可讓使用者建立自訂的功能表命令，這樣會降低應用程式中的按鍵輸入。 這個方法會建立[CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)物件。  
  
```  
BOOL EnableUserTools(
    const UINT uiCmdToolsDummy,  
    const UINT uiCmdFirst,  
    const UINT uiCmdLast,  
    CRuntimeClass* pToolRTC = RUNTIME_CLASS(CUserTool),  
    UINT uArgMenuID = 0,  
    UINT uInitDirMenuID = 0);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmdToolsDummy`  
 不帶正負號的整數，架構會使用預留位置做為使用者的 [工具] 功能表的命令識別碼。  
  
 [in] `uiCmdFirst`  
 第一個使用者工具命令的命令識別碼。  
  
 [in] `uiCmdLast`  
 最後一個使用者工具命令的命令識別碼。  
  
 [in] `pToolRTC`  
 類別 A`CUserToolsManager`物件會使用來建立新的使用者工具。  
  
 [in] `uArgMenuID`  
 引數功能表識別碼。  
  
 [in] `uInitDirMenuID`  
 初始工具目錄功能表識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法會建立並初始化`CUserToolsManager`物件;`FALSE`如果方法失敗，或如果`CUserToolsManager`物件已經存在。  
  
### <a name="remarks"></a>備註  
 當您啟用使用者定義的工具時，架構會自動支援自訂期間可以擴充動態功能表。 架構會將每個新的項目關聯的外部命令。 架構在使用者選取適當項目時，會叫用這些命令**工具**功能表。  
  
 每次使用者加入新項目時，framework 就會建立新的物件。 類別的新物件的類型由所定義`pToolRTC`。 `pToolRTC`類別型別必須衍生自[CUserTool 類別](../../mfc/reference/cusertool-class.md)。  
  
 如需有關使用者工具，以及如何將它們合併到您的應用程式的詳細資訊，請參閱[使用者定義工具](../../mfc/user-defined-tools.md)。  
  
##  <a name="exitinstance"></a>CWinAppEx::ExitInstance  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int ExitInstance();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getbinary"></a>CWinAppEx::GetBinary  
 從指定的登錄機碼讀取二進位資料。  
  
```  
BOOL GetBinary(
    LPCTSTR lpszEntry,  
    LPBYTE* ppData,  
    UINT* pBytes);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszEntry`  
 字串，包含的登錄機碼名稱。  
  
 [輸出] `ppData`  
 方法會以二進位資料的填滿緩衝區的指標。  
  
 [輸出] `pBytes`  
 讀取方法用來寫入的位元組數目的不帶正負號整數的指標。  
  
### <a name="return-value"></a>傳回值  
 `True`如果登錄成功。，`false`否則。  
  
### <a name="remarks"></a>備註  
 這個方法會讀取寫入登錄的二進位資料。 若要將資料寫入登錄中，使用方法[CWinAppEx::WriteBinary](#writebinary)和[CWinAppEx::WriteSectionBinary](#writesectionbinary)。  
  
 `lpszEntry`參數就是位於您的應用程式的預設登錄機碼下的登錄項目名稱。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
##  <a name="getcontextmenumanager"></a>CWinAppEx::GetContextMenuManager  
 將指標傳回至全域[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)物件。  
  
```  
CContextMenuManager* GetContextMenuManager();
```  
  
### <a name="return-value"></a>傳回值  
 指標的全域`CContextMenuManager`物件。  
  
### <a name="remarks"></a>備註  
 如果未初始化 CContextMenuManager 物件，此函數會呼叫[CWinAppEx::InitContextMenuManager](#initcontextmenumanager)它傳回的指標之前。  
  
##  <a name="getdataversion"></a>CWinAppEx::GetDataVersion  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetDataVersion() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getdataversionmajor"></a>CWinAppEx::GetDataVersionMajor  
 傳回會儲存在 Windows 登錄中，當您呼叫的應用程式的主要版本[CWinAppEx::SaveState](#savestate)。  
  
```  
int GetDataVersionMajor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 包含的主要版本號碼的整數值。  
  
##  <a name="getdataversionminor"></a>CWinAppEx::GetDataVersionMinor  
 傳回會儲存在 Windows 登錄中，當您呼叫的應用程式的次要版本[CWinAppEx::SaveState](#savestate)。  
  
```  
int GetDataVersionMinor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 包含的次要版本號碼的整數值。  
  
##  <a name="getint"></a>CWinAppEx::GetInt  
 從指定的登錄機碼讀取的整數資料。  
  
```  
int GetInt(
    LPCTSTR lpszEntry,  
    int nDefault = 0);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszEntry`  
 字串，包含名稱的登錄項目。  
  
 [in] `nDefault`  
 如果指定的登錄項目不存在該方法會傳回預設值。  
  
### <a name="return-value"></a>傳回值  
 登錄資料，如果該方法成功。否則`nDefault`。  
  
### <a name="remarks"></a>備註  
 這個方法會從登錄讀取整數資料。 如果沒有與所指定的登錄機碼相關聯的整數資料`lpszEntry`，這個方法會傳回`nDefault`。 若要將資料寫入登錄中，使用方法[CWinAppEx::WriteSectionInt](#writesectionint)和[CWinAppEx::WriteInt](#writeint)。  
  
 `lpszEntry`參數就是位於您的應用程式的預設登錄機碼下的登錄項目名稱。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
##  <a name="getkeyboardmanager"></a>CWinAppEx::GetKeyboardManager  
 將指標傳回至全域[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)物件。  
  
```  
CKeyboardManager* GetKeyboardManager();
```  
  
### <a name="return-value"></a>傳回值  
 指標的全域`CKeyboardManager`物件。  
  
### <a name="remarks"></a>備註  
 如果未初始化鍵盤管理員，此函數會呼叫[CWinAppEx::InitKeyboardManager](#initkeyboardmanager)它傳回的指標之前。  
  
##  <a name="getmousemanager"></a>CWinAppEx::GetMouseManager  
 將指標傳回至全域[CMouseManager](../../mfc/reference/cmousemanager-class.md)物件。  
  
```  
CMouseManager* GetMouseManager();
```  
  
### <a name="return-value"></a>傳回值  
 指標的全域`CMouseManager`物件。  
  
### <a name="remarks"></a>備註  
 如果未初始化滑鼠管理員、 這個函式呼叫[CWinAppEx::InitMouseManager](#initmousemanager)它傳回的指標之前。  
  
##  <a name="getobject"></a>CWinAppEx::GetObject  
 讀取[CObject](../../mfc/reference/cobject-class.md)-dervied 登錄中的資料。  
  
```  
BOOL GetObject(
    LPCTSTR lpszEntry,  
    CObject& obj);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszEntry`  
 字串，包含相對路徑的登錄項目。  
  
 [輸出] `obj`  
 若要參考`CObject`。 方法會使用這個參考來登錄資料儲存。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果該方法成功。否則便是 0。  
  
### <a name="remarks"></a>備註  
 這個方法會從衍生自的登錄讀取資料`CObject`。 要寫入`CObject`資料登錄中，使用[CWinAppEx::WriteObject](#writeobject)或[CWinAppEx::WriteSectionObject](#writesectionobject)。  
  
 `lpszEntry`參數就是位於您的應用程式的預設登錄機碼下的登錄項目名稱。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
##  <a name="getregistrybase"></a>CWinAppEx::GetRegistryBase  
 擷取應用程式的預設登錄路徑。  
  
```  
LPCTSTR GetRegistryBase();
```  
  
### <a name="return-value"></a>傳回值  
 字串，包含預設登錄位置的路徑。  
  
### <a name="remarks"></a>備註  
 所有方法[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)，存取在預設位置的登錄開始。 使用此方法以擷取預設登錄位置路徑。 使用[CWinAppEx::SetRegistryBase](#setregistrybase)若要變更預設的登錄位置。  
  
##  <a name="getregsectionpath"></a>CWinAppEx::GetRegSectionPath  
 建立並傳回登錄機碼的絕對路徑。  
  
```  
CString GetRegSectionPath(LPCTSTR szSectionAdd = _T(""));
```  
  
### <a name="parameters"></a>參數  
 [in] `szSectionAdd`  
 字串，包含相對路徑的登錄機碼。  
  
### <a name="return-value"></a>傳回值  
 A `CString` ，其中包含的登錄機碼的絕對路徑。  
  
### <a name="remarks"></a>備註  
 這個方法會藉由附加中的相對路徑定義的登錄機碼的絕對路徑`szSectionAdd`到您的應用程式的預設登錄位置。 若要取得預設的登錄機碼，請使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)。  
  
##  <a name="getsectionbinary"></a>CWinAppEx::GetSectionBinary  
 從登錄讀取二進位資料。  
  
```  
BOOL GetSectionBinary(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    LPBYTE* ppData,  
    UINT* pBytes);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszSubSection`  
 字串，包含相對路徑的登錄機碼。  
  
 [in] `lpszEntry`  
 字串，包含要讀取的值。  
  
 [輸出] `ppData`  
 方法會儲存資料緩衝區的指標。  
  
 [輸出] `pBytes`  
 不帶正負號的整數指標。 方法會寫入的大小`ppData`給這個參數。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `True`，否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會讀取登錄的方式寫入二進位資料[CWinAppEx::WriteBinary](#writebinary)和[CWinAppEx::WriteSectionBinary](#writesectionbinary)。  
  
 `lpszSubSection`參數不是絕對路徑的登錄項目。 它是相對路徑附加到您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
##  <a name="getsectionint"></a>CWinAppEx::GetSectionInt  
 從登錄讀取的整數資料。  
  
```  
int GetSectionInt(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    int nDefault = 0);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszSubSection`  
 字串，包含相對路徑的登錄機碼。  
  
 [in] `lpszEntry`  
 字串，包含要讀取的值。  
  
 [in] `nDefault`  
 要傳回如果指定的值不存在的預設值。  
  
### <a name="return-value"></a>傳回值  
 整數資料儲存在指定的登錄值。`nDefault`如果資料不存在。  
  
### <a name="remarks"></a>備註  
 使用方法[CWinAppEx::WriteInt](#writeint)和[CWinAppEx::WriteSectionInt](#writesectionint)將整數資料寫入登錄。  
  
 `lpszSubSection`參數不是絕對路徑的登錄項目。 它是相對的路徑加入至您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
##  <a name="getsectionobject"></a>CWinAppEx::GetSectionObject  
 讀取[CObject](../../mfc/reference/cobject-class.md)登錄中的登錄資料。  
  
```  
BOOL GetSectionObject(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    CObject& obj);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszSubSection`  
 字串，包含相對路徑的登錄機碼。  
  
 [in] `lpszEntry`  
 字串，包含要讀取的值。  
  
 [輸出] `obj`  
 若要參考`CObject`。 方法會使用此`CObject`登錄資料儲存。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會從登錄讀取資料。 資料讀取為`CObject`資料或衍生自的類別資料`CObject`。 要寫入`CObject`資料登錄中，使用[CWinAppEx::WriteObject](#writeobject)或[CWinAppEx::WriteSectionObject](#writesectionobject)。  
  
 `lpszSubSection`參數不是絕對路徑的登錄項目。 它是相對路徑附加到您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
##  <a name="getsectionstring"></a>CWinAppEx::GetSectionString  
 讀取字串登錄中的資料。  
  
```  
CString GetSectionString(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    LPCTSTR lpszDefault = _T(""));
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszSubSection`  
 字串，包含相對路徑的登錄機碼。  
  
 [in] `lpszEntry`  
 字串，包含要讀取的值。  
  
 [in] `lpszDefault`  
 要傳回如果指定的值不存在的預設值。  
  
### <a name="return-value"></a>傳回值  
 如果資料存在時，儲存在指定的登錄值中的字串資料否則`lpszDefault`。  
  
### <a name="remarks"></a>備註  
 這個方法會讀取寫入登錄的字串資料。 使用[CWinAppEx::WriteString](#writestring)和[CWinAppEx::WriteSectionString](#writesectionstring)將字串資料寫入登錄。  
  
 `lpszSubSection`參數不是絕對路徑的登錄項目。 它是相對路徑附加到您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
##  <a name="getshellmanager"></a>CWinAppEx::GetShellManager  
 將指標傳回至全域[CShellManager](../../mfc/reference/cshellmanager-class.md)物件。  
  
```  
CShellManager* GetShellManager();
```  
  
### <a name="return-value"></a>傳回值  
 指標的全域`CShellManager`物件。  
  
### <a name="remarks"></a>備註  
 如果`CShellManager`未初始化物件，此函數會呼叫[CWinAppEx::InitShellManager](#initshellmanager)它傳回的指標之前。  
  
##  <a name="getstring"></a>CWinAppEx::GetString  
 讀取的字串資料，從指定的登錄機碼。  
  
```  
CString GetString(
    LPCTSTR lpszEntry,  
    LPCTSTR lpzDefault= _T(""));
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszEntry`  
 字串，包含的登錄機碼名稱  
  
 [in] `lpzDefault`  
 如果指定的登錄項目不存在該方法會傳回預設值。  
  
### <a name="return-value"></a>傳回值  
 成功; 如果在登錄中儲存的字串資料`lpszDefault`否則。  
  
### <a name="remarks"></a>備註  
 這個方法會讀取寫入登錄的字串資料。 若要將資料寫入登錄中，使用方法[CWinAppEx::WriteString](#writestring)或[CWinAppEx::WriteSectionString](#writesectionstring)。  
  
 `lpszEntry`參數就是位於您的應用程式的預設登錄機碼下的登錄項目名稱。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
##  <a name="gettooltipmanager"></a>CWinAppEx::GetTooltipManager  
 將指標傳回至全域[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)物件。  
  
```  
CTooltipManager* GetTooltipManager();
```  
  
### <a name="return-value"></a>傳回值  
 指標的全域`CTooltipManager`物件。  
  
### <a name="remarks"></a>備註  
 如果`CTooltipManager`未初始化物件，此函數會呼叫[cwinappex:: Inittooltipmanager](#inittooltipmanager)它傳回的指標之前。  
  
##  <a name="getusertoolsmanager"></a>CWinAppEx::GetUserToolsManager  
 將指標傳回至全域[CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)物件。  
  
```  
CUserToolsManager* GetUserToolsManager();
```  
  
### <a name="return-value"></a>傳回值  
 指標的全域`CUserToolsManager`物件;`NULL`如果使用者工具管理未啟用應用程式。  
  
### <a name="remarks"></a>備註  
 擷取的指標之前`CUserToolsManager`物件，您必須藉由呼叫初始化管理員[CWinAppEx::EnableUserTools](#enableusertools)。  
  
##  <a name="initcontextmenumanager"></a>CWinAppEx::InitContextMenuManager  
 初始化[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)物件。  
  
```  
BOOL InitContextMenuManager();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法會建立 CContextMenuManager 物件，則為非零0 代表`CContextMenuManager`物件已經存在。  
  
### <a name="remarks"></a>備註  
 如果您呼叫[CWinAppEx::GetContextMenuManager](#getcontextmenumanager)，該方法的預設實作會呼叫`InitContextMenuManager`。  
  
 如果您的應用程式已取得內容功能表管理員，而且您呼叫`InitContextMenuManager`，您的應用程式[ASSERT](diagnostic-services.md#assert)失敗。 因此，您不應該呼叫`InitContextMenuManager`如果您建立`CContextMenuManager`直接物件。 如果您不想要使用自訂`CContextMenuManager`，您應該使用`GetContextMenuManager`建立`CContextMenuManager`物件。  
  
##  <a name="initkeyboardmanager"></a>CWinAppEx::InitKeyboardManager  
 初始化[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)物件。  
  
```  
BOOL InitKeyboardManager();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法會建立為非零`CKeyboardManager`物件，則為 0 代表`CKeyboardManager`物件已經存在。  
  
### <a name="remarks"></a>備註  
 如果您呼叫[CWinAppEx::GetKeyboardManager](#getkeyboardmanager)，該方法的預設實作會呼叫`InitKeyboardManager`。  
  
 如果您的應用程式已取得鍵盤管理員，而且您呼叫`InitKeyboardManager`，您的應用程式[ASSERT](diagnostic-services.md#assert)失敗。 因此，您不應該呼叫`InitKeyboardManager`如果您建立`CKeyboardManager`直接物件。 如果您不想要使用自訂`CKeyboardManager`，您應該使用`GetKeyboardManager`建立`CKeyboardManager`物件。  
  
##  <a name="initmousemanager"></a>CWinAppEx::InitMouseManager  
 初始化[CMouseManager](../../mfc/reference/cmousemanager-class.md)物件。  
  
```  
BOOL InitMouseManager();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法會建立為非零`CMouseManager`物件，則為 0 代表`CMouseManager`物件已經存在。  
  
### <a name="remarks"></a>備註  
 如果您呼叫[CWinAppEx::GetMouseManager](#getmousemanager)，該方法的預設實作會呼叫`InitMouseManager`。  
  
 如果您的應用程式已取得滑鼠管理員，而且您呼叫`InitMouseManager`，您的應用程式[ASSERT](diagnostic-services.md#assert)失敗。 因此您不應該呼叫`InitMouseManager`如果您建立`CMouseManager`直接物件。 如果您不想要使用自訂`CMouseManager`，您應該使用`GetMouseManager`建立`CMouseManager`物件。  
  
##  <a name="initshellmanager"></a>CWinAppEx::InitShellManager  
 初始化[CShellManager](../../mfc/reference/cshellmanager-class.md)物件。  
  
```  
BOOL InitShellManager();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法會建立為非零`CShellManager`物件，則為 0 代表`CShellManager`物件已經存在。  
  
### <a name="remarks"></a>備註  
 如果您呼叫[CWinAppEx::GetShellManager](#getshellmanager)，該方法的預設實作會呼叫`InitShellManager`。  
  
 如果您的應用程式已取得殼層管理員，而且您呼叫`InitShellManager`，應用程式引發[ASSERT](diagnostic-services.md#assert)失敗。 因此，請勿呼叫`InitShellManager`如果您建立`CShellManager`直接物件。 如果您不想要使用自訂`CShellManager`，使用`GetShellManager`建立`CShellManager`物件。  
  
##  <a name="inittooltipmanager"></a>Cwinappex:: Inittooltipmanager  
 初始化[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)物件。  
  
```  
BOOL InitTooltipManager();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法會建立為非零`CTooltipManager`物件，則為 0 代表`CTooltipManager`物件已經存在。  
  
### <a name="remarks"></a>備註  
 如果您呼叫[CWinAppEx::GetTooltipManager](#gettooltipmanager)，該方法的預設實作會呼叫`InitTooltipManager`。  
  
 如果您的應用程式已取得工具提示管理員，而且您呼叫`InitTooltipManager`，您的應用程式[ASSERT](diagnostic-services.md#assert)失敗。 因此，您不應該呼叫`InitTooltipManager`如果您建立`CTooltipManager`直接物件。 如果您不想要使用自訂`CTooltipManager`，您應該使用`GetTooltipManager`建立`CTooltipManager`物件。  
  
##  <a name="isresourcesmartupdate"></a>CWinAppEx::IsResourceSmartUpdate  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsResourceSmartUpdate() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="isstateexists"></a>CWinAppEx::IsStateExists  
 指出是否在登錄中指定之索引鍵。  
  
```  
BOOL IsStateExists(LPCTSTR lpszSectionName);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszSectionName`  
 包含的登錄機碼路徑的字串。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果索引鍵存在於登錄中。否則便是 0。  
  
##  <a name="loadcustomstate"></a>CWinAppEx::LoadCustomState  
 從登錄載入應用程式狀態後，架構會呼叫這個方法。  
  
```  
virtual void LoadCustomState();
```  
  
### <a name="remarks"></a>備註  
 如果您想要進行任何處理，應用程式從登錄載入狀態之後，請覆寫這個方法。 根據預設，這個方法沒有任何作用。  
  
 若要從登錄載入的自訂狀態資訊，必須先儲存資訊使用[CWinAppEx::SaveCustomState](#savecustomstate)。  
  
##  <a name="loadstate"></a>CWinAppEx::LoadState  
 從 Windows 登錄中讀取應用程式狀態。  
  
```  
BOOL LoadState(
    CMDIFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);

 
BOOL LoadState(
    CFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);

 
BOOL LoadState(
    COleIPFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);

 
virtual BOOL LoadState(
    LPCTSTR lpszSectionName = NULL,  
    CFrameImpl* pFrameImpl = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `pFrame`  
 框架視窗物件的指標。 此方法適用於此框架視窗中登錄的狀態資訊。  
  
 [in] `lpszSectionName`  
 字串，包含相對路徑的登錄機碼。  
  
 [in] `pFrameImpl`  
 指標`CFrameImpl`物件。 此方法適用於此框架視窗中登錄的狀態資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會載入應用程式和框架視窗的任何狀態資訊的狀態。 框架視窗的載入的資訊會套用到所提供的框架視窗。 如果您未提供框架視窗，只將應用程式狀態資訊會載入。 應用程式資訊包含狀態的[CMouseManager 類別](../../mfc/reference/cmousemanager-class.md)， [CContextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)， [CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)，而[CUserToolsManager 類別](../../mfc/reference/cusertoolsmanager-class.md)。  
  
 預設實作`CFrameImpl::OnLoadFrame`呼叫`LoadState`。  
  
 `lpszSectionName`參數不是絕對路徑的登錄項目。 它是相對的路徑加入至您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
##  <a name="loadwindowplacement"></a>CWinAppEx::LoadWindowPlacement  
 從登錄載入的大小和位置的主框架視窗時，由架構呼叫。  
  
```  
virtual BOOL LoadWindowPlacement(
    CRect& rectNormalPosition,  
    int& nFlags,  
    int& nShowCmd);
```  
  
### <a name="parameters"></a>參數  
 [輸出] `rectNormalPosition`  
 包含主框架視窗的座標，當它是在還原的位置矩形。  
  
 [輸出] `nFlags`  
 控制的位置最小化的視窗及作業系統還原的視窗最小化的視窗之間切換的方式的旗標。  
  
 [輸出] `nShowCmd`  
 指定視窗的顯示狀態的整數。 如需可能值的詳細資訊，請參閱[CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 根據預設，MFC 會自動載入主框架視窗的狀態與前一個位置的應用程式啟動時。 如需這項資訊儲存在登錄中的方式的詳細資訊，請參閱[CWinAppEx::StoreWindowPlacement](#storewindowplacement)。  
  
 如果您想要載入的主框架視窗的其他資訊，請覆寫這個方法。  
  
##  <a name="m_bforceimagereset"></a>CWinAppEx::m_bForceImageReset  
 指定當您重新載入專案包含的工具列的框架視窗 framework 是否重設所有工具列影像。  
  
```  
BOOL m_bForceImageReset;  
```  
  
### <a name="remarks"></a>備註  
 `m_bForceImageReset`資料成員是受保護的變數。  
  
##  <a name="onappcontexthelp"></a>CWinAppEx::OnAppContextHelp  
 架構會呼叫這個方法，當使用者要求的內容說明**自訂** 對話方塊。  
  
```  
virtual void OnAppContextHelp(
    CWnd* pWndControl,  
    const DWORD dwHelpIDArray[]);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndControl`  
 使用者叫用內容說明視窗物件的指標。  
  
 [in] `dwHelpIDArray[]`  
 保留的值。  
  
### <a name="remarks"></a>備註  
 這個方法目前已保留供未來使用。 預設實作不做任何動作，它目前不由架構呼叫。  
  
##  <a name="onclosingmainframe"></a>CWinAppEx::OnClosingMainFrame  
 框架視窗正在處理時，架構會呼叫這個方法`WM_CLOSE`。  
  
```  
virtual void OnClosingMainFrame(CFrameImpl* pFrameImpl);
```  
  
### <a name="parameters"></a>參數  
 [in] `pFrameImpl`  
 指標`CFrameImpl`物件。  
  
### <a name="remarks"></a>備註  
 這個方法的預設實作會將儲存的狀態`pFrameImpl`。  
  
##  <a name="onviewdoubleclick"></a>CWinAppEx::OnViewDoubleClick  
 呼叫使用者定義的命令是與檢視相關聯，當使用者按兩下該檢視內的任何位置。  
  
```  
virtual BOOL OnViewDoubleClick(
    CWnd* pWnd,  
    int iViewId);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWnd`  
 物件的指標衍生自[CView 類別](../../mfc/reference/cview-class.md)。  
  
 [in] `iViewId`  
 檢視識別碼。  
  
### <a name="return-value"></a>傳回值  
 `True`如果架構找到命令。否則為 false。  
  
### <a name="remarks"></a>備註  
 為了支援自訂滑鼠行為，您必須呼叫此函式處理時`WM_LBUTTONDBLCLK`訊息。 這個方法會執行與所提供的檢視表識別碼相關聯的命令`iViewId`。 如需自訂滑鼠行為的詳細資訊，請參閱[鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)。  
  
##  <a name="onworkspaceidle"></a>CWinAppEx::OnWorkspaceIdle  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnWorkspaceIdle(CWnd*);
```  
  
### <a name="parameters"></a>參數  
 [in] `CWnd*`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="preloadstate"></a>CWinAppEx::PreLoadState  
 它會從登錄載入應用程式的狀態之前，架構會呼叫這個方法。  
  
```  
virtual void PreLoadState();
```  
  
### <a name="remarks"></a>備註  
 如果您想要進行任何處理架構載入應用程式的狀態之前，請覆寫這個方法。  
  
##  <a name="presavestate"></a>CWinAppEx::PreSaveState  
 它會將儲存應用程式狀態之前，架構會呼叫這個方法。  
  
```  
virtual void PreSaveState();
```  
  
### <a name="remarks"></a>備註  
 如果您想要進行任何處理，架構會將儲存應用程式狀態之前，請覆寫這個方法。  
  
##  <a name="reloadwindowplacement"></a>CWinAppEx::ReloadWindowPlacement  
 重新載入的大小和位置的登錄中的視窗。  
  
```  
virtual BOOL ReloadWindowPlacement(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>參數  
 [in] `pFrame`  
 框架視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果該方法成功。0，表示載入失敗，或是沒有載入任何資料。  
  
### <a name="remarks"></a>備註  
 使用函數[CWinAppEx::StoreWindowPlacement](#storewindowplacement)寫入登錄的大小和視窗的位置。  
  
##  <a name="savecustomstate"></a>CWinAppEx::SaveCustomState  
 它會將儲存至登錄應用程式的狀態之後，架構會呼叫這個方法。  
  
```  
virtual void SaveCustomState();
```  
  
### <a name="remarks"></a>備註  
 如果您想要進行任何處理，應用程式會將狀態儲存至登錄之後，請覆寫這個方法。 根據預設，這個方法沒有任何作用。  
  
##  <a name="savestate"></a>CWinAppEx::SaveState  
 應用程式狀態寫入 Windows 登錄中。  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszSectionName = NULL,  
    CFrameImpl* pFrameImpl = NULL);

 
BOOL SaveState(
    CMDIFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);

 
BOOL SaveState(
    CFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);

 
BOOL SaveState(
    COleIPFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszSectionName`  
 字串，包含相對路徑的登錄機碼。  
  
 [in] `pFrameImpl`  
 指標`CFrameImpl`物件。 此框架會儲存至 Windows 登錄中。  
  
 [in] `pFrame`  
 框架視窗物件的指標。 此框架會儲存至 Windows 登錄中。  
  
### <a name="return-value"></a>傳回值  
 `True`如果登錄成功。，`false`否則。  
  
### <a name="remarks"></a>備註  
 這個方法會將儲存應用程式和提供的框架視窗的任何狀態資訊的狀態。 如果未提供框架視窗，此方法只會儲存應用程式狀態。 應用程式資訊包含狀態的[CMouseManager 類別](../../mfc/reference/cmousemanager-class.md)， [CContextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)， [CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)，而[CUserToolsManager 類別](../../mfc/reference/cusertoolsmanager-class.md)。  
  
 `lpszSectionName`參數不是絕對路徑的登錄項目。 它是相對路徑附加到您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
##  <a name="setregistrybase"></a>CWinAppEx::SetRegistryBase  
 設定應用程式的預設登錄路徑。  
  
```  
LPCTSTR SetRegistryBase(LPCTSTR lpszSectionName = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszSectionName`  
 字串，包含路徑的登錄機碼。  
  
### <a name="return-value"></a>傳回值  
 字串，包含預設登錄位置的路徑。  
  
### <a name="remarks"></a>備註  
 所有方法[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)，存取在預設位置的登錄開始。 若要變更該預設登錄位置中使用這個方法。 使用[CWinAppEx::GetRegistryBase](#getregistrybase)擷取預設登錄位置。  
  
##  <a name="showpopupmenu"></a>CWinAppEx::ShowPopupMenu  
 顯示快顯功能表。  
  
```  
virtual BOOL ShowPopupMenu(
    UINT uiMenuResId,  
    const CPoint& point,  
    CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiMenuResId`  
 功能表上的資源 id。  
  
 [in] `point`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)螢幕座標中指定功能表的位置。  
  
 [in] `pWnd`  
 擁有快顯功能表視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果快顯功能表會顯示可順利啟動。否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會顯示相關聯的功能表`uiMenuResId`。  
  
 若要支援快顯功能表，您必須擁有[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)物件。 如果您有未初始化`CContextMenuManager`物件`ShowPopupMenu`將會失敗。  
  
##  <a name="storewindowplacement"></a>CWinAppEx::StoreWindowPlacement  
 由架構呼叫以登錄中寫入的大小和位置的主框架視窗。  
  
```  
virtual BOOL StoreWindowPlacement(
    const CRect& rectNormalPosition,  
    int nFlags,  
    int nShowCmd);
```  
  
### <a name="parameters"></a>參數  
 [in] `nFlags`  
 控制的位置最小化的視窗及作業系統還原的視窗最小化的視窗之間切換的方式的旗標。  
  
 [in] `nShowCmd`  
 指定視窗的顯示狀態的整數。 如需可能值的詳細資訊，請參閱[CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)。  
  
 [in] `rectNormalPosition`  
 處於還原中狀態時，包含的主框架視窗座標的矩形。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 根據預設，MFC 會自動儲存的位置和應用程式結束之前的主框架視窗的狀態。 這項資訊會儲存在 Windows 登錄 WindowPlacement 機碼的預設登錄位置中，您的應用程式。 多個應用程式的預設登錄位置的詳細資訊，請參閱[CWinAppEx::GetRegistryBase](#getregistrybase)。  
  
 如果您想要儲存在主框架視窗的其他資訊，請覆寫這個方法。  
  
##  <a name="writebinary"></a>CWinAppEx::WriteBinary  
 將二進位資料寫入登錄。  
  
```  
BOOL WriteBinary(
    LPCTSTR lpszEntry,  
    LPBYTE pData,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszEntry`  
 字串，包含的登錄機碼名稱。  
  
 [in] `pData`  
 要儲存的資料。  
  
 [in] `nBytes`  
 大小`pData`以位元組為單位。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 `lpszEntry`參數就是位於您的應用程式的預設登錄機碼下的登錄項目名稱。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
 如果所指定的索引鍵`lpszEntry`不存在，這個方法會建立它。  
  
##  <a name="writeint"></a>CWinAppEx::WriteInt  
 將數值資料寫入登錄。  
  
```  
BOOL WriteInt(
    LPCTSTR lpszEntry,  
    int nValue);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszEntry`  
 字串，包含的登錄機碼名稱。  
  
 [in] `nValue`  
 要儲存的資料。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 `lpszEntry`參數就是位於您的應用程式的預設登錄機碼下的登錄項目名稱。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
 如果所指定的索引鍵`lpszEntry`不存在，這個方法會建立它。  
  
##  <a name="writeobject"></a>CWinAppEx::WriteObject  
 將衍生自資料寫入[CObject 類別](../../mfc/reference/cobject-class.md)登錄。  
  
```  
BOOL WriteObject(
    LPCTSTR lpszEntry,  
    CObject& obj);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszEntry`  
 字串，包含要設定的值。  
  
 [in] `obj`  
 若要參考`CObject`方法會將儲存的資料。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會寫入`obj`預設登錄機碼下的指定值的資料。 使用[CWinAppEx::GetRegistryBase](#getregistrybase)來判斷目前的登錄機碼。  
  
##  <a name="writesectionbinary"></a>CWinAppEx::WriteSectionBinary  
 將二進位資料寫入登錄中的值。  
  
```  
BOOL WriteSectionBinary(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    LPBYTE pData,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszSubSection`  
 字串，包含的登錄機碼名稱  
  
 [in] `lpszEntry`  
 字串，包含要設定的值。  
  
 [in] `pData`  
 要寫入登錄的資料。  
  
 [in] `nBytes`  
 大小`pData`以位元組為單位。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 `lpszSubSection`參數不是絕對路徑的登錄項目。 它是相對路徑附加到您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
 如果所指定的索引鍵`lpszEntry`不存在，這個方法會建立它。  
  
##  <a name="writesectionint"></a>CWinAppEx::WriteSectionInt  
 將數值資料寫入登錄。  
  
```  
BOOL WriteSectionInt(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    int nValue);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszSubSection`  
 字串，包含相對路徑的登錄機碼。  
  
 [in] `lpszEntry`  
 字串，包含要設定的值。  
  
 [in] `nValue`  
 要寫入登錄的資料。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 `lpszSubSection`參數不是絕對路徑的登錄項目。 它是附加至您的應用程式的預設登錄機碼的相對路徑。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
 如果所指定的索引鍵`lpszEntry`不存在，這個方法會建立它。  
  
##  <a name="writesectionobject"></a>CWinAppEx::WriteSectionObject  
 將衍生自資料寫入[CObject 類別](../../mfc/reference/cobject-class.md)特定登錄值。  
  
```  
BOOL WriteSectionObject(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    CObject& obj);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszSubSection`  
 字串，包含的登錄機碼名稱。  
  
 [in] `lpszEntry`  
 字串，包含要設定之值的名稱。  
  
 [in] `obj`  
 要儲存的資料。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 `lpszSubSection`參數不是絕對路徑的登錄項目。 它是相對路徑附加到您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
 如果所指定的值`lpszEntry`下所指定的登錄機碼不存在`lpszSubSection`，這個方法會建立該值。  
  
##  <a name="writesectionstring"></a>CWinAppEx::WriteSectionString  
 將字串的資料寫入登錄中的值。  
  
```  
BOOL WriteSectionString(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    LPCTSTR lpszValue);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszSubSection`  
 字串，包含的登錄機碼名稱。  
  
 [in] `lpszEntry`  
 字串，包含要設定的值。  
  
 [in] `lpszValue`  
 要寫入登錄的字串資料。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 `lpszSubSection`參數不是絕對路徑的登錄項目。 它是相對路徑附加到您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
 如果所指定的值`lpszEntry`下沒有`lpszSubSection`，這個方法會建立它。  
  
##  <a name="writestring"></a>CWinAppEx::WriteString  
 將字串的資料寫入登錄。  
  
```  
BOOL WriteString(
    LPCTSTR lpszEntry,  
    LPCTSTR lpszValue);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszEntry`  
 字串，包含的登錄機碼名稱。  
  
 [in] `lpszValue`  
 要儲存的資料。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 `lpszEntry`參數就是位於您的應用程式的預設登錄機碼下的登錄項目名稱。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
 如果所指定的索引鍵`lspzEntry`不存在，這個方法會建立它。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CWinApp 類別](../../mfc/reference/cwinapp-class.md)   
 [CMouseManager 類別](../../mfc/reference/cmousemanager-class.md)   
 [CContextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)   
 [CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)   
 [CUserToolsManager 類別](../../mfc/reference/cusertoolsmanager-class.md)

