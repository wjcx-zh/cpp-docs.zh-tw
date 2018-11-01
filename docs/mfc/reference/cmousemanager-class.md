---
title: CMouseManager 類別
ms.date: 11/04/2016
f1_keywords:
- CMouseManager
- AFXMOUSEMANAGER/CMouseManager
- AFXMOUSEMANAGER/CMouseManager::AddView
- AFXMOUSEMANAGER/CMouseManager::GetViewDblClickCommand
- AFXMOUSEMANAGER/CMouseManager::GetViewIconId
- AFXMOUSEMANAGER/CMouseManager::GetViewIdByName
- AFXMOUSEMANAGER/CMouseManager::GetViewNames
- AFXMOUSEMANAGER/CMouseManager::LoadState
- AFXMOUSEMANAGER/CMouseManager::SaveState
- AFXMOUSEMANAGER/CMouseManager::SetCommandForDblClk
helpviewer_keywords:
- CMouseManager [MFC], AddView
- CMouseManager [MFC], GetViewDblClickCommand
- CMouseManager [MFC], GetViewIconId
- CMouseManager [MFC], GetViewIdByName
- CMouseManager [MFC], GetViewNames
- CMouseManager [MFC], LoadState
- CMouseManager [MFC], SaveState
- CMouseManager [MFC], SetCommandForDblClk
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
ms.openlocfilehash: b3c5104038e6d715977a211af5a535cc9a5d916f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498146"
---
# <a name="cmousemanager-class"></a>CMouseManager 類別

可讓使用者建立不同的命令與特定的關聯[CView](../../mfc/reference/cview-class.md)物件的使用者在該檢視內部按兩下時。

## <a name="syntax"></a>語法

```
class CMouseManager : public CObject
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMouseManager::AddView](#addview)|新增`CView`物件至**自訂** 對話方塊。 **自訂**對話方塊可讓使用者按兩下關聯的命令，針對每個列出的檢視。|
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|傳回使用者在提供的檢視內部按兩下時，所執行的命令。|
|[CMouseManager::GetViewIconId](#getviewiconid)|傳回與提供的檢視識別碼相關聯的圖示|
|[CMouseManager::GetViewIdByName](#getviewidbyname)|傳回提供的檢視名稱相關聯的檢視識別碼。|
|[CMouseManager::GetViewNames](#getviewnames)|擷取所有已加入的檢視名稱的清單。|
|[CMouseManager::LoadState](#loadstate)|載入`CMouseManager`狀態從 Windows 登錄。|
|[CMouseManager::SaveState](#savestate)|寫入`CMouseManager`狀態到 Windows 登錄。|
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|將提供的命令，並提供的檢視。|

## <a name="remarks"></a>備註

`CMouseManager`類別會負責維護的集合`CView`物件。 每個檢視被識別由名稱和識別碼。 這些檢視表所示**自訂** 對話方塊。 使用者可以變更與透過任何檢視相關聯的命令**自訂** 對話方塊。 當使用者按兩下該檢視中，會執行相關聯的命令。 若要支援此功能從程式碼撰寫的觀點來看，您必須處理需要知道 WM_LBUTTONDBLCLK 訊息並呼叫[CWinAppEx::OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick)函式的程式碼中`CView`物件...

您不應建立`CMouseManager`手動物件。 它會建立您的應用程式的架構。 它也將被終結自動當使用者結束應用程式。 若要取得至滑鼠管理員的指標，您的應用程式，請呼叫[CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMouseManager`

## <a name="requirements"></a>需求

**標頭：** afxmousemanager.h

##  <a name="addview"></a>  CMouseManager::AddView

註冊[CView](../../mfc/reference/cview-class.md)物件[CMouseManager 類別](../../mfc/reference/cmousemanager-class.md)以支援自訂的滑鼠行為。

```
BOOL AddView(
    int iViewId,
    UINT uiViewNameResId,
    UINT uiIconId = 0);

BOOL AddView(
    int iId,
    LPCTSTR lpszViewName,
    UINT uiIconId = 0);
```

### <a name="parameters"></a>參數

*iViewId*<br/>
[in]檢視識別碼。

*uiViewNameResId*<br/>
[in]參考的檢視表名稱的資源字串識別碼。

*uiIconId*<br/>
[in]檢視圖示識別碼。

*iId*<br/>
[in]檢視識別碼。

*lpszViewName*<br/>
[in]檢視名稱。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

若要支援自訂的滑鼠行為，檢視必須向`CMouseManager`物件。 任何物件衍生自`CView`類別可以向滑鼠管理員。 字串和檢視表相關聯的圖示會顯示在**滑鼠**索引標籤**自訂** 對話方塊。

建立和維護檢視識別碼，例如，程式設計師負責*iViewId*並*iId*。

