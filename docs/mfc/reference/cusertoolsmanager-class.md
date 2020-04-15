---
title: CUserToolsManager 類別
ms.date: 11/04/2016
f1_keywords:
- CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CreateNewTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::FindTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetArgumentsMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetFilter
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetInitialDirMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetMaxTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetToolsEntryCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetUserTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::InvokeTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::IsUserToolCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::LoadState
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolDown
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolUp
- AFXUSERTOOLSMANAGER/CUserToolsManager::RemoveTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::SaveState
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetFilter
helpviewer_keywords:
- CUserToolsManager [MFC], CUserToolsManager
- CUserToolsManager [MFC], CreateNewTool
- CUserToolsManager [MFC], FindTool
- CUserToolsManager [MFC], GetArgumentsMenuID
- CUserToolsManager [MFC], GetDefExt
- CUserToolsManager [MFC], GetFilter
- CUserToolsManager [MFC], GetInitialDirMenuID
- CUserToolsManager [MFC], GetMaxTools
- CUserToolsManager [MFC], GetToolsEntryCmd
- CUserToolsManager [MFC], GetUserTools
- CUserToolsManager [MFC], InvokeTool
- CUserToolsManager [MFC], IsUserToolCmd
- CUserToolsManager [MFC], LoadState
- CUserToolsManager [MFC], MoveToolDown
- CUserToolsManager [MFC], MoveToolUp
- CUserToolsManager [MFC], RemoveTool
- CUserToolsManager [MFC], SaveState
- CUserToolsManager [MFC], SetDefExt
- CUserToolsManager [MFC], SetFilter
ms.assetid: bdfa37ae-efca-4616-abb5-9d0dcd2d335b
ms.openlocfilehash: c1f14657350c08679868299ce4878cca2ae10eec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373230"
---
# <a name="cusertoolsmanager-class"></a>CUserToolsManager 類別

維護應用程式中[CUserTool 類](../../mfc/reference/cusertool-class.md)物件的集合。 使用者工具是執行外部應用程式的功能表項目。 `CUserToolsManager` 物件可讓使用者或開發人員將新的使用者工具加入至應用程式。 它支援執行與使用者工具相關聯的命令，也會在 Windows 登錄中儲存使用者工具的相關資訊。

## <a name="syntax"></a>語法

