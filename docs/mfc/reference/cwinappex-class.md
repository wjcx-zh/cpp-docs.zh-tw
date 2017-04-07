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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6931f1e794116882722e402c9cb95acec1ebdfd5
ms.lasthandoff: 02/24/2017

---
# <a name="cwinappex-class"></a>Cwinappex 衍生類別
`CWinAppEx`處理應用程式狀態、 儲存狀態至登錄、 從登錄載入狀態、 初始化應用程式管理員和提供這些相同的應用程式管理員的連結。  
  
## <a name="syntax"></a>語法  
  
```  
class CWinAppEx : public CWinApp  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CWinAppEx::CWinAppEx](#cwinappex)|建構 `CWinAppEx` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CWinAppEx::CleanState](#cleanstate)|從 Windows 登錄移除應用程式的相關資訊。|  
|[CWinAppEx::EnableLoadWindowPlacement](#enableloadwindowplacement)|指定應用程式是否會載入初始大小和主框架視窗的位置，登錄中。|  
|[CWinAppEx::EnableTearOffMenus](#enabletearoffmenus)|可讓 tear-off 功能表應用程式。|  
|[CWinAppEx::EnableUserTools](#enableusertools)|可讓使用者在應用程式中建立自訂的功能表命令。|  
|[CWinAppEx::ExitInstance](#exitinstance)|中，由框架呼叫`Run`成員函式來結束應用程式的這個執行個體。 (覆寫[CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)。)|  
|[CWinAppEx::GetBinary](#getbinary)|讀取指定的登錄值相關聯的二進位資料。|  
|[CWinAppEx::GetContextMenuManager](#getcontextmenumanager)|將指標傳回至全域[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)物件。|  
|[CWinAppEx::GetDataVersion](#getdataversion)||  
|[CWinAppEx::GetDataVersionMajor](#getdataversionmajor)|傳回儲存在 Windows 登錄中的應用程式的主要版本。|  
|[CWinAppEx::GetDataVersionMinor](#getdataversionminor)|傳回儲存在 Windows 登錄中的應用程式的次要版本。|  
|[CWinAppEx::GetInt](#getint)|讀取登錄中指定的值相關聯的數值資料。|  
|[CWinAppEx::GetKeyboardManager](#getkeyboardmanager)|將指標傳回至全域[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)物件。|  
|[CWinAppEx::GetMouseManager](#getmousemanager)|將指標傳回至全域[CMouseManager](../../mfc/reference/cmousemanager-class.md)物件。|  
|[CWinAppEx::GetObject](#getobject)|讀取`CObject`-衍生登錄從指定的值相關聯的資料。|  
|[CWinAppEx::GetRegSectionPath](#getregsectionpath)|傳回字串，這是登錄機碼的路徑。 此路徑會串連提供的相對路徑，與應用程式路徑。|  
|[CWinAppEx::GetRegistryBase](#getregistrybase)|傳回應用程式的登錄路徑。|  
|[CWinAppEx::GetSectionBinary](#getsectionbinary)|讀取登錄值與指定之索引鍵相關聯的二進位資料。|  
|[CWinAppEx::GetSectionInt](#getsectionint)|讀取具有指定之索引鍵和值相關聯的登錄數值資料。|  
|[CWinAppEx::GetSectionObject](#getsectionobject)|讀取`CObject`登錄值與指定之索引鍵相關聯的資料。|  
|[CWinAppEx::GetSectionString](#getsectionstring)|讀取登錄值與指定之索引鍵相關聯的字串資料。|  
|[CWinAppEx::GetShellManager](#getshellmanager)|將指標傳回至全域[CShellManager](../../mfc/reference/cshellmanager-class.md)物件。|  
|[CWinAppEx::GetString](#getstring)|讀取登錄中指定的值相關聯的字串資料。|  
|[CWinAppEx::GetTooltipManager](#gettooltipmanager)|將指標傳回至全域[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)物件。|  
|[CWinAppEx::GetUserToolsManager](#getusertoolsmanager)|將指標傳回至全域[CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)物件。|  
|[CWinAppEx::InitContextMenuManager](#initcontextmenumanager)|初始化`CContextMenuManager`物件。|  
|[CWinAppEx::InitKeyboardManager](#initkeyboardmanager)|初始化`CKeyboardManager`物件。|  
|[CWinAppEx::InitMouseManager](#initmousemanager)|初始化`CMouseManager`物件。|  
|[CWinAppEx::InitShellManager](#initshellmanager)|初始化`CShellManager`類別|  
|[CWinAppEx::InitTooltipManager](#inittooltipmanager)|初始化`CTooltipManager`類別。|  
|[CWinAppEx::IsResourceSmartUpdate](#isresourcesmartupdate)||  
|[CWinAppEx::IsStateExists](#isstateexists)|指出是否在登錄中指定的索引鍵。|  
|[CWinAppEx::LoadState](#loadstate)|從登錄載入應用程式的狀態。|  
|[CWinAppEx::OnAppContextHelp](#onappcontexthelp)|當使用者要求內容的說明，由框架呼叫**自訂**對話方塊。|  
|[CWinAppEx::OnViewDoubleClick](#onviewdoubleclick)|當使用者按兩下應用程式中的任何位置，請呼叫使用者定義的命令。|  
|[CWinAppEx::OnWorkspaceIdle](#onworkspaceidle)||  
|[CWinAppEx::SaveState](#savestate)|應用程式架構的狀態寫入 Windows 登錄中。|  
|[CWinAppEx::SetRegistryBase](#setregistrybase)|設定預設登錄機碼的路徑。 這個索引鍵做為所有後續的登錄呼叫的根。|  
|[CWinAppEx::ShowPopupMenu](#showpopupmenu)|顯示快顯功能表。|  
|[CWinAppEx::WriteBinary](#writebinary)|寫入指定的登錄值的二進位資料。|  
|[CWinAppEx::WriteInt](#writeint)|寫入指定的登錄值的數值資料。|  
|[CWinAppEx::WriteObject](#writeobject)|寫入資料衍生自[CObject 類別](../../mfc/reference/cobject-class.md)到指定的登錄值。|  
|[CWinAppEx::WriteSectionBinary](#writesectionbinary)|二進位資料寫入指定的登錄機碼的值。|  
|[CWinAppEx::WriteSectionInt](#writesectionint)|數字的資料寫入指定的登錄機碼的值。|  
|[CWinAppEx::WriteSectionObject](#writesectionobject)|將資料衍生自`CObject`類別指定的登錄機碼的值。|  
|[CWinAppEx::WriteSectionString](#writesectionstring)|字串資料寫入指定的登錄機碼的值。|  
|[CWinAppEx::WriteString](#writestring)|寫入指定的登錄值的字串資料。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CWinAppEx::LoadCustomState](#loadcustomstate)|已載入應用程式的狀態時，由架構呼叫。|  
|[CWinAppEx::LoadWindowPlacement](#loadwindowplacement)|從登錄載入的大小和位置的應用程式時，由架構呼叫。 載入的資料包括的大小和位置的主要畫面格的上一次關閉您的應用程式的時間。|  
|[CWinAppEx::OnClosingMainFrame](#onclosingmainframe)|當處理主框架視窗時，由框架呼叫`WM_CLOSE`。|  
|[CWinAppEx::PreLoadState](#preloadstate)|前面的架構所呼叫的應用程式狀態會載入。|  
|[CWinAppEx::PreSaveState](#presavestate)|前面的架構所呼叫的應用程式狀態會儲存。|  
|[CWinAppEx::ReloadWindowPlacement](#reloadwindowplacement)|重新載入的大小和位置的登錄中提供的視窗|  
|[CWinAppEx::SaveCustomState](#savecustomstate)|應用程式的狀態寫入登錄之後，由架構呼叫。|  
|[CWinAppEx::StoreWindowPlacement](#storewindowplacement)|寫入登錄的大小和位置的主要畫面格的架構所呼叫。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CWinAppEx::m_bForceImageReset](#m_bforceimagereset)|指定是否架構將會重設所有的工具列影像載入框架視窗，其中包含工具列時。|  
  
## <a name="remarks"></a>備註  
 MFC 架構所提供的功能大多取決於`CWinAppEx`類別。 您可以將`CWinAppEx`到您的應用程式中有兩種類別︰  
  
-   建構`CWinAppEx`主執行緒中的類別。  
  
-   將主應用程式類別衍生自`CWinAppEx`。  
  
 您將合併後`CWinAppEx`到您的應用程式，您可以初始化其中一個應用程式管理員。 使用應用程式管理員之前，您必須藉由呼叫適當的 initialize 方法來進行初始化。 若要取得特定經理的指標，呼叫相關聯的 get 方法。 `CWinAppEx`類別會管理下列應用程式管理員︰ [CMouseManager 類別](../../mfc/reference/cmousemanager-class.md)， [CContextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)， [CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)， [CUserToolsManager 類別](../../mfc/reference/cusertoolsmanager-class.md)，和[CMenuTearOffManager 類別](../../mfc/reference/cmenutearoffmanager-class.md)。  
  
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
 字串，其中包含的登錄機碼路徑。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會清除從登錄的特定區段的應用程式資料。 您可以指定使用參數清除區段`lpszSectionName`。 如果`lpszSectionName`是`NULL`，這個方法會使用儲存在預設登錄路徑`CWinAppEx`物件。 若要取得預設的登錄路徑，請使用[CWinAppEx::GetRegistryBase](#getregistrybase)。  
  
##  <a name="cwinappex"></a>CWinAppEx::CWinAppEx  
 建構 `CWinAppEx` 物件。  
  
```  
CWinAppEx(BOOL bResourceSmartUpdate = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bResourceSmartUpdate`  
 布林值的參數，指定工作區的物件是否應該偵測與處理資源更新。  
  
### <a name="remarks"></a>備註  
 `CWinAppEx`類別有初始設定方法，提供儲存和載入至登錄，應用程式資訊的功能和控制項通用的應用程式設定。 它也可讓您使用全域管理員，例如[CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)和[CUserToolsManager 類別](../../mfc/reference/cusertoolsmanager-class.md)。 每個應用程式可以有只有一個執行個體`CWinAppEx`類別。  
  
##  <a name="enableloadwindowplacement"></a>CWinAppEx::EnableLoadWindowPlacement  
 指定應用程式是否會載入初始大小和主框架視窗的位置，登錄中。  
  
```  
void EnableLoadWindowPlacement(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 指定應用程式從登錄是否載入的初始大小和主框架視窗的位置。  
  
### <a name="remarks"></a>備註  
 根據預設，大小和位置的主要畫面格是從登錄以及其他應用程式設定載入。 時發生此狀況[CWinAppEx::LoadState](#loadstate)。 如果不想從登錄載入初始視窗放置，呼叫這個方法與`bEnable`設為`false`。  
  
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
 字串，其中包含的登錄機碼路徑。 應用程式會使用這個登錄機碼的 tear-off 功能表儲存資訊。  
  
 [in] `uiCmdFirst`  
 第一個功能表下的識別碼。  
  
 [in] `uiCmdLast`  
 最後一個功能表下的識別碼。  
  
### <a name="return-value"></a>傳回值  
 `True`如果`CMenuTearOffManager`建立和初始化可順利啟動。`false`發生錯誤，或如果`CMenuTearOffManager`已經存在。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式來啟用應用程式中的 tear-off 功能表。 您應該呼叫此函式，從`InitInstance`。  
  
##  <a name="enableusertools"></a>CWinAppEx::EnableUserTools  
 可讓使用者建立自訂功能表命令，減少應用程式中的按鍵。 這個方法會建立[CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)物件。  
  
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
 不帶正負號的整數，架構會使用預留位置做為使用者的 [工具] 功能表的命令 ID。  
  
 [in] `uiCmdFirst`  
 第一次的使用者工具命令的命令 ID。  
  
 [in] `uiCmdLast`  
 最後的使用者工具命令的命令 ID。  
  
 [in] `pToolRTC`  
 類別 A`CUserToolsManager`物件用來建立新的使用者工具。  
  
 [in] `uArgMenuID`  
 引數功能表識別碼。  
  
 [in] `uInitDirMenuID`  
 初始的工具目錄功能表識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法會建立並初始化`CUserToolsManager`物件;`FALSE`如果方法失敗，或如果`CUserToolsManager`物件已經存在。  
  
### <a name="remarks"></a>備註  
 當您啟用使用者定義的工具時，架構會自動支援動態功能表的自訂期間可以擴充。 架構會將每個新的項目關聯外部命令。 當使用者選取適當的項目，從這些命令叫用的架構**工具**功能表。  
  
 每次使用者加入新項目時，架構會建立新的物件。 類別的新物件的類型由`pToolRTC`。 `pToolRTC`類別型別必須衍生自[CUserTool 類別](../../mfc/reference/cusertool-class.md)。  
  
 如需使用者工具，以及如何將它們合併到您的應用程式的詳細資訊，請參閱[使用者定義工具](../../mfc/user-defined-tools.md)。  
  
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
 字串，其中包含的登錄機碼名稱。  
  
 [輸出] `ppData`  
 方法會填滿的二進位資料緩衝區的指標。  
  
 [輸出] `pBytes`  
 讀取方法用來寫入的位元組數目的不帶正負號整數的指標。  
  
### <a name="return-value"></a>傳回值  
 `True`如果登錄成功。，`false`否則。  
  
### <a name="remarks"></a>備註  
 這個方法會讀取寫入登錄的二進位資料。 若要將資料寫入至登錄中，使用方法[CWinAppEx::WriteBinary](#writebinary)和[CWinAppEx::WriteSectionBinary](#writesectionbinary)。  
  
 `lpszEntry`參數就是位於您的應用程式的預設登錄機碼底下的登錄項目名稱。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
##  <a name="getcontextmenumanager"></a>CWinAppEx::GetContextMenuManager  
 將指標傳回至全域[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)物件。  
  
```  
CContextMenuManager* GetContextMenuManager();
```  
  
### <a name="return-value"></a>傳回值  
 指標的全域`CContextMenuManager`物件。  
  
### <a name="remarks"></a>備註  
 如果尚未初始化 CContextMenuManager 物件，此函數會呼叫[CWinAppEx::InitContextMenuManager](#initcontextmenumanager)之前它傳回的指標。  
  
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
 包含主要版本號碼的整數值。  
  
##  <a name="getdataversionminor"></a>CWinAppEx::GetDataVersionMinor  
 傳回會儲存在 Windows 登錄中，當您呼叫的應用程式的次要版本[CWinAppEx::SaveState](#savestate)。  
  
```  
int GetDataVersionMinor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 包含次要版本號碼的整數值。  
  
##  <a name="getint"></a>CWinAppEx::GetInt  
 從指定的登錄機碼讀取整數資料。  
  
```  
int GetInt(
    LPCTSTR lpszEntry,  
    int nDefault = 0);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszEntry`  
 字串，其中包含登錄項目名稱。  
  
 [in] `nDefault`  
 如果指定的登錄項目不存在則方法會傳回預設值。  
  
### <a name="return-value"></a>傳回值  
 登錄資料，如果方法成功。否則`nDefault`。  
  
### <a name="remarks"></a>備註  
 這個方法會從登錄讀取整數資料。 如果沒有整數資料所指示的登錄機碼相關聯`lpszEntry`，這個方法會傳回`nDefault`。 若要將資料寫入至登錄中，使用方法[CWinAppEx::WriteSectionInt](#writesectionint)和[CWinAppEx::WriteInt](#writeint)。  
  
 `lpszEntry`參數就是位於您的應用程式的預設登錄機碼底下的登錄項目名稱。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
##  <a name="getkeyboardmanager"></a>CWinAppEx::GetKeyboardManager  
 將指標傳回至全域[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)物件。  
  
```  
CKeyboardManager* GetKeyboardManager();
```  
  
### <a name="return-value"></a>傳回值  
 指標的全域`CKeyboardManager`物件。  
  
### <a name="remarks"></a>備註  
 如果尚未初始化鍵盤管理員，此函數會呼叫[CWinAppEx::InitKeyboardManager](#initkeyboardmanager)之前它傳回的指標。  
  
##  <a name="getmousemanager"></a>CWinAppEx::GetMouseManager  
 將指標傳回至全域[CMouseManager](../../mfc/reference/cmousemanager-class.md)物件。  
  
```  
CMouseManager* GetMouseManager();
```  
  
### <a name="return-value"></a>傳回值  
 指標的全域`CMouseManager`物件。  
  
### <a name="remarks"></a>備註  
 如果未初始化滑鼠管理員，此函數會呼叫[CWinAppEx::InitMouseManager](#initmousemanager)之前它傳回的指標。  
  
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
 參考`CObject`。 方法會使用這個參考來登錄資料儲存。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會從衍生自登錄中讀取資料`CObject`。 要寫入`CObject`資料登錄中，使用其中一種[CWinAppEx::WriteObject](#writeobject)或[CWinAppEx::WriteSectionObject](#writesectionobject)。  
  
 `lpszEntry`參數就是位於您的應用程式的預設登錄機碼下的登錄項目名稱。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
##  <a name="getregistrybase"></a>CWinAppEx::GetRegistryBase  
 擷取應用程式的預設登錄路徑。  
  
```  
LPCTSTR GetRegistryBase();
```  
  
### <a name="return-value"></a>傳回值  
 字串，包含預設登錄位置的路徑。  
  
### <a name="remarks"></a>備註  
 所有的方法[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)，存取在預設位置的登錄開始。 使用這個方法來擷取預設登錄位置的路徑。 使用[CWinAppEx::SetRegistryBase](#setregistrybase)若要變更預設的登錄位置。  
  
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
 這個方法定義，加上中的相對路徑的登錄機碼的絕對路徑`szSectionAdd`到您的應用程式的預設登錄位置。 若要取得預設的登錄機碼，請使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)。  
  
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
 此方法會儲存資料的緩衝區指標。  
  
 [輸出] `pBytes`  
 不帶正負號的整數指標。 方法會寫入的大小`ppData`給這個參數。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `True`，否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會讀取登錄的方式寫入二進位資料[CWinAppEx::WriteBinary](#writebinary)和[CWinAppEx::WriteSectionBinary](#writesectionbinary)。  
  
 `lpszSubSection`參數不是絕對路徑的登錄項目。 它是相對路徑附加至您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
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
 如果指定的值並不會傳回預設值。  
  
### <a name="return-value"></a>傳回值  
 儲存在指定的登錄值; 整數資料`nDefault`如果資料不存在。  
  
### <a name="remarks"></a>備註  
 使用方法[CWinAppEx::WriteInt](#writeint)和[CWinAppEx::WriteSectionInt](#writesectionint)將整數資料寫入登錄。  
  
 `lpszSubSection`參數不是絕對路徑的登錄項目。 它是相對路徑新增至您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
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
 參考`CObject`。 此方法會使用這`CObject`登錄資料儲存。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會從登錄讀取資料。 資料讀取為`CObject`資料或從衍生的類別資料`CObject`。 要寫入`CObject`資料登錄中，使用其中一種[CWinAppEx::WriteObject](#writeobject)或[CWinAppEx::WriteSectionObject](#writesectionobject)。  
  
 `lpszSubSection`參數不是絕對路徑的登錄項目。 它是相對路徑附加至您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
##  <a name="getsectionstring"></a>CWinAppEx::GetSectionString  
 讀取字串中登錄的資料。  
  
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
 如果指定的值並不會傳回預設值。  
  
### <a name="return-value"></a>傳回值  
 如果資料存在，儲存在指定的登錄值的字串資料否則`lpszDefault`。  
  
### <a name="remarks"></a>備註  
 這個方法會讀取寫入登錄的字串資料。 使用[CWinAppEx::WriteString](#writestring)和[CWinAppEx::WriteSectionString](#writesectionstring)將字串資料寫入登錄。  
  
 `lpszSubSection`參數不是絕對路徑的登錄項目。 它是相對路徑附加至您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
##  <a name="getshellmanager"></a>CWinAppEx::GetShellManager  
 將指標傳回至全域[CShellManager](../../mfc/reference/cshellmanager-class.md)物件。  
  
```  
CShellManager* GetShellManager();
```  
  
### <a name="return-value"></a>傳回值  
 指標的全域`CShellManager`物件。  
  
### <a name="remarks"></a>備註  
 如果`CShellManager`未初始化物件，此函數會呼叫[CWinAppEx::InitShellManager](#initshellmanager)之前它傳回的指標。  
  
##  <a name="getstring"></a>CWinAppEx::GetString  
 讀取字串中指定的登錄機碼的資料。  
  
```  
CString GetString(
    LPCTSTR lpszEntry,  
    LPCTSTR lpzDefault= _T(""));
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszEntry`  
 字串，包含的登錄機碼名稱  
  
 [in] `lpzDefault`  
 如果指定的登錄項目不存在則方法會傳回預設值。  
  
### <a name="return-value"></a>傳回值  
 字串資料儲存在登錄中，如果登錄成功。`lpszDefault`否則。  
  
### <a name="remarks"></a>備註  
 這個方法會讀取寫入登錄的字串資料。 若要將資料寫入至登錄中，使用方法[CWinAppEx::WriteString](#writestring)或[CWinAppEx::WriteSectionString](#writesectionstring)。  
  
 `lpszEntry`參數就是位於您的應用程式的預設登錄機碼底下的登錄項目名稱。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
##  <a name="gettooltipmanager"></a>CWinAppEx::GetTooltipManager  
 將指標傳回至全域[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)物件。  
  
```  
CTooltipManager* GetTooltipManager();
```  
  
### <a name="return-value"></a>傳回值  
 指標的全域`CTooltipManager`物件。  
  
### <a name="remarks"></a>備註  
 如果`CTooltipManager`未初始化物件，此函數會呼叫[CWinAppEx::InitTooltipManager](#inittooltipmanager)之前它傳回的指標。  
  
##  <a name="getusertoolsmanager"></a>CWinAppEx::GetUserToolsManager  
 將指標傳回至全域[CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)物件。  
  
```  
CUserToolsManager* GetUserToolsManager();
```  
  
### <a name="return-value"></a>傳回值  
 指標的全域`CUserToolsManager`物件;`NULL`如果使用者工具管理未啟用應用程式。  
  
### <a name="remarks"></a>備註  
 擷取的指標之前`CUserToolsManager`物件時，您必須初始化管理員藉由呼叫[CWinAppEx::EnableUserTools](#enableusertools)。  
  
##  <a name="initcontextmenumanager"></a>CWinAppEx::InitContextMenuManager  
 初始化[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)物件。  
  
```  
BOOL InitContextMenuManager();
```  
  
### <a name="return-value"></a>傳回值  
 方法會建立 CContextMenuManager 物件; 如果為非零0 代表`CContextMenuManager`物件已經存在。  
  
### <a name="remarks"></a>備註  
 如果您呼叫[CWinAppEx::GetContextMenuManager](#getcontextmenumanager)，該方法的預設實作會呼叫`InitContextMenuManager`。  
  
 如果您的應用程式已具有內容功能表管理員，而且您呼叫`InitContextMenuManager`，您的應用程式[ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)失敗。 因此，您不應該呼叫`InitContextMenuManager`如果您建立`CContextMenuManager`直接物件。 如果您不想要使用自訂`CContextMenuManager`，您應該使用`GetContextMenuManager`建立`CContextMenuManager`物件。  
  
##  <a name="initkeyboardmanager"></a>CWinAppEx::InitKeyboardManager  
 初始化[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)物件。  
  
```  
BOOL InitKeyboardManager();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法會建立為非零`CKeyboardManager`物件，就是 0`CKeyboardManager`物件已經存在。  
  
### <a name="remarks"></a>備註  
 如果您呼叫[CWinAppEx::GetKeyboardManager](#getkeyboardmanager)，該方法的預設實作會呼叫`InitKeyboardManager`。  
  
 如果您的應用程式已經有鍵盤管理員，而且您呼叫`InitKeyboardManager`，您的應用程式[ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)失敗。 因此，您不應該呼叫`InitKeyboardManager`如果您建立`CKeyboardManager`直接物件。 如果您不想要使用自訂`CKeyboardManager`，您應該使用`GetKeyboardManager`建立`CKeyboardManager`物件。  
  
##  <a name="initmousemanager"></a>CWinAppEx::InitMouseManager  
 初始化[CMouseManager](../../mfc/reference/cmousemanager-class.md)物件。  
  
```  
BOOL InitMouseManager();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法會建立為非零`CMouseManager`物件，就是 0`CMouseManager`物件已經存在。  
  
### <a name="remarks"></a>備註  
 如果您呼叫[CWinAppEx::GetMouseManager](#getmousemanager)，該方法的預設實作會呼叫`InitMouseManager`。  
  
 如果您的應用程式已經有滑鼠管理員，而且您呼叫`InitMouseManager`，您的應用程式[ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)失敗。 因此您不應該呼叫`InitMouseManager`如果您建立`CMouseManager`直接物件。 如果您不想要使用自訂`CMouseManager`，您應該使用`GetMouseManager`建立`CMouseManager`物件。  
  
##  <a name="initshellmanager"></a>CWinAppEx::InitShellManager  
 初始化[CShellManager](../../mfc/reference/cshellmanager-class.md)物件。  
  
```  
BOOL InitShellManager();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法會建立為非零`CShellManager`物件，就是 0`CShellManager`物件已經存在。  
  
### <a name="remarks"></a>備註  
 如果您呼叫[CWinAppEx::GetShellManager](#getshellmanager)，該方法的預設實作會呼叫`InitShellManager`。  
  
 如果您的應用程式已經有殼層管理員，而且您呼叫`InitShellManager`，應用程式引發[ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)失敗。 因此，請勿呼叫`InitShellManager`如果您建立`CShellManager`直接物件。 如果您不想要使用自訂`CShellManager`，使用`GetShellManager`建立`CShellManager`物件。  
  
##  <a name="inittooltipmanager"></a>CWinAppEx::InitTooltipManager  
 初始化[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)物件。  
  
```  
BOOL InitTooltipManager();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法會建立為非零`CTooltipManager`物件，就是 0`CTooltipManager`物件已經存在。  
  
### <a name="remarks"></a>備註  
 如果您呼叫[CWinAppEx::GetTooltipManager](#gettooltipmanager)，該方法的預設實作會呼叫`InitTooltipManager`。  
  
 如果您的應用程式中已有工具提示管理員，而且您呼叫`InitTooltipManager`，您的應用程式[ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)失敗。 因此，您不應該呼叫`InitTooltipManager`如果您建立`CTooltipManager`直接物件。 如果您不想要使用自訂`CTooltipManager`，您應該使用`GetTooltipManager`建立`CTooltipManager`物件。  
  
##  <a name="isresourcesmartupdate"></a>CWinAppEx::IsResourceSmartUpdate  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsResourceSmartUpdate() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="isstateexists"></a>CWinAppEx::IsStateExists  
 指出是否在登錄中指定的索引鍵。  
  
```  
BOOL IsStateExists(LPCTSTR lpszSectionName);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszSectionName`  
 字串，其中包含的登錄機碼路徑。  
  
### <a name="return-value"></a>傳回值  
 如果在登錄機碼，非零值。否則為 0。  
  
##  <a name="loadcustomstate"></a>CWinAppEx::LoadCustomState  
 它會從登錄載入的應用程式狀態之後，架構會呼叫這個方法。  
  
```  
virtual void LoadCustomState();
```  
  
### <a name="remarks"></a>備註  
 如果您想要進行任何處理應用程式從登錄載入狀態之後，請覆寫這個方法。 根據預設，這個方法沒有作用。  
  
 若要從登錄載入的自訂狀態資訊，必須先儲存資訊使用[CWinAppEx::SaveCustomState](#savecustomstate)。  
  
##  <a name="loadstate"></a>CWinAppEx::LoadState  
 從 Windows 登錄中讀取應用程式的狀態。  
  
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
 框架視窗物件的指標。 方法會套用至這個框架視窗的登錄中的狀態資訊。  
  
 [in] `lpszSectionName`  
 字串，包含相對路徑的登錄機碼。  
  
 [in] `pFrameImpl`  
 指標`CFrameImpl`物件。 方法會套用至這個框架視窗的登錄中的狀態資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會載入應用程式和框架視窗的任何狀態資訊的狀態。 框架視窗的載入的資訊會套用至所提供的框架視窗。 如果未提供框架視窗，只將應用程式的狀態資訊會載入。 應用程式資訊包含狀態[CMouseManager 類別](../../mfc/reference/cmousemanager-class.md)， [CContextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)， [CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)，而[CUserToolsManager 類別](../../mfc/reference/cusertoolsmanager-class.md)。  
  
 預設實作`CFrameImpl::OnLoadFrame`呼叫`LoadState`。  
  
 `lpszSectionName`參數不是絕對路徑的登錄項目。 它是相對路徑新增至您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
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
 矩形，其中包含的主框架視窗座標中的還原位置時。  
  
 [輸出] `nFlags`  
 旗標，控制作業系統會還原的視窗最小化的視窗之間切換的方式和 最小化的視窗的位置。  
  
 [輸出] `nShowCmd`  
 整數，指定視窗的顯示狀態。 如需可能值的詳細資訊，請參閱[CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 根據預設，MFC 會自動載入主框架視窗的狀態與前一個位置的應用程式啟動時。 如需如何在登錄中儲存此資訊的詳細資訊，請參閱[CWinAppEx::StoreWindowPlacement](#storewindowplacement)。  
  
 如果您想要載入的主框架視窗的其他資訊，請覆寫這個方法。  
  
##  <a name="m_bforceimagereset"></a>CWinAppEx::m_bForceImageReset  
 指定當您重新載入專案框架視窗，其中包含工具列架構是否重設所有的工具列影像。  
  
```  
BOOL m_bForceImageReset;  
```  
  
### <a name="remarks"></a>備註  
 `m_bForceImageReset`資料成員是受保護的變數。  
  
##  <a name="onappcontexthelp"></a>CWinAppEx::OnAppContextHelp  
 當使用者要求內容的說明，架構會呼叫這個方法**自訂**對話方塊。  
  
```  
virtual void OnAppContextHelp(
    CWnd* pWndControl,  
    const DWORD dwHelpIDArray[]);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndControl`  
 使用者叫用內容輔助說明 視窗中物件的指標。  
  
 [in] `dwHelpIDArray[]`  
 保留的值。  
  
### <a name="remarks"></a>備註  
 這個方法目前被保留供未來使用。 預設實作不做任何動作，它目前不由呼叫架構。  
  
##  <a name="onclosingmainframe"></a>CWinAppEx::OnClosingMainFrame  
 處理框架視窗時，架構會呼叫這個方法`WM_CLOSE`。  
  
```  
virtual void OnClosingMainFrame(CFrameImpl* pFrameImpl);
```  
  
### <a name="parameters"></a>參數  
 [in] `pFrameImpl`  
 指標`CFrameImpl`物件。  
  
### <a name="remarks"></a>備註  
 這個方法的預設實作會將儲存的狀態`pFrameImpl`。  
  
##  <a name="onviewdoubleclick"></a>CWinAppEx::OnViewDoubleClick  
 呼叫使用者定義的命令是與檢視相關聯，當使用者按兩下該檢視中的任何位置。  
  
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
 `True`如果架構發現命令。否則為 false。  
  
### <a name="remarks"></a>備註  
 為了支援自訂的滑鼠行為，您必須呼叫此函式處理時`WM_LBUTTONDBLCLK`訊息。 這個方法會執行命令所提供的檢視表識別碼相關聯`iViewId`。 如需自訂滑鼠行為的詳細資訊，請參閱[鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)。  
  
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
 它會從登錄載入的應用程式狀態之前，架構會呼叫這個方法。  
  
```  
virtual void PreLoadState();
```  
  
### <a name="remarks"></a>備註  
 如果您想要進行任何處理架構便會載入應用程式的狀態之前，請覆寫這個方法。  
  
##  <a name="presavestate"></a>CWinAppEx::PreSaveState  
 它會將儲存應用程式的狀態之前，架構會呼叫這個方法。  
  
```  
virtual void PreSaveState();
```  
  
### <a name="remarks"></a>備註  
 如果您想要進行任何處理，架構會將儲存應用程式的狀態之前，請覆寫這個方法。  
  
##  <a name="reloadwindowplacement"></a>CWinAppEx::ReloadWindowPlacement  
 重新載入的大小和位置的登錄中的視窗。  
  
```  
virtual BOOL ReloadWindowPlacement(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>參數  
 [in] `pFrame`  
 框架視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則為非零0，表示載入失敗，或是沒有載入任何資料。  
  
### <a name="remarks"></a>備註  
 使用函數[CWinAppEx::StoreWindowPlacement](#storewindowplacement)寫入登錄的大小和視窗的位置。  
  
##  <a name="savecustomstate"></a>CWinAppEx::SaveCustomState  
 它會將儲存到登錄應用程式的狀態之後，架構會呼叫這個方法。  
  
```  
virtual void SaveCustomState();
```  
  
### <a name="remarks"></a>備註  
 如果您想要進行任何處理應用程式會將狀態儲存至登錄之後，請覆寫這個方法。 根據預設，這個方法沒有作用。  
  
##  <a name="savestate"></a>CWinAppEx::SaveState  
 應用程式的狀態寫入 Windows 登錄中。  
  
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
 指標`CFrameImpl`物件。 此範圍會儲存至 Windows 登錄。  
  
 [in] `pFrame`  
 框架視窗物件的指標。 此範圍會儲存至 Windows 登錄。  
  
### <a name="return-value"></a>傳回值  
 `True`如果登錄成功。，`false`否則。  
  
### <a name="remarks"></a>備註  
 這個方法會儲存應用程式和提供的框架視窗的任何狀態資訊的狀態。 如果未提供框架視窗，此方法只會儲存應用程式狀態。 應用程式資訊包含狀態[CMouseManager 類別](../../mfc/reference/cmousemanager-class.md)， [CContextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)， [CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)，而[CUserToolsManager 類別](../../mfc/reference/cusertoolsmanager-class.md)。  
  
 `lpszSectionName`參數不是絕對路徑的登錄項目。 它是相對路徑附加至您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
##  <a name="setregistrybase"></a>CWinAppEx::SetRegistryBase  
 設定應用程式的預設登錄路徑。  
  
```  
LPCTSTR SetRegistryBase(LPCTSTR lpszSectionName = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszSectionName`  
 字串，其中包含的登錄機碼路徑。  
  
### <a name="return-value"></a>傳回值  
 字串，包含預設登錄位置的路徑。  
  
### <a name="remarks"></a>備註  
 所有的方法[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)，存取在預設位置的登錄開始。 若要變更該預設登錄位置中使用這個方法。 使用[CWinAppEx::GetRegistryBase](#getregistrybase)擷取預設登錄位置。  
  
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
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)螢幕座標中指定的功能表上的位置。  
  
 [in] `pWnd`  
 主控的快顯功能表之視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 非零，如果快顯功能表會顯示可順利啟動。否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會顯示相關聯的功能表`uiMenuResId`。  
  
 若要支援快顯功能表，您必須擁有[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)物件。 如果您未初始化`CContextMenuManager`物件，`ShowPopupMenu`將會失敗。  
  
##  <a name="storewindowplacement"></a>CWinAppEx::StoreWindowPlacement  
 寫入登錄的大小和位置的主框架視窗的架構所呼叫。  
  
```  
virtual BOOL StoreWindowPlacement(
    const CRect& rectNormalPosition,  
    int nFlags,  
    int nShowCmd);
```  
  
### <a name="parameters"></a>參數  
 [in] `nFlags`  
 旗標，控制作業系統會還原的視窗最小化的視窗之間切換的方式和 最小化的視窗的位置。  
  
 [in] `nShowCmd`  
 整數，指定視窗的顯示狀態。 如需可能值的詳細資訊，請參閱[CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)。  
  
 [in] `rectNormalPosition`  
 矩形，包含在主框架視窗的座標時處於還原狀態。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 根據預設，MFC 會自動儲存的位置和應用程式結束前的主框架視窗的狀態。 這項資訊會儲存在 Windows 登錄 WindowPlacement 機碼的預設登錄位置中，您的應用程式。 如需您的應用程式的預設登錄位置的詳細資訊，請參閱[CWinAppEx::GetRegistryBase](#getregistrybase)。  
  
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
 字串，其中包含的登錄機碼名稱。  
  
 [in] `pData`  
 要儲存的資料。  
  
 [in] `nBytes`  
 大小`pData`以位元組為單位。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 `lpszEntry`參數就是位於您的應用程式的預設登錄機碼下的登錄項目名稱。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
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
 字串，其中包含的登錄機碼名稱。  
  
 [in] `nValue`  
 要儲存的資料。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 `lpszEntry`參數就是位於您的應用程式的預設登錄機碼底下的登錄項目名稱。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
 如果所指定的索引鍵`lpszEntry`不存在，這個方法會建立它。  
  
##  <a name="writeobject"></a>CWinAppEx::WriteObject  
 將資料衍生自[CObject 類別](../../mfc/reference/cobject-class.md)登錄。  
  
```  
BOOL WriteObject(
    LPCTSTR lpszEntry,  
    CObject& obj);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszEntry`  
 字串，包含要設定的值。  
  
 [in] `obj`  
 參考`CObject`方法會將儲存的資料。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會寫入`obj`預設登錄機碼底下指定的值的資料。 使用[CWinAppEx::GetRegistryBase](#getregistrybase)來判斷目前的登錄機碼。  
  
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
 `lpszSubSection`參數不是絕對路徑的登錄項目。 它是相對路徑附加至您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
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
 `lpszSubSection`參數不是絕對路徑的登錄項目。 它會附加至您的應用程式的預設登錄機碼的相對路徑。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
 如果所指定的索引鍵`lpszEntry`不存在，這個方法會建立它。  
  
##  <a name="writesectionobject"></a>CWinAppEx::WriteSectionObject  
 將資料衍生自[CObject 類別](../../mfc/reference/cobject-class.md)特定登錄值。  
  
```  
BOOL WriteSectionObject(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    CObject& obj);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszSubSection`  
 字串，其中包含的登錄機碼名稱。  
  
 [in] `lpszEntry`  
 字串，其中包含要設定的值名稱。  
  
 [in] `obj`  
 要儲存的資料。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 `lpszSubSection`參數不是絕對路徑的登錄項目。 它是相對路徑附加至您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
 如果所指定的值`lpszEntry`所指定的登錄機碼下沒有`lpszSubSection`，這個方法會建立該值。  
  
##  <a name="writesectionstring"></a>CWinAppEx::WriteSectionString  
 將字串資料，寫入登錄中的值。  
  
```  
BOOL WriteSectionString(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    LPCTSTR lpszValue);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszSubSection`  
 字串，其中包含的登錄機碼名稱。  
  
 [in] `lpszEntry`  
 字串，包含要設定的值。  
  
 [in] `lpszValue`  
 要寫入登錄的字串資料。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 `lpszSubSection`參數不是絕對路徑的登錄項目。 它是相對路徑附加至您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
 如果所指定的值`lpszEntry`下沒有`lpszSubSection`，這個方法會建立它。  
  
##  <a name="writestring"></a>CWinAppEx::WriteString  
 將字串資料，寫入登錄。  
  
```  
BOOL WriteString(
    LPCTSTR lpszEntry,  
    LPCTSTR lpszValue);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszEntry`  
 字串，其中包含的登錄機碼名稱。  
  
 [in] `lpszValue`  
 要儲存的資料。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 `lpszEntry`參數就是位於您的應用程式的預設登錄機碼底下的登錄項目名稱。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分別。  
  
 如果所指定的索引鍵`lspzEntry`不存在，這個方法會建立它。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CWinApp 類別](../../mfc/reference/cwinapp-class.md)   
 [CMouseManager 類別](../../mfc/reference/cmousemanager-class.md)   
 [CContextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)   
 [CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)   
 [CUserToolsManager 類別](../../mfc/reference/cusertoolsmanager-class.md)