如需如何提供自訂的滑鼠行為的詳細資訊，請參閱[鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)。

### <a name="example"></a>範例

下列範例示範如何擷取變數的指標，`CMouseManager`使用的物件`CWinAppEx::GetMouseManager`方法並`AddView`方法中的`CMouseManager`類別。 此程式碼片段是一部分[狀態集合範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]

##  <a name="getviewdblclickcommand"></a>  CMouseManager::GetViewDblClickCommand

傳回使用者在提供的檢視內部按兩下時，所執行的命令。

```
UINT GetViewDblClickCommand(int iId) const;
```

### <a name="parameters"></a>參數

*iId*<br/>
[in]檢視識別碼。

### <a name="return-value"></a>傳回值

如果檢視是相關聯的命令; 命令識別碼否則為 0。

##  <a name="getviewiconid"></a>  CMouseManager::GetViewIconId

擷取與檢視識別碼相關聯的圖示

```
UINT GetViewIconId(int iViewId) const;
```

### <a name="parameters"></a>參數

*iViewId*<br/>
[in]檢視識別碼。

### <a name="return-value"></a>傳回值

如果成功則圖示資源識別碼否則為 0。

### <a name="remarks"></a>備註

如果檢視未使用第一次註冊，這個方法將會失敗[CMouseManager::AddView](#addview)。

##  <a name="getviewidbyname"></a>  CMouseManager::GetViewIdByName

擷取與檢視名稱相關聯的檢視識別碼。

```
int GetViewIdByName(LPCTSTR lpszName) const;
```

### <a name="parameters"></a>參數

*lpszName*<br/>
[in]檢視名稱。

### <a name="return-value"></a>傳回值

如果成功則檢視表識別碼否則為 0。

### <a name="remarks"></a>備註

這個方法會透過使用註冊的檢視搜尋[CMouseManager::AddView](#addview)。

##  <a name="getviewnames"></a>  CMouseManager::GetViewNames

擷取所有已註冊的檢視名稱的清單。

```
void GetViewNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>參數

*listOfNames*<br/>
[out]參考`CStringList`物件。

### <a name="remarks"></a>備註

這個方法會填入參數`listOfNames`使用註冊的所有檢視的名稱[CMouseManager::AddView](#addview)。

##  <a name="loadstate"></a>  CMouseManager::LoadState

載入的狀態[CMouseManager 類別](../../mfc/reference/cmousemanager-class.md)從登錄。

```
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
[in]登錄機碼的路徑。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

從登錄載入狀態資訊會包括已註冊的檢視，檢視識別項，以及相關聯的命令。 如果參數*lpszProfileName*是 NULL，此函式會載入`CMouseManager`所控制的預設登錄位置的資料[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)。

在大部分情況下，您不必直接呼叫此函式。 它稱為工作區初始化程序的一部分。 如需工作區初始化程序的詳細資訊，請參閱[CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate)。

##  <a name="savestate"></a>  CMouseManager::SaveState

寫入的狀態[CMouseManager 類別](../../mfc/reference/cmousemanager-class.md)至登錄。

```
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
[in]登錄機碼的路徑。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

寫入登錄的狀態資訊包括所有已註冊的檢視，檢視識別項，以及相關聯的命令。 如果參數*lpszProfileName*是 NULL，此函式會寫入`CMouseManager`所控制的預設登錄位置的資料[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)。

在大部分情況下，您不必直接呼叫此函式。 它稱為工作區序列化程序的一部分。 如需工作區序列化程序的詳細資訊，請參閱[CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate)。

##  <a name="setcommandfordblclk"></a>  CMouseManager::SetCommandForDblClk

關聯已先向滑鼠管理員的檢視中的自訂命令。

```
void SetCommandForDblClk(
    int iViewId,
    UINT uiCmd);
```

### <a name="parameters"></a>參數

*iViewId*<br/>
[in]檢視識別項。

*uiCmd*<br/>
[in]命令識別項。

### <a name="remarks"></a>備註

若要將自訂命令產生關聯的檢視，您必須先註冊檢視使用[CMouseManager::AddView](#addview)。 `AddView`方法需要檢視識別碼做為輸入參數。 一旦您註冊的檢視時，您可以呼叫`CMouseManager::SetCommandForDblClk`具有相同檢視識別碼輸入參數提供給`AddView`。 之後，當使用者按兩下滑鼠在已註冊的檢視時，應用程式將執行命令以*uiCmd。* 若要支援自訂的滑鼠行為，您也需要自訂向滑鼠管理員的檢視。 如需有關自訂的滑鼠行為的詳細資訊，請參閱[鍵盤和滑鼠自訂](../keyboard-and-mouse-customization.md)。

如果*uiCmd*設為 0，指定的檢視已不再與命令相關聯。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)<br/>
[鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)