```
class CUserToolsManager : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[使用者工具管理員::使用者工具管理員](#cusertoolsmanager)|建構 `CUserToolsManager`。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[使用者工具管理員:建立新工具](#createnewtool)|創建新的使用者工具。|
|[使用者工具管理員::尋找工具](#findtool)|返回指向與指定命令`CMFCUserTool`ID 關聯的物件的指標。|
|[設定工具管理員::取得參數選單ID](#getargumentsmenuid)|傳回與 **「自訂」** 對話方塊「**工具**」 選項卡上的 **「參數」** 選單關聯的資源 ID。|
|[使用者工具管理員::取得DefExt](#getdefext)|傳回**檔案開啟**對話框( [CFileDialog)](../../mfc/reference/cfiledialog-class.md#cfiledialog)在 **「自訂**」對話方塊「**工具**」選項卡上的 **「指令**」欄位中使用的預設副檔名。|
|[使用者工具管理員::取得過濾器](#getfilter)|傳回**檔案開啟**對話框 ( [CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)) 在 **「自訂**」對話框「**工具」** 選項卡上的 **「命令**」欄位中使用的檔案篩選器。|
|[設定工具管理員::取得初始DirMenuID](#getinitialdirmenuid)|傳回與 **「自訂」** 對話方塊「**工具**」 選項卡上 **「 初始目錄」** 選單關聯的資源 ID。|
|[使用者工具管理員::取得MaxTools](#getmaxtools)|返回可在應用程式中分配的最大使用者工具數。|
|[使用者工具管理員::取得工具入口 Cmd](#gettoolsentrycmd)|返回使用者工具的功能表項占位符的命令 ID。|
|[使用者工具管理員:取得使用者工具](#getusertools)|返回對使用者工具清單的引用。|
|[使用者工具管理員::呼叫工具](#invoketool)|執行與具有指定命令 ID 的使用者工具關聯的應用程式。|
|[使用者工具管理員::使用者工具Cmd](#isusertoolcmd)|確定命令 ID 是否與使用者工具關聯。|
|[使用者工具管理員::載入狀態](#loadstate)|從 Windows 註冊表載入有關使用者工具的資訊。|
|[使用者工具管理員:行動工具向下](#movetooldown)|在使用者工具清單中向下移動指定的使用者工具。|
|[使用者工具管理員:行動工具](#movetoolup)|在使用者工具清單中向上移動指定的使用者工具。|
|[使用者工具管理員::刪除工具](#removetool)|從應用程式中刪除指定的使用者工具。|
|[CUserTools 管理員::儲存狀態](#savestate)|在 Windows 註冊表中存儲有關使用者工具的資訊。|
|[使用者工具管理員::SetDefExt](#setdefext)|指定 **「檔案開啟**」對話框[(CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)) 在 **「自訂**」對話方塊「**工具**」選項卡上的 **「命令**」欄位中使用的預設副檔名。|
|[使用者工具管理員::設定篩選器](#setfilter)|指定**檔案**開啟對話框 ( [CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)) 在 **「自訂**」對話框「**工具」** 選項卡上的 **「命令**」欄位中使用的檔案篩選器。|

## <a name="remarks"></a>備註

要將使用者工具合併到應用程式中,您必須:

1. 為使用者工具功能表條目保留功能表項和關聯的命令 ID。

2. 為用戶可以在應用程式中定義的每個使用者工具保留順序命令 ID。

3. 呼叫[CWinAppEx:啟用 UserTools](../../mfc/reference/cwinappex-class.md#enableusertools)方法並提供以下參數:選單命令 ID、第一個使用者工具命令 ID 和最後一個使用者工具命令 ID。

每個應用程式應只有一個`CUserToolsManager`全域物件。

有關使用者工具的範例,請參閱 VisualStudioDemo 範例專案。

## <a name="example"></a>範例

下面的範例展示如何檢索對`CUserToolsManager`物件的引用以及如何創建新的使用者工具。 此代碼段是[可視化工作室演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CUserToolsManager`

## <a name="requirements"></a>需求

**標題:** afxuser工具管理員.h

## <a name="cusertoolsmanagercreatenewtool"></a><a name="createnewtool"></a>使用者工具管理員:建立新工具

創建新的使用者工具。

```
CUserTool* CreateNewTool();
```

### <a name="return-value"></a>傳回值

指向新創建的使用者工具的指標,如果使用者工具數超過最大值,則指向 NULL。 返回的類型與傳遞給`CWinAppEx::EnableUserTools` *pToolRTC*參數的類型相同。

### <a name="remarks"></a>備註

