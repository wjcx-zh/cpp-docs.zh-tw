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
ms.openlocfilehash: 405260d4bc2f7cdf163dbd7a00f342b8afc87d48
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668104"
---
# <a name="cusertoolsmanager-class"></a>CUserToolsManager 類別

會維護的集合[CUserTool 類別](../../mfc/reference/cusertool-class.md)應用程式中的物件。 使用者工具是執行外部應用程式的功能表項目。 `CUserToolsManager` 物件可讓使用者或開發人員將新的使用者工具加入至應用程式。 它支援執行與使用者工具相關聯的命令，也會在 Windows 登錄中儲存使用者工具的相關資訊。

## <a name="syntax"></a>語法

```
class CUserToolsManager : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CUserToolsManager::CUserToolsManager](#cusertoolsmanager)|建構 `CUserToolsManager`。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CUserToolsManager::CreateNewTool](#createnewtool)|建立新的使用者工具。|
|[CUserToolsManager::FindTool](#findtool)|傳回的指標`CMFCUserTool`與指定的命令識別碼相關聯的物件|
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|傳回相關聯的資源識別碼**引數**上的功能表**工具**索引標籤**自訂** 對話方塊。|
|[CUserToolsManager::GetDefExt](#getdefext)|傳回預設的延伸模組**開啟舊檔** 對話方塊 ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) 中使用**命令**欄位**工具** 索引標籤**自訂** 對話方塊。|
|[CUserToolsManager::GetFilter](#getfilter)|傳回檔案篩選器**開啟舊檔** 對話方塊 ( [CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**欄位**工具** 索引標籤**自訂** 對話方塊。|
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|傳回相關聯的資源識別碼**初始目錄**上的功能表**工具**索引標籤**自訂** 對話方塊。|
|[CUserToolsManager::GetMaxTools](#getmaxtools)|傳回應用程式中的使用者工具，可配置的最大數目。|
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|傳回使用者工具的功能表項目預留位置的命令識別碼。|
|[CUserToolsManager::GetUserTools](#getusertools)|傳回清單中的使用者工具的參考。|
|[CUserToolsManager::InvokeTool](#invoketool)|執行具有指定的命令識別碼。 此使用者工具相關聯的應用程式|
|[CUserToolsManager::IsUserToolCmd](#isusertoolcmd)|判斷是否與使用者工具相關聯的命令識別碼。|
|[CUserToolsManager::LoadState](#loadstate)|從 Windows 登錄載入使用者工具的相關資訊。|
|[CUserToolsManager::MoveToolDown](#movetooldown)|使用者工具的清單中，向下移動指定的使用者工具。|
|[CUserToolsManager::MoveToolUp](#movetoolup)|在使用者工具的清單中，向上移動指定的使用者工具。|
|[CUserToolsManager::RemoveTool](#removetool)|從應用程式中移除指定的使用者工具。|
|[CUserToolsManager::SaveState](#savestate)|在 Windows 登錄中儲存使用者工具的相關資訊。|
|[CUserToolsManager::SetDefExt](#setdefext)|指定預設的延伸模組所**開啟舊檔** 對話方塊中 ( [CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**欄位**工具** 索引標籤**自訂** 對話方塊。|
|[CUserToolsManager::SetFilter](#setfilter)|指定檔案的篩選條件**開啟舊檔** 對話方塊 ( [CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**欄位**工具** 索引標籤**自訂** 對話方塊。|

## <a name="remarks"></a>備註

若要併入您的應用程式中的使用者工具，您必須：

1. 保留的功能表項目和相關聯的命令 ID 的使用者工具 功能表項目。

2. 保留每個使用者工具，使用者可以定義在您的應用程式中的循序的命令識別碼。

3. 呼叫[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)方法並提供下列參數： 功能表命令識別碼、 第一個使用者工具命令識別碼，以及最後一個使用者工具的命令識別碼。

應該只有一個全域`CUserToolsManager`每個應用程式的物件。

如需使用者工具的範例，請參閱 VisualStudioDemo 範例專案。

## <a name="example"></a>範例

下列範例示範如何擷取參考`CUserToolsManager`物件，以及如何建立新的使用者工具。 此程式碼片段是一部分[Visual Studio 示範範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CUserToolsManager`

