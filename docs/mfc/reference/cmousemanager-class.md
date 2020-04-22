---
title: 滑鼠管理員類別
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
ms.openlocfilehash: 1394a1b47a86022e37b11e032b87ee2a2a369862
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752803"
---
# <a name="cmousemanager-class"></a>滑鼠管理員類別

允許使用者在用戶雙擊該檢視中時將不同的命令與特定的[CView](../../mfc/reference/cview-class.md)物件相關聯。

## <a name="syntax"></a>語法

```
class CMouseManager : public CObject
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[滑鼠管理員::新增檢視](#addview)|將`CView`物件添加到 **「自定義」** 對話框中。 「**自訂」** 對話方塊使用戶能夠將按兩下與每個列出的檢視的命令相關聯。|
|[滑鼠管理員::取得查看點擊指令](#getviewdblclickcommand)|返回使用者在提供的檢視中按兩下時執行的命令。|
|[滑鼠管理員::取得檢視圖示](#getviewiconid)|返回與提供的檢視 ID 關聯的圖示。|
|[滑鼠管理員:取得檢視 IdBY 名稱](#getviewidbyname)|返回與提供的檢視名稱關聯的檢視 ID。|
|[滑鼠管理員::取得檢視名稱](#getviewnames)|檢索所有添加的檢視名稱的清單。|
|[滑鼠管理員::載入狀態](#loadstate)|從`CMouseManager`Windows 註冊表載入狀態。|
|[滑鼠管理員::儲存狀態](#savestate)|將`CMouseManager`狀態寫入 Windows 註冊表。|
|[滑鼠管理員::SetCommandForBlClk](#setcommandfordblclk)|關聯提供的命令和提供的檢視。|

## <a name="remarks"></a>備註

類`CMouseManager`維護`CView`物件的集合。 每個檢視都由名稱和 ID 標識。 這些檢視顯示在 **「自定義」** 對話框中。 使用者可以通過 **「自定義」** 對話方塊更改與任何檢視關聯的命令。 當用戶雙擊該視圖中時,將執行關聯的命令。 要從編碼角度支援這一點,您必須處理WM_LBUTTONDBLCLK消息,並在該`CView`物件的代碼中調用[CWinAppEx:onViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick)函數。

不應手動創建`CMouseManager`物件。 它將由應用程式的框架創建。 當使用者退出應用程式時,它也會自動銷毀。 要取得指向應用程式的滑鼠管理員的指標,請致電[CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CMouseManager`

## <a name="requirements"></a>需求

**標題:** afxmouse 管理器.h

## <a name="cmousemanageraddview"></a><a name="addview"></a>滑鼠管理員::新增檢視

將[CView](../../mfc/reference/cview-class.md)物件註冊到[CMouseManager 類](../../mfc/reference/cmousemanager-class.md),以支援自訂滑鼠行為。

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
[在]視圖 ID。

*uiViewNameResId*<br/>
[在]引用檢視名稱的資源字串 ID。

*烏伊科尼*<br/>
[在]視圖圖示 ID。

*Iid*<br/>
[在]視圖 ID。

*lpszView名稱*<br/>
[在]視圖名稱。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

為了支援自定義滑鼠行為,必須向`CMouseManager`物件註冊視圖。 從`CView`類派生的任何物件都可以註冊到滑鼠管理器。 與檢視關聯的字串和圖示將顯示在 **「自訂」** 對話框的 **「滑鼠」** 選項卡中。

程式師有責任建立和維護檢視 ID,如*iViewId*和*iId*。

有關如何提供自訂滑鼠行為的詳細資訊,請參閱[鍵盤和滑鼠自定義](../../mfc/keyboard-and-mouse-customization.md)。

### <a name="example"></a>範例

`CMouseManager`下面的範例展示如何使用`CWinAppEx::GetMouseManager``AddView``CMouseManager`類中的方法和 方法檢索指向物件的指標。 此代碼段是[狀態收集示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]

## <a name="cmousemanagergetviewdblclickcommand"></a><a name="getviewdblclickcommand"></a>滑鼠管理員::取得查看點擊指令

返回使用者在提供的檢視中按兩下時執行的命令。

