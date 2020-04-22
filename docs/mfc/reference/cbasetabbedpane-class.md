---
title: CBaseTabbedPane 類別
ms.date: 11/04/2016
f1_keywords:
- CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::AddTab
- AFXBASETABBEDPANE/CBaseTabbedPane::AllowDestroyEmptyTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::ApplyRestoredTabInfo
- AFXBASETABBEDPANE/CBaseTabbedPane::CanFloat
- AFXBASETABBEDPANE/CBaseTabbedPane::CanSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::ConvertToTabbedDocument
- AFXBASETABBEDPANE/CBaseTabbedPane::DetachPane
- AFXBASETABBEDPANE/CBaseTabbedPane::EnableSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::FillDefaultTabsOrderArray
- AFXBASETABBEDPANE/CBaseTabbedPane::FindBarByTabNumber
- AFXBASETABBEDPANE/CBaseTabbedPane::FindPaneByID
- AFXBASETABBEDPANE/CBaseTabbedPane::FloatTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetDefaultTabsOrder
- AFXBASETABBEDPANE/CBaseTabbedPane::GetFirstVisibleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetMinSize
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneIcon
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneList
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabArea
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::GetUnderlyingWindow
- AFXBASETABBEDPANE/CBaseTabbedPane::GetVisibleTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::HasAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::IsHideSingleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::RecalcLayout
- AFXBASETABBEDPANE/CBaseTabbedPane::RemovePane
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoDestroy
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::ShowTab
helpviewer_keywords:
- CBaseTabbedPane [MFC], AddTab
- CBaseTabbedPane [MFC], AllowDestroyEmptyTabbedPane
- CBaseTabbedPane [MFC], ApplyRestoredTabInfo
- CBaseTabbedPane [MFC], CanFloat
- CBaseTabbedPane [MFC], CanSetCaptionTextToTabName
- CBaseTabbedPane [MFC], ConvertToTabbedDocument
- CBaseTabbedPane [MFC], DetachPane
- CBaseTabbedPane [MFC], EnableSetCaptionTextToTabName
- CBaseTabbedPane [MFC], FillDefaultTabsOrderArray
- CBaseTabbedPane [MFC], FindBarByTabNumber
- CBaseTabbedPane [MFC], FindPaneByID
- CBaseTabbedPane [MFC], FloatTab
- CBaseTabbedPane [MFC], GetDefaultTabsOrder
- CBaseTabbedPane [MFC], GetFirstVisibleTab
- CBaseTabbedPane [MFC], GetMinSize
- CBaseTabbedPane [MFC], GetPaneIcon
- CBaseTabbedPane [MFC], GetPaneList
- CBaseTabbedPane [MFC], GetTabArea
- CBaseTabbedPane [MFC], GetTabsNum
- CBaseTabbedPane [MFC], GetUnderlyingWindow
- CBaseTabbedPane [MFC], GetVisibleTabsNum
- CBaseTabbedPane [MFC], HasAutoHideMode
- CBaseTabbedPane [MFC], IsHideSingleTab
- CBaseTabbedPane [MFC], RecalcLayout
- CBaseTabbedPane [MFC], RemovePane
- CBaseTabbedPane [MFC], SetAutoDestroy
- CBaseTabbedPane [MFC], SetAutoHideMode
- CBaseTabbedPane [MFC], ShowTab
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
ms.openlocfilehash: b3ae0d69c385ba89cf75d682ce12c6f1f4e5112f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752978"
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane 類別

擴充 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) 的功能，以支援建立索引標籤式視窗。

## <a name="syntax"></a>語法

