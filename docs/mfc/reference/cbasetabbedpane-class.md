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
ms.openlocfilehash: 21f2821392d2b9e71837997f5a9a10ab80ba073f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838668"
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
|[CBaseTabbedPane：： AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|指定是否可終結空白的索引標籤式窗格。|
|[CBaseTabbedPane：： ApplyRestoredTabInfo](#applyrestoredtabinfo)|將從登錄載入的索引標籤設定套用至索引標籤式窗格。|
|[CBaseTabbedPane：： CanFloat](#canfloat)|判斷窗格是否可以浮動。  (覆寫 [CBasePane：： CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。 ) |
|[CBaseTabbedPane：： CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|決定索引標籤式窗格的標題是否應該顯示為使用中索引標籤的相同文字。|
|[CBaseTabbedPane：： ConvertToTabbedDocument](#converttotabbeddocument)| (覆寫 [CDockablePane：： ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument)。 ) |
|[CBaseTabbedPane：:D etachPane](#detachpane)|將一或多個可停駐窗格轉換成 MDI 索引標籤式檔。|
|[CBaseTabbedPane：： EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|啟用或停用索引標籤式窗格在使用中索引標籤上，將標題文字與標籤文字同步處理的能力。|
|[CBaseTabbedPane：： FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|將 [內部] 索引標籤順序還原為預設狀態。|
|[CBaseTabbedPane：： FindBarByTabNumber](#findbarbytabnumber)|當索引標籤以零為基礎的索引標籤索引來識別時，傳回位於索引標籤中的窗格。|
|[CBaseTabbedPane：： FindPaneByID](#findpanebyid)|傳回窗格識別碼所識別的窗格。|
|[CBaseTabbedPane：： FloatTab](#floattab)|讓窗格浮動，但僅限於窗格目前位於可卸離的索引標籤時。|
|[CBaseTabbedPane：： GetDefaultTabsOrder](#getdefaulttabsorder)|傳回窗格中的預設索引標籤順序。|
|[CBaseTabbedPane：： GetFirstVisibleTab](#getfirstvisibletab)|抓取第一個所顯示索引標籤的指標。|
|[CBaseTabbedPane：： GetMinSize](#getminsize)|抓取窗格允許的最小大小。  (覆寫 [CPane：： GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。 ) |
|[CBaseTabbedPane：： GetPaneIcon](#getpaneicon)|傳回窗格圖示的控制碼。  (覆寫 [CBasePane：： GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon)。 ) |
|[CBaseTabbedPane：： GetPaneList](#getpanelist)|傳回包含在索引標籤式窗格中的窗格清單。|
|[CBaseTabbedPane：： GetTabArea](#gettabarea)|傳回頂端和底部索引標籤區域的周框矩形。|
|[CBaseTabbedPane：： GetTabsNum](#gettabsnum)|傳回索引標籤視窗中的索引標籤計數。|
|[CBaseTabbedPane：： GetUnderlyingWindow](#getunderlyingwindow)|取得已包裝) 索引標籤視窗的基礎 (。|
|[CBaseTabbedPane：： GetVisibleTabsNum](#getvisibletabsnum)|傳回所顯示索引標籤的計數。|
|[CBaseTabbedPane：： HasAutoHideMode](#hasautohidemode)|決定索引標籤式窗格是否可以切換為自動隱藏模式。|
|[CBaseTabbedPane：： IsHideSingleTab](#ishidesingletab)|決定如果只顯示一個索引標籤，是否隱藏索引標籤式窗格。|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|在序列化期間于內部使用。|
|[CBaseTabbedPane：： RecalcLayout](#recalclayout)|重新計算窗格的版面配置資訊。  (覆寫 [CPane：： RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout)。 ) |
|[CBaseTabbedPane：： RemovePane](#removepane)|從索引標籤式窗格中移除窗格。|
|`CBaseTabbedPane::SaveSiblingBarIDs`|在序列化期間于內部使用。|
|`CBaseTabbedPane::Serialize`| (覆寫 [CDockablePane：：序列化](cdockablepane-class.md)。 ) |
|`CBaseTabbedPane::SerializeTabWindow`|在序列化期間于內部使用。|
|[CBaseTabbedPane：： SetAutoDestroy](#setautodestroy)|決定是否會自動終結索引標籤式控制列。|
|[CBaseTabbedPane：： SetAutoHideMode](#setautohidemode)|切換顯示和自動隱藏模式之間的停駐窗格。  (覆寫 [CDockablePane：： SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode)。 ) |
|[CBaseTabbedPane：： Showtab]](#showtab)|顯示或隱藏索引標籤。|

## <a name="remarks"></a>備註

這個類別是抽象類別，無法具現化。 它會執行各種索引標籤式窗格通用的服務。

目前，程式庫包含兩個衍生的索引標籤式窗格類別： [CTabbedPane 類別](../../mfc/reference/ctabbedpane-class.md) 和 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。

`CBaseTabbedPane`物件會包裝指向[CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)物件的指標。 [CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md) 接著會成為索引標籤式窗格的子視窗。

如需如何建立索引標籤式窗格的詳細資訊，請參閱 [CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)、 [CTabbedPane 類別](../../mfc/reference/ctabbedpane-class.md)和 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>規格需求

**標頭：** afxBaseTabbedPane。h

## <a name="cbasetabbedpaneaddtab"></a><a name="addtab"></a> CBaseTabbedPane：： AddTab

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
[in，out]要加入之窗格的指標。 呼叫這個方法之後，這個指標可能會變成無效。 如需詳細資訊，請參閱＜備註＞一節。

*bVisible*<br/>
在TRUE 表示讓索引標籤可見;否則為 FALSE。

*bSetActive*<br/>
在TRUE 表示讓索引標籤成為使用中的索引標籤;否則為 FALSE。

*bDetachable*<br/>
在TRUE 表示讓索引標籤可分離;否則為 FALSE。

### <a name="return-value"></a>傳回值

如果窗格已成功加入為索引標籤，且未在進程中終結，則為 TRUE。 如果要加入的窗格是類型的物件，則為 FALSE `CBaseTabbedPane` 。 如需詳細資訊，請參閱＜備註＞一節。

### <a name="remarks"></a>備註

呼叫這個方法，將窗格加入至索引標籤式窗格上的新索引標籤。 如果 *pNewBar* 指向型別的物件，則它的所有索引標籤 `CBaseTabbedPane` 都會複製到索引標籤式窗格，然後 *pNewBar* 就會損毀。 因此， *pNewBar* 會變成不正確指標，且不應該使用。

## <a name="cbasetabbedpaneallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a> CBaseTabbedPane：： AllowDestroyEmptyTabbedPane

指定是否可終結空白的索引標籤式窗格。

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>傳回值

如果可以終結空白的索引標籤式窗格，則為 TRUE;否則為 FALSE。 預設的實值一律會傳回 TRUE。

### <a name="remarks"></a>備註

如果不允許終結空白的索引標籤式窗格，則架構會改為隱藏窗格。

## <a name="cbasetabbedpaneapplyrestoredtabinfo"></a><a name="applyrestoredtabinfo"></a> CBaseTabbedPane：： ApplyRestoredTabInfo

從登錄載入索引標籤設定，並將其套用至索引標籤式窗格。

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>參數

*bUseTabIndexes*<br/>
在此參數會由架構在內部使用。

### <a name="remarks"></a>備註

當架構從登錄重載停駐狀態資訊時，會呼叫這個方法。 方法會取得索引標籤式窗格的索引標籤順序和索引標籤名稱的相關資訊。

## <a name="cbasetabbedpanecanfloat"></a><a name="canfloat"></a> CBaseTabbedPane：： CanFloat

指定索引標籤式窗格是否可以浮動。

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>傳回值

如果窗格可以浮點數，則為 TRUE;否則為 FALSE。

## <a name="cbasetabbedpanecansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a> CBaseTabbedPane：： CanSetCaptionTextToTabName

決定索引標籤式窗格的標題是否應該顯示為使用中索引標籤的相同文字。

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>傳回值

如果索引標籤式窗格的標題文字設定為 [使用中] 索引標籤的文字，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

方法是用來判斷顯示在索引標籤式窗格標題上的文字是否重複使用中索引標籤的標籤。您可以藉由呼叫 [CBaseTabbedPane：： EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)來啟用或停用這項功能。

## <a name="cbasetabbedpaneconverttotabbeddocument"></a><a name="converttotabbeddocument"></a> CBaseTabbedPane：： ConvertToTabbedDocument

將一或多個可停駐窗格轉換成 MDI 索引標籤式檔。

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>參數

*bActiveTabOnly*<br/>
在當您轉換索引標籤式窗格時，請指定 [TRUE] 只轉換使用中的索引標籤。指定 FALSE 可轉換窗格中的所有索引標籤。

## <a name="cbasetabbedpanedetachpane"></a><a name="detachpane"></a> CBaseTabbedPane：:D etachPane

從索引標籤式窗格卸離窗格。

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>參數

*pBar*<br/>
在要卸離之窗格的指標。

*bHide*<br/>
在布林值參數，指定架構是否會在卸離之後隱藏窗格。

### <a name="return-value"></a>傳回值

如果架構成功卸離窗格，則為 TRUE;如果 *pBar* 是 Null 或參考不在索引標籤式窗格中的窗格，則為 FALSE。

### <a name="remarks"></a>備註

架構會盡可能浮動卸離的窗格。 如需詳細資訊，請參閱 [CBasePane：： CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。

## <a name="cbasetabbedpaneenablesetcaptiontexttotabname"></a><a name="enablesetcaptiontexttotabname"></a> CBaseTabbedPane：： EnableSetCaptionTextToTabName

啟用或停用索引標籤式窗格在使用中索引標籤上，將標題文字與標籤文字同步處理的能力。

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
在TRUE 表示與使用中的索引標籤標題同步處理索引標籤式窗格標題;否則為 FALSE。

## <a name="cbasetabbedpanefilldefaulttabsorderarray"></a><a name="filldefaulttabsorderarray"></a> CBaseTabbedPane：： FillDefaultTabsOrderArray

將 [內部] 索引標籤順序還原為預設狀態。

```cpp
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>備註

當 framework 將 Outlook bar 還原為初始狀態時，就會呼叫這個方法。

## <a name="cbasetabbedpanefindpanebyid"></a><a name="findpanebyid"></a> CBaseTabbedPane：： FindPaneByID

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

這個方法會比較窗格中的所有索引標籤，並傳回具有 *uBarID* 參數所指定之識別碼的索引標籤。

## <a name="cbasetabbedpanefindbarbytabnumber"></a><a name="findbarbytabnumber"></a> CBaseTabbedPane：： FindBarByTabNumber

傳回位於索引標籤中的窗格。

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>參數

*nTabNum*<br/>
在指定要抓取之索引標籤的以零為起始的索引。

*bGetWrappedBar*<br/>
在TRUE 表示傳回窗格的基礎 (包裝) 視窗，而非窗格本身;否則為 FALSE。 這僅適用于衍生自 [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)的窗格。

### <a name="return-value"></a>傳回值

如果找到該窗格，則會傳回所搜尋之窗格的有效指標;否則為 Null。

### <a name="remarks"></a>備註

呼叫這個方法，以取得位於 *nTabNum* 參數所指定之索引標籤中的窗格。

## <a name="cbasetabbedpanefloattab"></a><a name="floattab"></a> CBaseTabbedPane：： FloatTab

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
[in，out]要浮動之窗格的指標。

*nTabID*<br/>
在指定要浮點數之索引標籤的以零為基底的索引。

*dockMethod*<br/>
在指定要用來讓窗格浮動的方法。 如需詳細資訊，請參閱＜備註＞一節。

*bHide*<br/>
在TRUE 表示在浮動之前隱藏窗格;否則為 FALSE。

### <a name="return-value"></a>傳回值

如果窗格浮動，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

呼叫這個方法，將目前位於可卸離索引標籤中的窗格浮動。

如果您想要以程式設計方式卸離窗格，請指定 *dockMethod* 參數的 DM_SHOW。 如果您想要將窗格浮在它之前浮動的相同位置，請將 DM_DBL_CLICK 指定為 *dockMethod* 參數。

## <a name="cbasetabbedpanegetdefaulttabsorder"></a><a name="getdefaulttabsorder"></a> CBaseTabbedPane：： GetDefaultTabsOrder

傳回窗格中的預設索引標籤順序。

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>傳回值

`CArray`物件，指定窗格中的預設索引標籤順序。

### <a name="remarks"></a>備註

當 Outlook bar 重設為初始狀態時，架構會呼叫這個方法。

## <a name="cbasetabbedpanegetfirstvisibletab"></a><a name="getfirstvisibletab"></a> CBaseTabbedPane：： GetFirstVisibleTab

抓取第一個所顯示索引標籤的指標。

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>參數

*iTabNum*<br/>
在整數的參考。 這個方法會將第一個顯示的索引標籤之以零為起始的索引寫入此參數，如果找不到顯示的索引標籤，則為-1。

### <a name="return-value"></a>傳回值

如果成功，則為第一個顯示索引標籤的指標;否則為 Null。

## <a name="cbasetabbedpanegetminsize"></a><a name="getminsize"></a> CBaseTabbedPane：： GetMinSize

抓取窗格允許的最小大小。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>參數

*size*<br/>
擴展以 `CSize` 允許的最小大小填滿的物件。

### <a name="remarks"></a>備註

如果最小窗格大小的一致性處理是作用中的 ( [CPane：： m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)) ，則 *大小* 會填滿 [使用中] 索引標籤的 [允許的最小大小]。否則， *大小* 會填入 [CPane：： GetMinSize](../../mfc/reference/cpane-class.md#getminsize)的傳回值。

## <a name="cbasetabbedpanegetpaneicon"></a><a name="getpaneicon"></a> CBaseTabbedPane：： GetPaneIcon

抓取窗格允許的最小大小。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>參數

*size*<br/>
擴展以 `CSize` 允許的最小大小填滿的物件。

### <a name="remarks"></a>備註

如果最小窗格大小的一致性處理是作用中的 ( [CPane：： m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)) ，則 *大小* 會填滿 [使用中] 索引標籤的 [允許的最小大小]。否則， *大小* 會填入 [CPane：： GetMinSize](../../mfc/reference/cpane-class.md#getminsize)的傳回值。

## <a name="cbasetabbedpanegetpanelist"></a><a name="getpanelist"></a> CBaseTabbedPane：： GetPaneList

傳回包含在索引標籤式窗格中的窗格清單。

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>參數

*Lst*<br/>
擴展填入索引標籤 `CObList` 式窗格中所含窗格的。

*pRTCFilter*<br/>
在如果不是 Null，則傳回的清單只會包含所指定執行時間類別的窗格。

## <a name="cbasetabbedpanegettabarea"></a><a name="gettabarea"></a> CBaseTabbedPane：： GetTabArea

傳回頂端和底部索引標籤區域的周框矩形。

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>參數

*rectTabAreaTop*<br/>
擴展接收上索引標籤區域的螢幕座標。

*rectTabAreaBottom*<br/>
擴展接收下方索引標籤區域的螢幕座標。

### <a name="remarks"></a>備註

呼叫這個方法，以針對上方和下方的索引標籤區域，判斷周框矩形（以螢幕座標為單位）。

## <a name="cbasetabbedpanegettabsnum"></a><a name="gettabsnum"></a> CBaseTabbedPane：： GetTabsNum

傳回索引標籤視窗中的索引標籤計數。

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>傳回值

索引標籤式窗格中的索引標籤數目。

## <a name="cbasetabbedpanegetunderlyingwindow"></a><a name="getunderlyingwindow"></a> CBaseTabbedPane：： GetUnderlyingWindow

取得已包裝) 索引標籤視窗的基礎 (。

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>傳回值

基礎索引標籤視窗的指標。

## <a name="cbasetabbedpanegetvisibletabsnum"></a><a name="getvisibletabsnum"></a> CBaseTabbedPane：： GetVisibleTabsNum

傳回可見索引標籤的計數。

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>傳回值

可見索引標籤的數目，將會大於或等於零。

### <a name="remarks"></a>備註

呼叫這個方法，以決定索引標籤式窗格中可見索引標籤的數目。

## <a name="cbasetabbedpanehasautohidemode"></a><a name="hasautohidemode"></a> CBaseTabbedPane：： HasAutoHideMode

決定索引標籤式窗格是否可切換為自動隱藏模式。

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>傳回值

如果窗格可以切換為自動隱藏模式，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果停用自動隱藏模式，索引標籤式窗格標題上就不會顯示 [釘選] 按鈕。

## <a name="cbasetabbedpaneishidesingletab"></a><a name="ishidesingletab"></a> CBaseTabbedPane：： IsHideSingleTab

決定如果只顯示一個索引標籤，是否隱藏索引標籤式窗格。

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>傳回值

如果只有一個可見索引標籤，就不會顯示索引標籤視窗，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

如果因為只開啟一個索引標籤而未顯示窗格，您可以呼叫這個方法來判斷索引標籤式窗格是否正常運作。

## <a name="cbasetabbedpaneremovepane"></a><a name="removepane"></a> CBaseTabbedPane：： RemovePane

從索引標籤式窗格中移除窗格。

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>參數

*pBar*<br/>
[in，out]要從索引標籤式窗格中移除之窗格的指標。

### <a name="return-value"></a>傳回值

如果已成功從索引標籤式窗格移除窗格，以及索引標籤式窗格仍然有效，則為 TRUE。 如果最後一個窗格已從索引標籤式窗格中移除，且即將終結索引標籤式窗格，則為 FALSE。 如果傳回值為 FALSE，則請勿使用索引標籤式窗格。

### <a name="remarks"></a>備註

呼叫這個方法，從索引標籤式窗格中移除 *pBar* 參數所指定的窗格。

## <a name="cbasetabbedpanesetautodestroy"></a><a name="setautodestroy"></a> CBaseTabbedPane：： SetAutoDestroy

決定是否會自動終結索引標籤式控制列。

```cpp
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*bAutoDestroy*<br/>
在如果已動態建立索引標籤式窗格，而且您沒有控制其存留期，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果您以動態方式建立索引標籤式窗格，以及您未控制其存留期，請將自動損毀模式設定為 [TRUE]。 如果自動損毀模式為 TRUE，架構會自動終結索引標籤式窗格。

## <a name="cbasetabbedpaneshowtab"></a><a name="showtab"></a> CBaseTabbedPane：： Showtab]

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
在TRUE 表示讓索引標籤成為使用中的索引標籤;否則為 FALSE。

### <a name="return-value"></a>傳回值

如果已成功顯示或隱藏索引標籤，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

當您呼叫這個方法時，會根據 *bShow* 參數的值顯示或隱藏窗格。 如果您隱藏索引標籤，而且它是基礎索引標籤視窗中最後一個可見的索引標籤，則會隱藏索引標籤式窗格。 如果您在先前未顯示索引標籤時顯示索引標籤，則會顯示索引標籤式窗格。

## <a name="cbasetabbedpanerecalclayout"></a><a name="recalclayout"></a> CBaseTabbedPane：： RecalcLayout

重新計算窗格的版面配置資訊。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>備註

如果窗格是浮動的，這個方法會通知架構將窗格的大小調整為迷你框架的目前大小。

如果停駐窗格，這個方法不會執行任何動作。

## <a name="cbasetabbedpanesetautohidemode"></a><a name="setautohidemode"></a> CBaseTabbedPane：： SetAutoHideMode

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
在指定要建立之自動隱藏窗格的對齊方式。 如需可能值的清單，請參閱 [CPane：： MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment)。

*pCurrAutoHideBar*<br/>
[in，out]目前自動隱藏工具列的指標。 可以是 NULL。

*bUseTimer*<br/>
在指定當使用者將窗格切換為自動隱藏模式時，是否要使用自動隱藏效果，或立即隱藏窗格。

### <a name="return-value"></a>傳回值

切換至自動隱藏模式時所建立之自動隱藏工具列的指標，如果未建立任何工具列，則為 Null。

### <a name="remarks"></a>備註

當使用者選擇 [釘選] 按鈕，將索引標籤式窗格切換為自動隱藏模式或一般銜接模式時，架構會呼叫這個方法。

您可以在索引標籤式窗格中，針對每個可分離的窗格設定自動隱藏模式。 系統會忽略不可卸離的窗格。 如需詳細資訊，請參閱 [CMFCBaseTabCtrl：： EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach)。

呼叫這個方法，以程式設計方式將索引標籤式窗格切換為自動隱藏模式。 您必須將窗格停駐于主框架視窗 ( [CDockablePane：： GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) 必須傳回 [CPaneDivider](../../mfc/reference/cpanedivider-class.md)) 的有效指標。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)
