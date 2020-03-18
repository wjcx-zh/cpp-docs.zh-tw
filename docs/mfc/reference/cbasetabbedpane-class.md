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
ms.openlocfilehash: d7ffaa7274a8ed12944cdbc5dcbbdcb8fd3fd2b9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418864"
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
|[CBaseTabbedPane：： AddTab](#addtab)|將新的索引標籤加入至索引標籤式窗格。|
|[CBaseTabbedPane：： AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|指定是否可以終結空的索引標籤式窗格。|
|[CBaseTabbedPane：： ApplyRestoredTabInfo](#applyrestoredtabinfo)|將 [索引標籤] 設定（從登錄載入）套用至索引標籤式窗格。|
|[CBaseTabbedPane：： CanFloat](#canfloat)|決定窗格是否可以浮動。 （覆寫[CBasePane：： CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。）|
|[CBaseTabbedPane：： CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|決定索引標籤式窗格的標題是否應顯示與 [使用中] 索引標籤相同的文字。|
|[CBaseTabbedPane：： ConvertToTabbedDocument](#converttotabbeddocument)|（覆寫[CDockablePane：： ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument)。）|
|[CBaseTabbedPane：:D etachPane](#detachpane)|將一個或多個可停駐窗格轉換成 MDI 索引標籤式檔。|
|[CBaseTabbedPane：： EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|啟用或停用索引標籤式窗格的功能，以在使用中索引標籤上將標題文字與標籤文字同步處理。|
|[CBaseTabbedPane：： FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|將 [內部] 索引標籤順序還原為預設狀態。|
|[CBaseTabbedPane：： FindBarByTabNumber](#findbarbytabnumber)|當索引標籤以零為基底的索引標籤時，傳回位在索引標籤中的窗格。|
|||
|[CBaseTabbedPane：： FindPaneByID](#findpanebyid)|傳回窗格識別碼所識別的窗格。|
|[CBaseTabbedPane：： FloatTab](#floattab)|讓窗格浮動，但僅限於窗格目前位於可卸離的索引標籤時。|
|[CBaseTabbedPane：： GetDefaultTabsOrder](#getdefaulttabsorder)|傳回窗格中索引標籤的預設順序。|
|[CBaseTabbedPane：： GetFirstVisibleTab](#getfirstvisibletab)|抓取第一個顯示之索引標籤的指標。|
|[CBaseTabbedPane：： GetMinSize](#getminsize)|抓取窗格所允許的最小大小。 （覆寫[CPane：： GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。）|
|[CBaseTabbedPane：： GetPaneIcon](#getpaneicon)|傳回窗格圖示的控制碼。 （覆寫[CBasePane：： GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon)。）|
|[CBaseTabbedPane：： GetPaneList](#getpanelist)|傳回包含在索引標籤式窗格中的窗格清單。|
|[CBaseTabbedPane：： GetTabArea](#gettabarea)|傳回上和下索引標籤區域的周框。|
|[CBaseTabbedPane：： GetTabsNum](#gettabsnum)|傳回索引標籤視窗中的索引標籤計數。|
|[CBaseTabbedPane：： GetUnderlyingWindow](#getunderlyingwindow)|取得基礎（已包裝的）索引標籤視窗。|
|[CBaseTabbedPane：： GetVisibleTabsNum](#getvisibletabsnum)|傳回顯示的索引標籤計數。|
|[CBaseTabbedPane：： HasAutoHideMode](#hasautohidemode)|決定索引標籤式窗格是否可以切換為自動隱藏模式。|
|[CBaseTabbedPane：： IsHideSingleTab](#ishidesingletab)|決定如果只顯示一個索引標籤，是否隱藏索引標籤式窗格。|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|在序列化期間于內部使用。|
|[CBaseTabbedPane：： RecalcLayout](#recalclayout)|重新計算窗格的版面配置資訊。 （覆寫[CPane：： RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout)。）|
|[CBaseTabbedPane：： RemovePane](#removepane)|從索引標籤式窗格中移除窗格。|
|`CBaseTabbedPane::SaveSiblingBarIDs`|在序列化期間于內部使用。|
|`CBaseTabbedPane::Serialize`|（覆寫[CDockablePane：：序列化](cdockablepane-class.md)。）|
|`CBaseTabbedPane::SerializeTabWindow`|在序列化期間于內部使用。|
|[CBaseTabbedPane：： SetAutoDestroy](#setautodestroy)|決定是否會自動終結索引標籤式控制列。|
|[CBaseTabbedPane：： SetAutoHideMode](#setautohidemode)|在顯示和自動隱藏模式之間切換停駐窗格。 （覆寫[CDockablePane：： SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode)。）|
|[CBaseTabbedPane：： Showtab](#showtab)|顯示或隱藏索引標籤。|

## <a name="remarks"></a>備註

這個類別是抽象類別，無法具現化。 它會實作為各種索引標籤式窗格的泛型服務。

目前，此程式庫包含兩個衍生的索引標籤式窗格類別： [CTabbedPane 類別](../../mfc/reference/ctabbedpane-class.md)和[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。

`CBaseTabbedPane` 物件會包裝[CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)物件的指標。 [CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)接著會成為索引標籤式窗格的子視窗。

如需如何建立索引標籤式窗格的詳細資訊，請參閱[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)、 [CTabbedPane 類別](../../mfc/reference/ctabbedpane-class.md)和[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>需求

**標頭：** afxBaseTabbedPane。h

##  <a name="addtab"></a>CBaseTabbedPane：： AddTab

將新的索引標籤加入至索引標籤式窗格。

```
virtual BOOL AddTab(
    CWnd* pNewBar,
    BOOL bVisible = TRUE,
    BOOL bSetActive = TRUE,
    BOOL bDetachable = TRUE);
```

### <a name="parameters"></a>參數

*pNewBar*<br/>
[in、out]要加入之窗格的指標。 呼叫這個方法之後，這個指標可能會變成無效。 如需詳細資訊，請參閱＜備註＞一節。

*bVisible*<br/>
在TRUE 表示讓索引標籤可見;否則為 FALSE。

*bSetActive*<br/>
在TRUE 表示讓索引標籤變成使用中索引標籤;否則為 FALSE。

*bDetachable*<br/>
在TRUE 表示讓索引標籤可分離;否則為 FALSE。

### <a name="return-value"></a>傳回值

如果窗格已成功新增為索引標籤，且未在進程中終結，則為 TRUE。 如果要加入的窗格是 `CBaseTabbedPane`類型的物件，則為 FALSE。 如需詳細資訊，請參閱＜備註＞一節。

### <a name="remarks"></a>備註

呼叫這個方法，將窗格加入至索引標籤式窗格上的新索引標籤。 如果*pNewBar*指向 `CBaseTabbedPane`類型的物件，其所有索引標籤都會複製到索引標籤式窗格上，然後*pNewBar*會終結。 因此， *pNewBar*會變成不正確指標，因此不應使用。

##  <a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane：： AllowDestroyEmptyTabbedPane

指定是否可以終結空的索引標籤式窗格。

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>傳回值

如果可以終結空的索引標籤式窗格，則為 TRUE;否則為 FALSE。 預設的執行一律會傳回 TRUE。

### <a name="remarks"></a>備註

如果不允許終結空的索引標籤式窗格，則架構會改為隱藏該窗格。

##  <a name="applyrestoredtabinfo"></a>CBaseTabbedPane：： ApplyRestoredTabInfo

從登錄載入索引標籤設定，並將其套用至索引標籤式窗格。

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>參數

*bUseTabIndexes*<br/>
在這個參數是由架構在內部使用。

### <a name="remarks"></a>備註

當此方法從登錄重載停駐狀態資訊時，會由架構呼叫。 方法會取得索引標籤式窗格的定位順序和索引標籤名稱的相關資訊。

##  <a name="canfloat"></a>CBaseTabbedPane：： CanFloat

指定索引標籤式窗格是否可以浮動。

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>傳回值

如果窗格可以浮動，則為 TRUE;否則為 FALSE。

##  <a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane：： CanSetCaptionTextToTabName

決定索引標籤式窗格的標題是否應顯示與 [使用中] 索引標籤相同的文字。

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>傳回值

如果索引標籤式窗格的標題文字設定為使用中索引標籤的文字，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

方法是用來判斷在索引標籤式窗格標題上顯示的文字是否會複製作用中索引標籤的標籤。您可以藉由呼叫[CBaseTabbedPane：： EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)來啟用或停用這項功能。

##  <a name="converttotabbeddocument"></a>CBaseTabbedPane：： ConvertToTabbedDocument

將一個或多個可停駐窗格轉換成 MDI 索引標籤式檔。

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>參數

*bActiveTabOnly*<br/>
在當您轉換索引標籤式窗格時，請指定 TRUE 以僅轉換作用中的索引標籤。指定 FALSE 可轉換窗格中的所有索引標籤。

##  <a name="detachpane"></a>CBaseTabbedPane：:D etachPane

從索引標籤式窗格中卸離窗格。

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>參數

*pBar*<br/>
在要卸離之窗格的指標。

*bHide*<br/>
在布林值參數，指定架構在卸離後是否隱藏窗格。

### <a name="return-value"></a>傳回值

如果架構成功卸離窗格，則為 TRUE;如果*pBar*為 Null，或參考不在索引標籤式窗格中的窗格，則為 FALSE。

### <a name="remarks"></a>備註

如果可能的話，架構會將已卸離的窗格浮動。 如需詳細資訊，請參閱[CBasePane：： CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。

##  <a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane：： EnableSetCaptionTextToTabName

啟用或停用索引標籤式窗格的功能，以在使用中索引標籤上將標題文字與標籤文字同步處理。

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
在TRUE 表示使用作用中的索引標籤標題同步處理索引標籤式窗格標題;否則為 FALSE。

##  <a name="filldefaulttabsorderarray"></a>CBaseTabbedPane：： FillDefaultTabsOrderArray

將 [內部] 索引標籤順序還原為預設狀態。

```
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>備註

當架構將 Outlook 橫條還原為初始狀態時，會呼叫這個方法。

##  <a name="findpanebyid"></a>CBaseTabbedPane：： FindPaneByID

傳回窗格識別碼所識別的窗格。

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>參數

*uBarID*<br/>
在指定要尋找之窗格的識別碼。

### <a name="return-value"></a>傳回值

如果找到，則為窗格的指標;否則為 Null。

### <a name="remarks"></a>備註

這個方法會比較窗格中的所有索引標籤，並傳回一個具有*uBarID*參數所指定之識別碼的索引標籤。

##  <a name="findbarbytabnumber"></a>CBaseTabbedPane：： FindBarByTabNumber

傳回位在索引標籤中的窗格。

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>參數

*nTabNum*<br/>
在指定要抓取之索引標籤的以零為基底的索引。

*bGetWrappedBar*<br/>
在TRUE 表示傳回窗格的基礎（已包裝）視窗，而不是窗格本身;否則為 FALSE。 這僅適用于衍生自[CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)的窗格。

### <a name="return-value"></a>傳回值

如果找到窗格，則會傳回所搜尋之窗格的有效指標。否則為 Null。

### <a name="remarks"></a>備註

呼叫這個方法來抓取位於*nTabNum*參數所指定之索引標籤中的窗格。

##  <a name="floattab"></a>CBaseTabbedPane：： FloatTab

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
[in、out]要浮動之窗格的指標。

*nTabID*<br/>
在將索引標籤的以零起始的索引指定為 float。

*dockMethod*<br/>
在指定要用來使窗格浮動的方法。 如需詳細資訊，請參閱＜備註＞一節。

*bHide*<br/>
在TRUE 表示在浮動之前隱藏窗格;否則為 FALSE。

### <a name="return-value"></a>傳回值

如果窗格浮動，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

呼叫這個方法，將目前位於可分離索引標籤中的窗格浮動。

如果您想要以程式設計方式卸離窗格，請指定*dockMethod*參數的 DM_SHOW。 如果您想要將窗格浮動在先前浮動的相同位置，請指定 DM_DBL_CLICK 做為*dockMethod*參數。

##  <a name="getdefaulttabsorder"></a>CBaseTabbedPane：： GetDefaultTabsOrder

傳回窗格中索引標籤的預設順序。

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>傳回值

`CArray` 物件，指定窗格中索引標籤的預設順序。

### <a name="remarks"></a>備註

當 Outlook 橫條重設為初始狀態時，架構會呼叫這個方法。

##  <a name="getfirstvisibletab"></a>CBaseTabbedPane：： GetFirstVisibleTab

抓取第一個顯示之索引標籤的指標。

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>參數

*iTabNum*<br/>
在整數的參考。 這個方法會將第一個顯示的索引標籤之以零為起始的索引寫入這個參數，如果找不到顯示的索引標籤，則為-1。

### <a name="return-value"></a>傳回值

如果成功，則為第一個顯示之索引標籤的指標;否則為 Null。

##  <a name="getminsize"></a>CBaseTabbedPane：： GetMinSize

抓取窗格所允許的最小大小。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>參數

*size*<br/>
脫銷填入允許大小下限的 `CSize` 物件。

### <a name="remarks"></a>備註

如果最小窗格大小的一致處理為使用中（ [CPane：： m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)），則會以作用中索引標籤的最小允許大小填入*大小*。否則，*大小*會填入[CPane：： GetMinSize](../../mfc/reference/cpane-class.md#getminsize)的傳回值。

##  <a name="getpaneicon"></a>CBaseTabbedPane：： GetPaneIcon

抓取窗格所允許的最小大小。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>參數

*size*<br/>
脫銷填入允許大小下限的 `CSize` 物件。

### <a name="remarks"></a>備註

如果最小窗格大小的一致處理為使用中（ [CPane：： m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)），則會以作用中索引標籤的最小允許大小填入*大小*。否則，*大小*會填入[CPane：： GetMinSize](../../mfc/reference/cpane-class.md#getminsize)的傳回值。

##  <a name="getpanelist"></a>CBaseTabbedPane：： GetPaneList

傳回包含在索引標籤式窗格中的窗格清單。

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>參數

*.lst*<br/>
脫銷以索引標籤式窗格中包含的窗格填入的 `CObList`。

*pRTCFilter*<br/>
在如果不是 Null，則傳回的清單只會包含屬於所指定執行時間類別的窗格。

##  <a name="gettabarea"></a>CBaseTabbedPane：： GetTabArea

傳回上和下索引標籤區域的周框。

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>參數

*rectTabAreaTop*<br/>
脫銷接收上方索引標籤區域的螢幕座標。

*rectTabAreaBottom*<br/>
脫銷接收下方索引標籤區域的螢幕座標。

### <a name="remarks"></a>備註

呼叫這個方法，以針對上方和下方的索引標籤區域，判斷周框的邊框（以螢幕座標表示）。

##  <a name="gettabsnum"></a>CBaseTabbedPane：： GetTabsNum

傳回索引標籤視窗中的索引標籤計數。

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>傳回值

索引標籤式窗格中的索引標籤數目。

##  <a name="getunderlyingwindow"></a>CBaseTabbedPane：： GetUnderlyingWindow

取得基礎（已包裝的）索引標籤視窗。

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>傳回值

基礎索引標籤視窗的指標。

##  <a name="getvisibletabsnum"></a>CBaseTabbedPane：： GetVisibleTabsNum

傳回可見索引標籤的計數。

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>傳回值

可見索引標籤的數目，會大於或等於零。

### <a name="remarks"></a>備註

呼叫這個方法，以判斷索引標籤式窗格中可見的索引標籤數目。

##  <a name="hasautohidemode"></a>CBaseTabbedPane：： HasAutoHideMode

決定索引標籤式窗格是否可切換為自動隱藏模式。

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>傳回值

如果窗格可以切換為自動隱藏模式，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果停用自動隱藏模式，則索引標籤式窗格標題上不會顯示 [釘選] 按鈕。

##  <a name="ishidesingletab"></a>CBaseTabbedPane：： IsHideSingleTab

決定如果只顯示一個索引標籤，是否隱藏索引標籤式窗格。

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>傳回值

如果只有一個可見索引標籤，則不會顯示索引標籤視窗，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果窗格未顯示，因為只有一個索引標籤已開啟，您可以呼叫這個方法來判斷索引標籤式窗格是否正常運作。

##  <a name="removepane"></a>CBaseTabbedPane：： RemovePane

從索引標籤式窗格中移除窗格。

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>參數

*pBar*<br/>
[in、out]要從索引標籤式窗格中移除之窗格的指標。

### <a name="return-value"></a>傳回值

如果已從索引標籤式窗格中成功移除窗格，而且索引標籤式窗格仍然有效，則為 TRUE。 如果已從索引標籤式窗格中移除最後一個窗格，而且索引標籤式窗格即將終結，則為 FALSE。 如果傳回值為 FALSE，請不要再使用索引標籤式窗格。

### <a name="remarks"></a>備註

呼叫這個方法，從索引標籤式窗格中移除*pBar*參數所指定的窗格。

##  <a name="setautodestroy"></a>CBaseTabbedPane：： SetAutoDestroy

決定是否會自動終結索引標籤式控制列。

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*bAutoDestroy*<br/>
在如果已動態建立索引標籤式窗格，而且您不控制其存留期，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果您以動態方式建立索引標籤式窗格，且未控制其存留期，請將自動終結模式設定為 [TRUE]。 如果自動銷毀模式為 TRUE，則架構會自動終結索引標籤式窗格。

##  <a name="showtab"></a>CBaseTabbedPane：： Showtab

顯示或隱藏索引標籤。

```
virtual BOOL ShowTab(
    CWnd* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>參數

*pBar*<br/>
在要顯示或隱藏之窗格的指標。

*bShow*<br/>
在TRUE 表示顯示窗格;FALSE 表示隱藏窗格。

*bDelay*<br/>
在TRUE 表示延遲調整索引標籤版面配置;否則為 FALSE。

*bActivate*<br/>
在TRUE 表示讓索引標籤變成使用中索引標籤;否則為 FALSE。

### <a name="return-value"></a>傳回值

如果已成功顯示或隱藏索引標籤，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

當您呼叫這個方法時，窗格會顯示或隱藏，視*bShow*參數的值而定。 如果您隱藏索引標籤，而它是基礎索引標籤視窗中的最後一個可見索引標籤，則會隱藏索引標籤式窗格。 如果您在先前沒有顯示索引標籤的情況下顯示索引標籤，則會顯示索引標籤式窗格。

##  <a name="recalclayout"></a>CBaseTabbedPane：： RecalcLayout

重新計算窗格的版面配置資訊。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>備註

如果窗格是浮動的，此方法會通知架構將窗格的大小調整為迷你框架的目前大小。

如果窗格停駐，這個方法不會執行任何操作。

##  <a name="setautohidemode"></a>CBaseTabbedPane：： SetAutoHideMode

設定索引標籤式窗格中可分離窗格的自動隱藏模式。

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>參數

*bMode*<br/>
在TRUE 表示啟用自動隱藏模式;FALSE 表示啟用一般銜接模式。

*dwAlignment*<br/>
在指定要建立之自動隱藏窗格的對齊方式。 如需可能值的清單，請參閱[CPane：： MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment)。

*pCurrAutoHideBar*<br/>
[in、out]目前自動隱藏工具列的指標。 可以是 NULL。

*bUseTimer*<br/>
在指定當使用者將窗格切換為自動隱藏模式，或立即隱藏窗格時，是否要使用自動隱藏效果。

### <a name="return-value"></a>傳回值

當切換為自動隱藏模式時所建立之自動隱藏工具列的指標，如果未建立任何工具列，則為 Null。

### <a name="remarks"></a>備註

當使用者選擇 [釘選] 按鈕，將索引標籤式窗格切換為自動隱藏模式或一般銜接模式時，架構會呼叫這個方法。

自動隱藏模式會針對索引標籤式窗格中的每個可分離窗格進行設定。 無法分離的窗格會被忽略。 如需詳細資訊，請參閱[CMFCBaseTabCtrl：： EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach)。

呼叫這個方法，以程式設計方式將索引標籤式窗格切換為自動隱藏模式。 窗格必須停駐于主框架視窗（ [CDockablePane：： GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider)必須傳回[CPaneDivider](../../mfc/reference/cpanedivider-class.md)的有效指標）。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)