## <a name="requirements"></a>需求

**標頭：** afxusertoolsmanager.h

##  <a name="createnewtool"></a>  CUserToolsManager::CreateNewTool

建立新的使用者工具。

```
CUserTool* CreateNewTool();
```

### <a name="return-value"></a>傳回值

新建立的使用者 工具中或如果使用者工具的數目已超過最大值為 NULL 指標。 傳回的型別為型別傳遞至相同`CWinAppEx::EnableUserTools`作為*pToolRTC*參數。

### <a name="remarks"></a>備註

這個方法會尋找第一個可用的功能表命令 ID 來呼叫中提供的範圍內[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)並指派使用者工具，此識別碼。

如果工具的數目已達到最大值，方法將會失敗。 會發生這種情況是當範圍內的所有命令識別碼都指派給使用者工具。 您可以藉由呼叫擷取工具的最大數目[CUserToolsManager::GetMaxTools](#getmaxtools)。 您可以呼叫來取得工具清單的存取權[CUserToolsManager::GetUserTools](#getusertools)方法。

##  <a name="cusertoolsmanager"></a>  CUserToolsManager::CUserToolsManager

建構 `CUserToolsManager`。 每個應用程式必須有最多一位使用者工具管理員。

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
[in]不帶正負號的整數，架構會使用預留位置做為使用者的 [工具] 功能表的命令識別碼。

*uiCmdFirst*<br/>
[in]第一次的 [使用者] 工具命令的命令識別碼。

*uiCmdLast*<br/>
[in]最後的 [使用者] 工具命令的命令識別碼。

*pToolRTC*<br/>
[in]此類別的[CUserToolsManager::CreateNewTool](#createnewtool)建立。 藉由使用這個類別，您可以使用衍生的型別[CUserTool 類別](../../mfc/reference/cusertool-class.md)而不是預設實作。

*uArgMenuID*<br/>
[in]引數快顯功能表的功能表資源識別碼。

*uInitDirMenuID*<br/>
[in]初始目錄快顯功能表的功能表資源識別碼。

### <a name="remarks"></a>備註

請勿呼叫這個建構函式。 請改為呼叫[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)啟用使用者工具，並呼叫[CWinAppEx::GetUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager)若要取得的指標`CUserToolsManager`。 如需詳細資訊，請參閱 <<c0> [ 使用者定義工具](../../mfc/user-defined-tools.md)。

##  <a name="findtool"></a>  CUserToolsManager::FindTool

傳回的指標[CUserTool 類別](../../mfc/reference/cusertool-class.md)與指定的命令識別碼相關聯的物件

```
CUserTool* FindTool(UINT uiCmdId) const;
```

### <a name="parameters"></a>參數

*uiCmdId*<br/>
[in]功能表命令的識別項。

### <a name="return-value"></a>傳回值

指標[CUserTool 類別](../../mfc/reference/cusertool-class.md)或`CUserTool`-衍生物件，如果成功，否則為 NULL。

### <a name="remarks"></a>備註

當`FindTool`會成功，傳回的型別是相同的型別*pToolRTC*參數來[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)。

##  <a name="getargumentsmenuid"></a>  CUserToolsManager::GetArgumentsMenuID

傳回相關聯的資源識別碼**引數**上的功能表**工具**索引標籤**自訂** 對話方塊。

```
UINT GetArgumentsMenuID() const;
```

### <a name="return-value"></a>傳回值

功能表資源的識別項。

### <a name="remarks"></a>備註

*UArgMenuID*的參數[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)指定資源的識別碼。

##  <a name="getdefext"></a>  CUserToolsManager::GetDefExt

傳回預設的延伸模組**開啟舊檔** 對話方塊 ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) 中使用**命令**欄位**工具** 索引標籤**自訂** 對話方塊。

```
const CString& GetDefExt() const;
```

### <a name="return-value"></a>傳回值

參考`CString`物件，其中包含延伸模組。

##  <a name="getfilter"></a>  CUserToolsManager::GetFilter

傳回檔案篩選器**開啟舊檔** 對話方塊 ( [CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**欄位**工具** 索引標籤**自訂** 對話方塊。

```
const CString& GetFilter() const;
```

### <a name="return-value"></a>傳回值

參考`CString`包含篩選條件的物件。

##  <a name="getinitialdirmenuid"></a>  CUserToolsManager::GetInitialDirMenuID

傳回相關聯的資源識別碼**初始目錄**上的功能表**工具**索引標籤**自訂** 對話方塊。

```
UINT GetInitialDirMenuID() const;
```

### <a name="return-value"></a>傳回值

功能表資源的識別項。

### <a name="remarks"></a>備註

傳回的識別碼中指定*uInitDirMenuID*的參數[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)。

##  <a name="getmaxtools"></a>  CUserToolsManager::GetMaxTools

傳回應用程式中的使用者工具，可配置的最大數目。

```
int GetMaxTools() const;
```

### <a name="return-value"></a>傳回值

可配置的使用者工具的數目上限。

### <a name="remarks"></a>備註

呼叫這個方法來擷取可配置在應用程式的工具的最大數目。 這個數字是從範圍中的識別碼數目*uiCmdFirst*透過*uiCmdLast*參數傳遞給[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)。

##  <a name="gettoolsentrycmd"></a>  CUserToolsManager::GetToolsEntryCmd

傳回使用者工具的功能表項目預留位置的命令識別碼。

```
UINT GetToolsEntryCmd() const;
```

### <a name="return-value"></a>傳回值

預留位置的命令識別碼。

### <a name="remarks"></a>備註

若要啟用使用者工具，請呼叫[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)。 *UiCmdToolsDummy*參數指定 [工具] 進入命令的命令識別碼。 這個方法會傳回工具項目的命令識別碼。 只要使用該識別碼，就在功能表中，它會取代使用者工具的清單功能表顯示時。

##  <a name="getusertools"></a>  CUserToolsManager::GetUserTools

傳回清單中的使用者工具的參考。

```
const CObList& GetUserTools() const;
```

### <a name="return-value"></a>傳回值

Const 參考[CObList 類別](../../mfc/reference/coblist-class.md)物件，其中包含一份使用者工具。

### <a name="remarks"></a>備註

呼叫此方法來擷取一份使用者工具[CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)物件會維護。 每個使用者工具由類型的物件[CUserTool 類別](../../mfc/reference/cusertool-class.md)或型別衍生自`CUserTool`。 藉由指定型別*pToolRTC*當您呼叫的參數[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)啟用使用者工具。

##  <a name="invoketool"></a>  CUserToolsManager::InvokeTool

執行具有指定的命令識別碼。 此使用者工具相關聯的應用程式

```
BOOL InvokeTool(UINT uiCmdId);
```

### <a name="parameters"></a>參數

*uiCmdId*<br/>
[in]與使用者工具相關聯的功能表命令識別碼。

### <a name="return-value"></a>傳回值

使用者工具相關聯的命令執行成功; 如果為非零否則為 0。

### <a name="remarks"></a>備註

呼叫此方法才能執行與使用者相關聯的應用程式工具，具有所指定的命令 ID *uiCmdId*。

##  <a name="isusertoolcmd"></a>  CUserToolsManager::IsUserToolCmd

判斷是否與使用者工具相關聯的命令識別碼。

```
BOOL IsUserToolCmd(UINT uiCmdId) const;
```

### <a name="parameters"></a>參數

*uiCmdId*<br/>
[in]功能表項目的命令識別碼。

### <a name="return-value"></a>傳回值

如果指定的命令識別碼相關聯的使用者工具，為非零否則為 0。

### <a name="remarks"></a>備註

這個方法會檢查指定的命令識別碼是否為命令識別碼範圍。 當您呼叫時，指定的範圍[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)啟用使用者工具。

##  <a name="loadstate"></a>  CUserToolsManager::LoadState

從 Windows 登錄載入使用者工具的相關資訊。

```
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
[in]Windows 登錄機碼的路徑。

### <a name="return-value"></a>傳回值

如果已成功; 載入狀態，非零值。否則為 0。

### <a name="remarks"></a>備註

這個方法載入的狀態`CUserToolsManager`從 Windows 登錄的物件。

通常，您無法進行直接呼叫這個方法。 [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate)呼叫它的工作區初始化程序的一部分。

##  <a name="movetooldown"></a>  CUserToolsManager::MoveToolDown

使用者工具的清單中，向下移動指定的使用者工具。

```
BOOL MoveToolDown(CUserTool* pTool);
```

### <a name="parameters"></a>參數

*pTool*<br/>
[in]指定要移動的使用者工具。

### <a name="return-value"></a>傳回值

如果使用者工具已順利移往下，非零值。否則為 0。

### <a name="remarks"></a>備註

方法會失敗，如果此工具， *pTool*指定不在內部清單或如果此工具會在清單中最後一個。

##  <a name="movetoolup"></a>  CUserToolsManager::MoveToolUp

在使用者工具的清單中，向上移動指定的使用者工具。

```
BOOL MoveToolUp(CUserTool* pTool);
```

### <a name="parameters"></a>參數

*pTool*<br/>
[in]指定要移動的使用者工具。

### <a name="return-value"></a>傳回值

如果使用者工具已順利移動為非零否則為 0。

### <a name="remarks"></a>備註

方法會失敗，如果此工具， *pTool*參數會指定不在內部清單或此工具是否在清單中的第一個工具項目。

##  <a name="removetool"></a>  CUserToolsManager::RemoveTool

從應用程式中移除指定的使用者工具。

```
BOOL RemoveTool(CUserTool* pTool);
```

### <a name="parameters"></a>參數

*pTool*<br/>
[in、 out]要移除的使用者工具指標。

### <a name="return-value"></a>傳回值

如果成功移除工具，則為 TRUE。 否則為 FALSE。

### <a name="remarks"></a>備註

如果成功移除工具，這個方法會刪除*pTool*。

##  <a name="savestate"></a>  CUserToolsManager::SaveState

在 Windows 登錄中儲存使用者工具的相關資訊。

```
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
[in]Windows 登錄機碼路徑。

### <a name="return-value"></a>傳回值

如果已成功; 儲存狀態，非零值。否則為 0。

### <a name="remarks"></a>備註

方法會儲存目前的狀態`CUserToolsManager`Windows 登錄中的物件。

通常，您不需要直接呼叫這個方法[CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate)的應用程式工作區序列化程序的一部分自動呼叫它。

##  <a name="setdefext"></a>  CUserToolsManager::SetDefExt

指定預設的延伸模組所**開啟舊檔** 對話方塊中 ( [CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**欄位**工具** 索引標籤**自訂** 對話方塊。

```
void SetDefExt(const CString& strDefExt);
```

### <a name="parameters"></a>參數

*strDefExt*<br/>
[in]文字字串，其中包含預設的副檔名。

### <a name="remarks"></a>備註

呼叫這個方法來指定在預設檔案名稱副檔名**開啟舊檔**對話方塊中，會顯示當使用者選取的使用者工具相關聯的應用程式。 預設值是"exe"。

##  <a name="setfilter"></a>  CUserToolsManager::SetFilter

指定檔案的篩選條件**開啟舊檔** 對話方塊 ( [CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**欄位**工具** 索引標籤**自訂** 對話方塊。

```
void SetFilter(const CString& strFilter);
```

### <a name="parameters"></a>參數

*strFilter*<br/>
[in]指定的篩選器。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)<br/>
[CUserTool 類別](../../mfc/reference/cusertool-class.md)