```
UINT GetViewDblClickCommand(int iId) const;
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]視圖 ID。

### <a name="return-value"></a>傳回值

如果視圖與命令關聯,則命令標識符;否則 0。

## <a name="cmousemanagergetviewiconid"></a><a name="getviewiconid"></a>滑鼠管理員::取得檢視圖示

檢索與檢視 ID 關聯的圖示。

```
UINT GetViewIconId(int iViewId) const;
```

### <a name="parameters"></a>參數

*iViewId*<br/>
[在]視圖 ID。

### <a name="return-value"></a>傳回值

圖示資源標識符(如果成功);否則 0。

### <a name="remarks"></a>備註

如果檢視不是首先使用[CMouseManager 註冊,](#addview)則此方法將失敗: :addView 。

## <a name="cmousemanagergetviewidbyname"></a><a name="getviewidbyname"></a>滑鼠管理員:取得檢視 IdBY 名稱

檢索與檢視名稱關聯的檢視 ID。

```
int GetViewIdByName(LPCTSTR lpszName) const;
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
[在]視圖名稱。

### <a name="return-value"></a>傳回值

視圖 ID(如果成功);否則 0。

### <a name="remarks"></a>備註

此方法搜尋使用[CMouseManager 註冊的檢視::addView](#addview)。

## <a name="cmousemanagergetviewnames"></a><a name="getviewnames"></a>滑鼠管理員::取得檢視名稱

檢索所有已註冊視圖名稱的清單。

```cpp
void GetViewNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>參數

*名稱清單*<br/>
[出]對`CStringList`物件的引用。

### <a name="remarks"></a>備註

此方法使用`listOfNames`[CMouseManager:::AddView](#addview)註冊的所有檢視的名稱填充參數。

## <a name="cmousemanagerloadstate"></a><a name="loadstate"></a>滑鼠管理員::載入狀態

從註冊表載入[CMouseManager 類](../../mfc/reference/cmousemanager-class.md)的狀態。

```
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>參數

*lpsz 設定檔名稱*<br/>
[在]註冊表項的路徑。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

從註冊表載入的狀態資訊包括已註冊的檢視、檢視識別碼和關聯的命令。 如果參數*lpszProfileName*為 NULL,則此`CMouseManager`函數將載入[CWinAppEx 類](../../mfc/reference/cwinappex-class.md)控制的預設註冊表位置的數據。

在大多數情況下,您不必直接調用此函數。 它稱為工作區初始化過程的一部分。 有關工作區初始化過程的詳細資訊,請參閱[CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate)。

## <a name="cmousemanagersavestate"></a><a name="savestate"></a>滑鼠管理員::儲存狀態

將[CMouseManager 類](../../mfc/reference/cmousemanager-class.md)的狀態寫入註冊表。

```
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>參數

*lpsz 設定檔名稱*<br/>
[在]註冊表項的路徑。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

寫入註冊表的狀態資訊包括所有已註冊的視圖、視圖標識符和關聯的命令。 如果參數*lpszProfileName*為 NULL,則此`CMouseManager`函數將數據寫入[CWinAppEx 類](../../mfc/reference/cwinappex-class.md)控制的預設註冊表位置。

在大多數情況下,您不必直接調用此函數。 它稱為工作區序列化過程的一部分。 有關工作區序列化過程的詳細資訊,請參閱[CWinAppEx:::保存狀態](../../mfc/reference/cwinappex-class.md#savestate)。

## <a name="cmousemanagersetcommandfordblclk"></a><a name="setcommandfordblclk"></a>滑鼠管理員::SetCommandForBlClk

將自定義命令與首次向滑鼠管理器註冊的檢視關聯。

```cpp
void SetCommandForDblClk(
    int iViewId,
    UINT uiCmd);
```

### <a name="parameters"></a>參數

*iViewId*<br/>
[在]視圖標識碼。

*烏伊Cmd*<br/>
[在]命令識別碼。

### <a name="remarks"></a>備註

為了將自定義命令與檢視關聯,必須首先使用[CMouseManager:::AddView](#addview)註冊檢視。 該方法`AddView`需要視圖標識符作為輸入參數。 註冊檢視後,可以使用提供給的相同檢視`CMouseManager::SetCommandForDblClk`識別碼輸入參數進行呼叫`AddView`。 此後,當用戶雙擊已註冊檢視中的滑鼠時,應用程式將執行*uiCmd*指示的命令。 要支援自定義滑鼠行為,還需要自定義在滑鼠管理器中註冊的視圖。 有關自訂滑鼠行為的詳細資訊,請參閱[鍵盤和滑鼠自訂](../keyboard-and-mouse-customization.md)。

如果*uiCmd*設置為 0,則指定的檢視不再與命令關聯。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)<br/>
[鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)