```
class CBaseTabbedPane : public CDockablePane
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CBaseTabbedPane::CBaseTabbedPane`|預設建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CBaseTabbed窗格::新增選項卡](#addtab)|將新選項卡添加到選項卡式窗格中。|
|[CBaseTabbed 窗格::允許銷毀空表板窗格](#allowdestroyemptytabbedpane)|指定是否可以銷毀空選項卡式窗格。|
|[CBaseTabbed窗格::應用已還原的選項卡資訊](#applyrestoredtabinfo)|將從註冊表載入的選項卡設置應用於選項卡式窗格。|
|[CBaseTabbed窗格::可以浮動](#canfloat)|確定窗格是否可以浮動。 (覆蓋[CBasePane::可以浮動](../../mfc/reference/cbasepane-class.md#canfloat). )|
|[CBaseTabbed窗格::可以設定標題文字標籤名稱](#cansetcaptiontexttotabname)|確定選項卡式窗格的標題是否應顯示與活動選項卡相同的文本。|
|[CBaseTabbed窗格::轉換到選項卡文件](#converttotabbeddocument)|( 覆寫[可嵌入字元::轉換為 Tabbed 文件](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument)。)|
|[CBaseTabbedPane::D埃塔奇帕內](#detachpane)|將一個或多個可停靠窗格轉換為 MDI 選項卡式文件。|
|[CBaseTabbed窗格::啟用設定標題文字標籤名稱](#enablesetcaptiontexttotabname)|啟用或禁用選項卡式窗格將標題文本與活動選項卡上的標籤文本同步的能力。|
|[CBaseTabbed窗格::填充預設選項卡順序陣列](#filldefaulttabsorderarray)|將內部選項卡順序還原為默認狀態。|
|[CBaseTabbed窗格::尋找巴比塔號](#findbarbytabnumber)|當選項卡由零基選項卡索引標識時,返回駐留在選項卡中的窗格。|
|||
|[CBaseTabbed窗格::尋找窗格ByID](#findpanebyid)|返回窗格 ID 標識的窗格。|
|[CBaseTabbed窗格::浮動選項卡](#floattab)|讓窗格浮動，但僅限於窗格目前位於可卸離的索引標籤時。|
|[CBaseTabbed窗格::取得預設選項卡訂單](#getdefaulttabsorder)|傳回窗格中的選項卡的預設順序。|
|[CBaseTabbed窗格::取得第一個可見點選項卡](#getfirstvisibletab)|檢索指向第一個顯示的選項卡的指標。|
|[CBaseTabbed窗格::取得最小尺寸](#getminsize)|檢索窗格的最小允許大小。 ( 覆[寫 CPane: 取得最小值](../../mfc/reference/cpane-class.md#getminsize)。|
|[CBaseTabbed窗格::取得窗格圖示](#getpaneicon)|將句柄返回到窗格圖示。 (覆蓋[CBasePane:抓取窗格](../../mfc/reference/cbasepane-class.md#getpaneicon).)|
|[CBaseTabbed窗格::抓取窗格清單](#getpanelist)|傳回選項卡式窗格中包含的窗格的清單。|
|[CBaseTabbed窗格::取得塔布區域](#gettabarea)|返回頂部和底部選項卡區域的邊界矩形。|
|[CBaseTabbed窗格::取得TabsNum](#gettabsnum)|傳回選項卡視窗中的選項卡計數。|
|[CBaseTabbed窗格::取得基礎視窗](#getunderlyingwindow)|獲取基礎(包裝)選項卡視窗。|
|[CBaseTabbed窗格::取得可見的TabsNum](#getvisibletabsnum)|返回顯示的選項卡的計數。|
|[CBaseTabbed窗格::具有自動隱藏模式](#hasautohidemode)|確定是否可以將選項卡式窗格切換到自動隱藏模式。|
|[CBaseTabbed窗格::IsHide單一選項卡](#ishidesingletab)|確定如果只顯示一個選項卡,選項卡窗格是否隱藏。|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|在序列化期間在內部使用。|
|[CBaseTabbed窗格::Recalclayout](#recalclayout)|重新計算窗格的佈局資訊。 (覆蓋[CPane:Recalclayout](../../mfc/reference/cpane-class.md#recalclayout).)|
|[CBaseTabbed 窗格::刪除窗格](#removepane)|從選項卡式窗格中刪除窗格。|
|`CBaseTabbedPane::SaveSiblingBarIDs`|在序列化期間在內部使用。|
|`CBaseTabbedPane::Serialize`|( 覆[寫 可嵌入窗格::序列化](cdockablepane-class.md)。|
|`CBaseTabbedPane::SerializeTabWindow`|在序列化期間在內部使用。|
|[CBaseTabbed窗格::設定自動銷毀](#setautodestroy)|確定 Tabbed 控制欄是否將自動銷毀。|
|[CBaseTabbed窗格::設定自動隱藏模式](#setautohidemode)|在顯示模式和自動隱藏模式之間切換停靠窗格。 ( 覆[寫可嵌入窗格: 設定自動隱藏模式](../../mfc/reference/cdockablepane-class.md#setautohidemode)。|
|[CBaseTabbed窗格::顯示選項卡](#showtab)|顯示或隱藏選項卡。|

## <a name="remarks"></a>備註

此類是抽象類,無法實例化。 它實現各種選項卡式窗格共有的服務。

目前,該庫包括兩個派生的選項卡式窗格類[:CTabbedPane 類別](../../mfc/reference/ctabbedpane-class.md)和[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。

`CBaseTabbedPane`物件將指標繞到[CMFCBaseTabCtrl 類](../../mfc/reference/cmfcbasetabctrl-class.md)物件。 [然後,CMFCBaseTabCtrl 類](../../mfc/reference/cmfcbasetabctrl-class.md)將成為選項卡式窗格的子視窗。

有關如何建立選項卡式窗格的詳細資訊,請參閱[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)[、CTabbedPane 類別](../../mfc/reference/ctabbedpane-class.md)和[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>需求

**標題:** afxBaseTabbedPane.h

## <a name="cbasetabbedpaneaddtab"></a><a name="addtab"></a>CBaseTabbed窗格::新增選項卡

將新選項卡添加到選項卡式窗格中。

```
virtual BOOL AddTab(
    CWnd* pNewBar,
    BOOL bVisible = TRUE,
    BOOL bSetActive = TRUE,
    BOOL bDetachable = TRUE);
```

### <a name="parameters"></a>參數

*pNewBar*<br/>
[進出]指向要添加的窗格的指標。 調用此方法后,此指標可能會無效。 如需詳細資訊，請參閱＜備註＞一節。

*b 可見*<br/>
[在]TRUE 使選項卡可見;否則,FALSE。

*bSetActive*<br/>
[在]TRUE 使選項卡成為活動選項卡;否則,FALSE。

*b 可拆卸*<br/>
[在]TRUE 使選項卡可拆卸;否則,FALSE。

### <a name="return-value"></a>傳回值

如果窗格已成功添加為選項卡,並且在此過程中未銷毀,則為 TRUE。 如果正在添加的窗格是類型`CBaseTabbedPane`的物件,則 FALSE。 如需詳細資訊，請參閱＜備註＞一節。

### <a name="remarks"></a>備註

呼叫此方法將窗格添加為選項卡式窗格上的新選項卡。 如果*pNewBar*`CBaseTabbedPane`指向類型的物件,則其所有選項卡都將複製到選項卡式窗格中,然後*pNewBar*被銷毀。 因此 *,pNewBar*成為無效的指標,不應使用。

## <a name="cbasetabbedpaneallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a>CBaseTabbed 窗格::允許銷毀空表板窗格

指定是否可以銷毀空選項卡式窗格。

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>傳回值

如果可以銷毀空選項卡式窗格,則為 TRUE;否則,FALSE。 預設實現始終返回 TRUE。

### <a name="remarks"></a>備註

如果不允許銷毀空選項卡式窗格,則框架將隱藏該窗格。

## <a name="cbasetabbedpaneapplyrestoredtabinfo"></a><a name="applyrestoredtabinfo"></a>CBaseTabbed窗格::應用已還原的選項卡資訊

從註冊表載入選項卡設置,並將它們應用於選項卡式窗格。

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>參數

*bUseTabIndexs*<br/>
[在]此參數由框架在內部使用。

### <a name="remarks"></a>備註

當框架從註冊表重新載入停靠狀態資訊時,會調用此方法。 該方法獲取有關選項卡式窗格的選項卡順序和選項卡名稱的資訊。

## <a name="cbasetabbedpanecanfloat"></a><a name="canfloat"></a>CBaseTabbed窗格::可以浮動

指定選項卡式窗格是否可以浮動。

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>傳回值

如果窗格可以浮動,則為 TRUE;否則,FALSE。

## <a name="cbasetabbedpanecansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a>CBaseTabbed窗格::可以設定標題文字標籤名稱

確定選項卡式窗格的標題是否應顯示與活動選項卡相同的文本。

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>傳回值

如果選項卡式窗格的標題文本設定為活動選項卡的文本,則為 TRUE;如果選項卡式窗格的標題文本設置為活動選項卡的文本,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

該方法用於確定選項卡式窗格標題中顯示的文本是否複製活動選項卡的標籤。您可以通過調用[CBaseTabbedPane::啟用設定標題文本標籤名稱](#enablesetcaptiontexttotabname)來啟用或禁用此功能。

## <a name="cbasetabbedpaneconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CBaseTabbed窗格::轉換到選項卡文件

將一個或多個可停靠窗格轉換為 MDI 選項卡式文件。

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>參數

*b 作用分頁*<br/>
[在]轉換選項卡式窗格時,指定 TRUE 以僅轉換活動選項卡。 指定 FALSE 以轉換窗格中的所有選項卡。

## <a name="cbasetabbedpanedetachpane"></a><a name="detachpane"></a>CBaseTabbedPane::D埃塔奇帕內

從選項卡式窗格分離窗格。

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>參數

*pBar*<br/>
[在]指向要分離的窗格。

*bHide*<br/>
[在]布爾參數,用於指定框架在分離后是否隱藏窗格。

### <a name="return-value"></a>傳回值

如果框架成功分離窗格,則為 TRUE;如果框架成功分離窗格,則為 TRUE。如果*pBar*為 NULL 或引用不在選項卡式窗格中的窗格,則 FALSE。

### <a name="remarks"></a>備註

如果可能,框架將浮動分離的窗格。 有關詳細資訊,請參閱[CBasePane::可以浮動](../../mfc/reference/cbasepane-class.md#canfloat)。

## <a name="cbasetabbedpaneenablesetcaptiontexttotabname"></a><a name="enablesetcaptiontexttotabname"></a>CBaseTabbed窗格::啟用設定標題文字標籤名稱

啟用或禁用選項卡式窗格將標題文本與活動選項卡上的標籤文本同步的能力。

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]TRUE 將選項卡式窗格標題與活動選項卡標題同步;否則,FALSE。

## <a name="cbasetabbedpanefilldefaulttabsorderarray"></a><a name="filldefaulttabsorderarray"></a>CBaseTabbed窗格::填充預設選項卡順序陣列

將內部選項卡順序還原為默認狀態。

```cpp
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>備註

當框架將 Outlook 欄還原到初始狀態時,將調用此方法。

## <a name="cbasetabbedpanefindpanebyid"></a><a name="findpanebyid"></a>CBaseTabbed窗格::尋找窗格ByID

返回窗格 ID 標識的窗格。

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>參數

*烏巴里德*<br/>
[在]指定要尋找的窗格的識別碼。

### <a name="return-value"></a>傳回值

找到窗格的指標;如果找到該窗格,則指向該窗格的指標。否則,NULL。

### <a name="remarks"></a>備註

此方法比較窗格中的所有選項卡,並返回具有*uBarID*參數指定的ID的選項卡。

## <a name="cbasetabbedpanefindbarbytabnumber"></a><a name="findbarbytabnumber"></a>CBaseTabbed窗格::尋找巴比塔號

返回駐留在選項卡中的窗格。

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>參數

*NTabNum*<br/>
[在]指定要檢索的選項卡的零基索引。

*bGet 包裝條*<br/>
[在]TRUE 返回窗格的基礎(包裝)視窗,而不是窗格本身;否則 FALSE。 這僅適用於從[CdockAblePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)派生的窗格。

### <a name="return-value"></a>傳回值

如果找到窗格,則返回指向要搜索的窗格的有效指標;如果找到窗格,則會返回該指標。否則,NULL。

### <a name="remarks"></a>備註

呼叫此方法以檢索駐留在*nTabNum*參數指定的選項卡中的窗格。

## <a name="cbasetabbedpanefloattab"></a><a name="floattab"></a>CBaseTabbed窗格::浮動選項卡

讓窗格浮動，但僅限於窗格目前位於可卸離的索引標籤時。

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>參數

*pBar*<br/>
[進出]指向窗格的指標以浮動。

*nTabID*<br/>
[在]指定要浮動的選項卡的零基索引。

*基方法*<br/>
[在]指定用於使窗格浮動的方法。 如需詳細資訊，請參閱＜備註＞一節。

*bHide*<br/>
[在]TRUE 以在浮動前隱藏窗格;否則,FALSE。

### <a name="return-value"></a>傳回值

如果窗格浮動,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

調用此方法以浮動當前駐留在可拆卸選項卡中的窗格。

如果要以程式設計方式分離窗格,請為*dockMethod*參數指定DM_SHOW。 如果要將窗格浮動到以前浮動的相同位置,請指定DM_DBL_CLICK作為*dockMethod*參數。

## <a name="cbasetabbedpanegetdefaulttabsorder"></a><a name="getdefaulttabsorder"></a>CBaseTabbed窗格::取得預設選項卡訂單

傳回窗格中的選項卡的預設順序。

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>傳回值

指定`CArray`窗格中選項卡的預設順序的物件。

### <a name="remarks"></a>備註

當 Outlook 欄重置為初始狀態時,框架調用此方法。

## <a name="cbasetabbedpanegetfirstvisibletab"></a><a name="getfirstvisibletab"></a>CBaseTabbed窗格::取得第一個可見點選項卡

檢索指向第一個顯示的選項卡的指標。

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>參數

*伊塔布納姆*<br/>
[在]對整數的引用。 此方法將第一個顯示選項卡的零基索引寫入此參數,如果沒有找到顯示的選項卡,則為 -1。

### <a name="return-value"></a>傳回值

如果成功,則指向第一個顯示選項卡的指標;如果成功,則指向第一個顯示的選項卡。否則,NULL。

## <a name="cbasetabbedpanegetminsize"></a><a name="getminsize"></a>CBaseTabbed窗格::取得最小尺寸

檢索窗格的最小允許大小。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>參數

*size*<br/>
[出]以`CSize`最小允許大小填充的物件。

### <a name="remarks"></a>備註

如果最小窗格大小的一致處理處於活動狀態[(CPane::m_bHandleMinSize),](../../mfc/reference/cpane-class.md#m_bhandleminsize)*則大小*將填充活動選項卡的最小允許大小。否則,*大小*將填充[CPane:getMinSize](../../mfc/reference/cpane-class.md#getminsize)的返回值。

## <a name="cbasetabbedpanegetpaneicon"></a><a name="getpaneicon"></a>CBaseTabbed窗格::取得窗格圖示

檢索窗格的最小允許大小。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>參數

*size*<br/>
[出]以`CSize`最小允許大小填充的物件。

### <a name="remarks"></a>備註

如果最小窗格大小的一致處理處於活動狀態[(CPane::m_bHandleMinSize),](../../mfc/reference/cpane-class.md#m_bhandleminsize)*則大小*將填充活動選項卡的最小允許大小。否則,*大小*將填充[CPane:getMinSize](../../mfc/reference/cpane-class.md#getminsize)的返回值。

## <a name="cbasetabbedpanegetpanelist"></a><a name="getpanelist"></a>CBaseTabbed窗格::抓取窗格清單

傳回選項卡式窗格中包含的窗格的清單。

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>參數

*Lst*<br/>
[出]`CObList`填充選項卡式窗格中的窗格。

*pRTC 過濾器*<br/>
[在]如果它不是 NULL,則傳回的清單僅包含指定執行時類的窗格。

## <a name="cbasetabbedpanegettabarea"></a><a name="gettabarea"></a>CBaseTabbed窗格::取得塔布區域

返回頂部和底部選項卡區域的邊界矩形。

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>參數

*rectTabAreaTop*<br/>
[出]接收上部選項卡區域的螢幕座標。

*rectTab 區域底部*<br/>
[出]接收下部選項卡區域的螢幕座標。

### <a name="remarks"></a>備註

調用此方法以確定上部和下部選項卡區域在螢幕座標中的邊界矩形。

## <a name="cbasetabbedpanegettabsnum"></a><a name="gettabsnum"></a>CBaseTabbed窗格::取得TabsNum

傳回選項卡視窗中的選項卡計數。

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>傳回值

選項卡式窗格中的選項卡數。

## <a name="cbasetabbedpanegetunderlyingwindow"></a><a name="getunderlyingwindow"></a>CBaseTabbed窗格::取得基礎視窗

獲取基礎(包裝)選項卡視窗。

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>傳回值

指向基礎選項卡視窗的指標。

## <a name="cbasetabbedpanegetvisibletabsnum"></a><a name="getvisibletabsnum"></a>CBaseTabbed窗格::取得可見的TabsNum

返回可見選項卡的計數。

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>傳回值

可見選項卡的數量,該選項卡大於或等於零。

### <a name="remarks"></a>備註

呼叫此方法以確定選項卡式窗格中的可見選項卡數。

## <a name="cbasetabbedpanehasautohidemode"></a><a name="hasautohidemode"></a>CBaseTabbed窗格::具有自動隱藏模式

決定索引標籤式窗格是否可切換為自動隱藏模式。

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>傳回值

如果窗格可以切換到自動隱藏模式,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

如果關閉自動隱藏模式,則選項卡式窗格標題上不顯示引腳按鈕。

## <a name="cbasetabbedpaneishidesingletab"></a><a name="ishidesingletab"></a>CBaseTabbed窗格::IsHide單一選項卡

確定如果只顯示一個選項卡,選項卡窗格是否隱藏。

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>傳回值

如果選項卡視窗在只有一個可見選項卡時未顯示,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

如果未顯示窗格,因為只有一個選項卡處於打開狀態,則可以調用此方法以確定選項卡式窗格是否正常工作。

## <a name="cbasetabbedpaneremovepane"></a><a name="removepane"></a>CBaseTabbed 窗格::刪除窗格

從選項卡式窗格中刪除窗格。

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>參數

*pBar*<br/>
[進出]指向窗格的指標,用於從選項卡式窗格中刪除。

### <a name="return-value"></a>傳回值

如果窗格已成功從選項卡式窗格中刪除,並且選項卡式窗格仍然有效,則為 TRUE。 如果最後一個窗格已從選項卡式窗格中刪除,並且選項卡式窗格即將銷毀,則 FALSE。 如果返回值為 FALSE,則不要再使用選項卡式窗格。

### <a name="remarks"></a>備註

呼叫此方法從選項卡式窗格中刪除*pBar*參數指定的窗格。

## <a name="cbasetabbedpanesetautodestroy"></a><a name="setautodestroy"></a>CBaseTabbed窗格::設定自動銷毀

確定 Tabbed 控制欄是否將自動銷毀。

```cpp
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*bAuto銷毀*<br/>
[在]如果選項卡式窗格是動態創建的,並且您不控制其存留期,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

如果動態創建選項卡式窗格,並且未控制其存留期,則將自動銷毀模式設置為 TRUE。 如果自動銷毀模式為 TRUE,則框架將自動銷毀選項卡式窗格。

## <a name="cbasetabbedpaneshowtab"></a><a name="showtab"></a>CBaseTabbed窗格::顯示選項卡

顯示或隱藏選項卡。

```
virtual BOOL ShowTab(
    CWnd* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>參數

*pBar*<br/>
[在]指向要顯示或隱藏窗格的指標。

*b 顯示*<br/>
[在]TRUE 以顯示窗格;FALSE 以隱藏窗格。

*bDelay*<br/>
[在]TRUE 以延遲選項卡布局的調整;否則,FALSE。

*b 啟動*<br/>
[在]TRUE 使選項卡成為活動選項卡;否則,FALSE。

### <a name="return-value"></a>傳回值

如果選項卡已顯示或已成功隱藏,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

呼叫此方法時,會顯示或隱藏窗格,具體取決於*bShow*參數的值。 如果隱藏選項卡,並且它是基礎選項卡視窗中的最後一個可見選項卡,則選項卡式窗格將隱藏。 如果在以前沒有可見的選項卡時顯示選項卡,將顯示選項卡式窗格。

## <a name="cbasetabbedpanerecalclayout"></a><a name="recalclayout"></a>CBaseTabbed窗格::Recalclayout

重新計算窗格的佈局資訊。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>備註

如果窗格是浮動的,此方法會通知框架將窗格的大小調整到小型框架的當前大小。

如果窗格已停靠,則此方法不執行任何操作。

## <a name="cbasetabbedpanesetautohidemode"></a><a name="setautohidemode"></a>CBaseTabbed窗格::設定自動隱藏模式

設定選項卡式窗格中可拆卸窗格的自動隱藏模式。

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>參數

*bMode*<br/>
[在]TRUE 以啟用自動隱藏模式;FALSE 以啟用常規停靠模式。

*dwalignment*<br/>
[在]指定要建立的自動隱藏窗格的對齊方式。 有關可能值的清單,請參閱[CPane::移動。](../../mfc/reference/cpane-class.md#movebyalignment)

*pCurrAutoHidebar*<br/>
[進出]指向目前自動隱藏工具列的指標。 可以是 NULL。

*bUseTimer*<br/>
[在]指定使用者將窗格切換到自動隱藏模式時是否使用自動隱藏效果,還是立即隱藏窗格。

### <a name="return-value"></a>傳回值

切換到自動隱藏模式時建立的指向自動隱藏工具列的指標;如果未建立工具列,則指向 NULL。

### <a name="remarks"></a>備註

當使用者選擇按鍵按鈕將選項卡式窗格切換到自動隱藏模式或常規停靠模式時,框架將調用此方法。

為選項卡式窗格中的每個可拆卸窗格設置自動隱藏模式。 不可拆卸的窗格將被忽略。 有關詳細資訊,請參閱[CMFCBaseTabCtrl::啟用Tabdetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach)。

呼叫此方法以程式設計方式將選項卡式窗格切換到自動隱藏模式。 窗格必須停靠到主框架視窗[(CDockable Pane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider)必須返回指向[CPaneDivider](../../mfc/reference/cpanedivider-class.md)的有效指標)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)