此方法查找[CWinAppEx::啟用 UserTools](../../mfc/reference/cwinappex-class.md#enableusertools)並在調用中提供的範圍中提供的第一個可用功能表命令 ID,並分配此 ID 的使用者工具。

如果工具數已達到最大值,則該方法將失敗。 當將範圍內的所有命令指示指定給使用者工具時,將發生這種情況。 您可以通過呼叫[CUserToolsManager 檢索工具的最大數量::GetMaxTools](#getmaxtools)。 您可以通過調用[CUserToolsManager:::getUserTools](#getusertools)方法存取工具清單。

## <a name="cusertoolsmanagercusertoolsmanager"></a><a name="cusertoolsmanager"></a>使用者工具管理員::使用者工具管理員

建構 `CUserToolsManager`。 每個應用程式必須最多有一個使用者工具管理器。

```
CUserToolsManager();

CUserToolsManager(
    const UINT uiCmdToolsDummy,
    const UINT uiCmdFirst,
    const UINT uiCmdLast,
    CRuntimeClass* pToolRTC=RUNTIME_CLASS(CUserTool),
    UINT uArgMenuID=0,
    UINT uInitDirMenuID=0);
```

### <a name="parameters"></a>參數

*uiCmdToolsDummy*<br/>
[在]框架用作使用者工具功能表的命令 ID 的占位符的無符號整數。

*uiCmdFirst*<br/>
[在]第一個使用者工具命令的命令 ID。

*uiCmdLast*<br/>
[在]最後一個使用者工具命令的命令 ID。

*pToolRTC*<br/>
[在][CUserToolsManager:創建新工具](#createnewtool)創建的類。 通過使用此類,可以使用派生類型的[CUserTool 類](../../mfc/reference/cusertool-class.md)而不是預設實現。

*uArgMenuID*<br/>
[在]參數彈出功能表的功能表資源 ID。

*烏伊尼特迪爾梅尼*<br/>
[在]初始目錄彈出功能表的功能表資源 ID。

### <a name="remarks"></a>備註

不要調用此構造函數。 相反,調用[CWinAppEx::啟用使用者工具](../../mfc/reference/cwinappex-class.md#enableusertools)以啟用使用者工具,並調用[CWinAppEx::getUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager)以獲取指向`CUserToolsManager`的指標。 有關詳細資訊,請參閱[使用者定義的工具](../../mfc/user-defined-tools.md)。

## <a name="cusertoolsmanagerfindtool"></a><a name="findtool"></a>使用者工具管理員::尋找工具

返回指向與指定命令 ID 關聯的[CUserTool 類](../../mfc/reference/cusertool-class.md)物件的指標。

```
CUserTool* FindTool(UINT uiCmdId) const;
```

### <a name="parameters"></a>參數

*烏伊CmDId*<br/>
[在]功能表命令識別碼。

### <a name="return-value"></a>傳回值

指向[CUserTool](../../mfc/reference/cusertool-class.md)`CUserTool`類 或 派生物件的指標(如果成功);否則 NULL。

### <a name="remarks"></a>備註

成功`FindTool`後,傳回的類型與 CWinAppEx*的 pToolRTC*參數類型相同[::啟用使用者工具](../../mfc/reference/cwinappex-class.md#enableusertools)。

## <a name="cusertoolsmanagergetargumentsmenuid"></a><a name="getargumentsmenuid"></a>設定工具管理員::取得參數選單ID

傳回與 **「自訂」** 對話方塊「**工具**」 選項卡上的 **「參數」** 選單關聯的資源 ID。

```
UINT GetArgumentsMenuID() const;
```

### <a name="return-value"></a>傳回值

功能表資源的標識碼。

### <a name="remarks"></a>備註

[CWinAppEx 的](../../mfc/reference/cwinappex-class.md#enableusertools) *uArgMenuID*參數:啟用使用者工具指定資源的 ID。

## <a name="cusertoolsmanagergetdefext"></a><a name="getdefext"></a>使用者工具管理員::取得DefExt

傳回**檔案開啟**對話框( [CFileDialog)](../../mfc/reference/cfiledialog-class.md#cfiledialog)在 **「自訂**」對話方塊「**工具**」選項卡上的 **「指令**」欄位中使用的預設副檔名。

```
const CString& GetDefExt() const;
```

### <a name="return-value"></a>傳回值

對包含擴展`CString`的物件的引用。

## <a name="cusertoolsmanagergetfilter"></a><a name="getfilter"></a>使用者工具管理員::取得過濾器

傳回**檔案開啟**對話框 ( [CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)) 在 **「自訂**」對話框「**工具」** 選項卡上的 **「命令**」欄位中使用的檔案篩選器。

```
const CString& GetFilter() const;
```

### <a name="return-value"></a>傳回值

對包含篩選器`CString`的物件的引用。

## <a name="cusertoolsmanagergetinitialdirmenuid"></a><a name="getinitialdirmenuid"></a>設定工具管理員::取得初始DirMenuID

傳回與 **「自訂」** 對話方塊「**工具**」 選項卡上 **「 初始目錄」** 選單關聯的資源 ID。

```
UINT GetInitialDirMenuID() const;
```

### <a name="return-value"></a>傳回值

功能表資源標識碼。

### <a name="remarks"></a>備註

傳回的識別碼在 CWinAppEx 的*uInitDirMenuID*參數中指定[:啟用使用者工具](../../mfc/reference/cwinappex-class.md#enableusertools)。

## <a name="cusertoolsmanagergetmaxtools"></a><a name="getmaxtools"></a>使用者工具管理員::取得MaxTools

返回可在應用程式中分配的最大使用者工具數。

```
int GetMaxTools() const;
```

### <a name="return-value"></a>傳回值

可分配的最大使用者工具數。

### <a name="remarks"></a>備註

調用此方法以檢索可在應用程式中分配的最大工具數。 此數字是從*uiCmdFirst*到您傳遞給[CWinAppEx](../../mfc/reference/cwinappex-class.md#enableusertools)的*uiCmdLast*參數範圍內的 ID 數:啟用使用者工具 。

## <a name="cusertoolsmanagergettoolsentrycmd"></a><a name="gettoolsentrycmd"></a>使用者工具管理員::取得工具入口 Cmd

返回使用者工具的功能表項占位符的命令 ID。

```
UINT GetToolsEntryCmd() const;
```

### <a name="return-value"></a>傳回值

占位符的命令 ID。

### <a name="remarks"></a>備註

要啟用使用者工具,請致電[CWinAppEx::啟用使用者工具](../../mfc/reference/cwinappex-class.md#enableusertools)。 *uiCmdToolsDummy*參數指定工具輸入命令的命令 ID。 此方法返回工具條目命令 ID。 無論該 ID 在功能表中使用何處,當功能表出現時,該 ID 將被使用者工具列表替換。

## <a name="cusertoolsmanagergetusertools"></a><a name="getusertools"></a>使用者工具管理員:取得使用者工具

返回對使用者工具清單的引用。

```
const CObList& GetUserTools() const;
```

### <a name="return-value"></a>傳回值

對包含使用者工具清單的[CObList 類](../../mfc/reference/coblist-class.md)物件的引用。

### <a name="remarks"></a>備註

呼叫此方法以檢索[CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)物件維護的使用者工具清單。 每個使用者工具由[CUserTool 類別](../../mfc/reference/cusertool-class.md)類型的物件或派`CUserTool`生自的類型表示。 當您調用[CWinAppEx::啟用使用者工具啟用使用者工具](../../mfc/reference/cwinappex-class.md#enableusertools)時,該類型由*pToolRTC*參數指定。

## <a name="cusertoolsmanagerinvoketool"></a><a name="invoketool"></a>使用者工具管理員::呼叫工具

執行與具有指定命令 ID 的使用者工具關聯的應用程式。

```
BOOL InvokeTool(UINT uiCmdId);
```

### <a name="parameters"></a>參數

*烏伊CmDId*<br/>
[在]與使用者工具關聯的功能表命令 ID。

### <a name="return-value"></a>傳回值

如果成功執行與使用者工具關聯的命令,則非零;否則 0。

### <a name="remarks"></a>備註

呼叫此方法以執行與具有*uiCmdId*指定的命令 ID 的使用者工具關聯的應用程式。

## <a name="cusertoolsmanagerisusertoolcmd"></a><a name="isusertoolcmd"></a>使用者工具管理員::使用者工具Cmd

確定命令 ID 是否與使用者工具關聯。

```
BOOL IsUserToolCmd(UINT uiCmdId) const;
```

### <a name="parameters"></a>參數

*烏伊CmDId*<br/>
[在]功能表項的命令 ID。

### <a name="return-value"></a>傳回值

如果給定的命令 ID 與使用者工具關聯,則非零;否則 0。

### <a name="remarks"></a>備註

此方法檢查給定的命令 ID 是否位於命令 ID 範圍內。 當您呼叫[CWinAppEx 時,您可以指定範圍:啟用使用者工具](../../mfc/reference/cwinappex-class.md#enableusertools)以啟用使用者工具。

## <a name="cusertoolsmanagerloadstate"></a><a name="loadstate"></a>使用者工具管理員::載入狀態

從 Windows 註冊表載入有關使用者工具的資訊。

```
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>參數

*lpsz 設定檔名稱*<br/>
[在]Windows 註冊表項的路徑。

### <a name="return-value"></a>傳回值

如果狀態已成功載入,則非零;否則 0。

### <a name="remarks"></a>備註

此方法從 Windows 註冊表`CUserToolsManager`載入 物件的狀態。

通常,您不會直接調用此方法。 [CWinAppEx:LoadState](../../mfc/reference/cwinappex-class.md#loadstate)將其稱為工作區初始化過程的一部分。

## <a name="cusertoolsmanagermovetooldown"></a><a name="movetooldown"></a>使用者工具管理員:行動工具向下

在使用者工具清單中向下移動指定的使用者工具。

```
BOOL MoveToolDown(CUserTool* pTool);
```

### <a name="parameters"></a>參數

*pTool*<br/>
[在]指定要移動的使用者工具。

### <a name="return-value"></a>傳回值

如果使用者工具已成功向下移動,則非零;否則 0。

### <a name="remarks"></a>備註

如果*pTool*指定的工具不在內部清單中,或者該工具在清單中是最後一個,則該方法將失敗。

## <a name="cusertoolsmanagermovetoolup"></a><a name="movetoolup"></a>使用者工具管理員:行動工具

在使用者工具清單中向上移動指定的使用者工具。

```
BOOL MoveToolUp(CUserTool* pTool);
```

### <a name="parameters"></a>參數

*pTool*<br/>
[在]指定要移動的使用者工具。

### <a name="return-value"></a>傳回值

如果使用者工具成功向上移動,則非零;否則 0。

### <a name="remarks"></a>備註

如果*pTool*參數指定的工具不在內部清單中,或者該工具是清單中的第一個工具項,則該方法將失敗。

## <a name="cusertoolsmanagerremovetool"></a><a name="removetool"></a>使用者工具管理員::刪除工具

從應用程式中刪除指定的使用者工具。

```
BOOL RemoveTool(CUserTool* pTool);
```

### <a name="parameters"></a>參數

*pTool*<br/>
[進出]指向要刪除的使用者工具的指標。

### <a name="return-value"></a>傳回值

如果工具已成功刪除,則為 TRUE。 否則，FALSE。

### <a name="remarks"></a>備註

如果該工具已成功刪除,則此方法將刪除*pTool*。

## <a name="cusertoolsmanagersavestate"></a><a name="savestate"></a>CUserTools 管理員::儲存狀態

在 Windows 註冊表中存儲有關使用者工具的資訊。

```
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>參數

*lpsz 設定檔名稱*<br/>
[在]Windows 註冊表項的路徑。

### <a name="return-value"></a>傳回值

如果成功保存狀態,則非零;否則 0。

### <a name="remarks"></a>備註

該方法在 Windows 註冊表`CUserToolsManager`中儲存 物件的當前狀態。

通常,您不需要直接調用此方法[CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate)自動調用它作為應用程式的工作區序列化過程的一部分。

## <a name="cusertoolsmanagersetdefext"></a><a name="setdefext"></a>使用者工具管理員::SetDefExt

指定 **「檔案開啟**」對話框[(CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)) 在 **「自訂**」對話方塊「**工具**」選項卡上的 **「命令**」欄位中使用的預設副檔名。

```
void SetDefExt(const CString& strDefExt);
```

### <a name="parameters"></a>參數

*斯特德夫克斯*<br/>
[在]包含預設檔案名副檔名的文字字串。

### <a name="remarks"></a>備註

呼叫此方法以在 **「檔案開啟」** 對話方塊中指定預設檔案名副檔名,當使用者選擇要與使用者工具關聯的應用程式時將顯示該對話框。 默認值為"exe"。

## <a name="cusertoolsmanagersetfilter"></a><a name="setfilter"></a>使用者工具管理員::設定篩選器

指定**檔案**開啟對話框 ( [CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)) 在 **「自訂**」對話框「**工具」** 選項卡上的 **「命令**」欄位中使用的檔案篩選器。

```
void SetFilter(const CString& strFilter);
```

### <a name="parameters"></a>參數

*斯特過濾器*<br/>
[在]指定篩選器。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)<br/>
[CUserTool 類別](../../mfc/reference/cusertool-class.md)
