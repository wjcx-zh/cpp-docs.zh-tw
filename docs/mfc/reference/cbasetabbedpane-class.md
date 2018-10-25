---
title: CBaseTabbedPane 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: addbc7c81c8cd38f44b7b1004c0b4e23ca183ecb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067316"
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
|[Cbasetabbedpane:: Addtab](#addtab)|將新的索引標籤加入至索引標籤式窗格中。|
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|指定空的索引標籤式的窗格是否可以終結。|
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|適用於定位點設定，會從登錄中，載入至索引標籤式窗格。|
|[CBaseTabbedPane::CanFloat](#canfloat)|判斷是否可以浮動窗格。 (覆寫[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。)|
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|決定索引標籤式窗格的標題是否應該為作用中的索引標籤會顯示相同的文字。|
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(覆寫[CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument)。)|
|[Cbasetabbedpane:: Detachpane](#detachpane)|MDI 索引標籤式文件會將一或多個可停駐窗格。|
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|啟用或停用索引標籤式窗格的重新同步處理與作用中的索引標籤上的標籤文字的標題文字。|
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|將內部的定位順序還原成預設狀態。|
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|傳回位於索引標籤時 [] 索引標籤是索引所識別之以零起始的索引標籤, 的窗格。|
|||
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|傳回窗格識別碼所識別的窗格|
|[Cbasetabbedpane:: Floattab](#floattab)|讓窗格浮動，但僅限於窗格目前位於可卸離的索引標籤時。|
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|傳回在窗格中的索引標籤的預設順序。|
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|擷取第一個顯示索引標籤的指標。|
|[CBaseTabbedPane::GetMinSize](#getminsize)|擷取最小允許大小的窗格。 (覆寫[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。)|
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|傳回窗格圖示的控制代碼。 (覆寫[CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon)。)|
|[CBaseTabbedPane::GetPaneList](#getpanelist)|傳回一份包含窗格的索引標籤式窗格。|
|[CBaseTabbedPane::GetTabArea](#gettabarea)|傳回的頂端和底部的索引標籤區域的週框矩形。|
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|傳回索引標籤 視窗中的索引標籤的計數。|
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|取得基礎 （包裝） 索引標籤視窗。|
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|傳回顯示索引標籤的計數。|
|[Cbasetabbedpane:: Hasautohidemode](#hasautohidemode)|決定索引標籤式的窗格是否可以切換為自動隱藏模式。|
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|決定索引標籤式的窗格是否會隱藏如果只有一個索引標籤會顯示。|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|在序列化期間，在內部使用。|
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|重新計算窗格的配置資訊。 (覆寫[cpane:: Recalclayout](../../mfc/reference/cpane-class.md#recalclayout)。)|
|[CBaseTabbedPane::RemovePane](#removepane)|從索引標籤式窗格中移除窗格。|
|`CBaseTabbedPane::SaveSiblingBarIDs`|在序列化期間，在內部使用。|
|`CBaseTabbedPane::Serialize`|(覆寫[cdockablepane:: Serialize](cdockablepane-class.md)。)|
|`CBaseTabbedPane::SerializeTabWindow`|在序列化期間，在內部使用。|
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|判斷是否會自動終結索引標籤式的控制列。|
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|切換停駐窗格之間顯示並自動隱藏模式。 (覆寫[CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode)。)|
|[CBaseTabbedPane::ShowTab](#showtab)|顯示或隱藏 索引標籤。|

## <a name="remarks"></a>備註

這個類別是抽象類別，而且無法具現化。 它會實作服務通用於所有類型的索引標籤式窗格。

目前，此程式庫包含兩個衍生的索引標籤式的窗格的類別： [CTabbedPane 類別](../../mfc/reference/ctabbedpane-class.md)並[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。

A`CBaseTabbedPane`物件會包裝的指標[CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)物件。 [CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)就會變成索引標籤式窗格的子視窗。

如需如何建立索引標籤式的窗格的詳細資訊，請參閱[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)， [CTabbedPane 類別](../../mfc/reference/ctabbedpane-class.md)，並[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>需求

**標頭：** afxBaseTabbedPane.h

##  <a name="addtab"></a>  Cbasetabbedpane:: Addtab

將新的索引標籤加入至索引標籤式窗格中。

```
virtual BOOL AddTab(
    CWnd* pNewBar,
    BOOL bVisible = TRUE,
    BOOL bSetActive = TRUE,
    BOOL bDetachable = TRUE);
```

### <a name="parameters"></a>參數

*pNewBar*<br/>
[in、 out]將窗格指標。 之後呼叫這個方法，這個指標可能會變成無效。 如需詳細資訊，請參閱＜備註＞一節。

*bVisible*<br/>
[in]若要顯示 [] 索引標籤;，則為 TRUE否則為 FALSE。

*bSetActive*<br/>
[in]True 表示將索引標籤作用中 索引標籤上;否則為 FALSE。

*bDetachable*<br/>
[in]True 表示將中斷連結; 索引標籤否則為 FALSE。

### <a name="return-value"></a>傳回值

如果已成功加入索引標籤的窗格，且已不會終結程序中，則為 TRUE。 如果要加入的窗格是型別的物件，則為 FALSE `CBaseTabbedPane`。 如需詳細資訊，請參閱＜備註＞一節。

### <a name="remarks"></a>備註

呼叫這個方法，以加入成為新的索引標籤上的索引標籤式窗格的窗格。 如果*pNewBar*指向的物件型別的`CBaseTabbedPane`，其所有的索引標籤會複製到索引標籤式窗格，然後*pNewBar*終結。 因此， *pNewBar*會變成無效的指標，而不應使用。

##  <a name="allowdestroyemptytabbedpane"></a>  CBaseTabbedPane::AllowDestroyEmptyTabbedPane

指定空的索引標籤式的窗格是否可以終結。

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>傳回值

如果空白，則為 TRUE 才能終結索引標籤式的窗格;否則為 FALSE。 預設實作永遠傳回 TRUE。

### <a name="remarks"></a>備註

如果要終結不允許空白的索引標籤式的窗格，架構會改為隱藏窗格。

##  <a name="applyrestoredtabinfo"></a>  CBaseTabbedPane::ApplyRestoredTabInfo

從登錄載入 索引標籤上設定並將其套用至索引標籤式窗格。

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>參數

*bUseTabIndexes*<br/>
[in]由架構在內部使用這個參數。

### <a name="remarks"></a>備註

重新載入登錄中的停駐狀態資訊時，這個方法是由架構呼叫。 方法會取得索引標籤順序和索引標籤式窗格的索引標籤名稱的相關資訊。

##  <a name="canfloat"></a>  CBaseTabbedPane::CanFloat

指定是否可以浮動索引標籤式的窗格。

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>傳回值

如果可以浮動窗格;，則為 TRUE。否則為 FALSE。

##  <a name="cansetcaptiontexttotabname"></a>  CBaseTabbedPane::CanSetCaptionTextToTabName

決定索引標籤式窗格的標題是否應該為作用中的索引標籤會顯示相同的文字。

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>傳回值

如果索引標籤式窗格的標題文字設定為使用中索引標籤; 文字，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

方法用來判斷顯示的文字是否在索引標籤式的窗格標題重複的項目上的作用中的索引標籤。您可以啟用或停用此功能藉由呼叫[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)。

##  <a name="converttotabbeddocument"></a>  CBaseTabbedPane::ConvertToTabbedDocument

MDI 索引標籤式文件會將一或多個可停駐窗格。

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>參數

*bActiveTabOnly*<br/>
[in]當您將轉換的索引標籤式的窗格時，指定 TRUE 會轉換是使用索引標籤。指定為 FALSE，則轉換在窗格中的所有索引標籤。

##  <a name="detachpane"></a>  Cbasetabbedpane:: Detachpane

中斷連結從索引標籤式窗格的窗格。

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>參數

*pBar*<br/>
[in]若要卸離 窗格的指標。

*bHide*<br/>
[in]布林值參數，指定卸離後，framework 是否隱藏窗格。

### <a name="return-value"></a>傳回值

如果架構已成功中斷連結 窗格中，則為 TRUEFalse *pBar*為 NULL 或參考到不在索引標籤式窗格的窗格。

### <a name="remarks"></a>備註

架構會盡可能浮動卸離的窗格。 如需詳細資訊，請參閱 < [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。

##  <a name="enablesetcaptiontexttotabname"></a>  CBaseTabbedPane::EnableSetCaptionTextToTabName

啟用或停用索引標籤式窗格的重新同步處理與作用中的索引標籤上的標籤文字的標題文字。

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
[in]與作用中 索引標籤標題; 同步處理的索引標籤式的窗格的標題，則為 TRUE否則為 FALSE。

##  <a name="filldefaulttabsorderarray"></a>  CBaseTabbedPane::FillDefaultTabsOrderArray

將內部的定位順序還原成預設狀態。

```
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>備註

當架構還原 Outlook 功能區設為初始狀態時，會呼叫這個方法。

##  <a name="findpanebyid"></a>  CBaseTabbedPane::FindPaneByID

傳回窗格識別碼所識別的窗格

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>參數

*uBarID*<br/>
[in]指定要尋找窗格的識別碼。

### <a name="return-value"></a>傳回值

窗格中，如果找不到它; 指標否則為 NULL。

### <a name="remarks"></a>備註

這個方法會比較在窗格中的所有索引標籤，並傳回具有所指定的識別碼*uBarID*參數。

##  <a name="findbarbytabnumber"></a>  CBaseTabbedPane::FindBarByTabNumber

傳回位於索引標籤的窗格。

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>參數

*nTabNum*<br/>
[in]指定要擷取之索引標籤的以零為起始索引。

*bGetWrappedBar*<br/>
[in]傳回基礎的 （包裝） 視窗的窗格中，而不是本身; 窗格，則為 TRUE否則為 FALSE。 這只適用於衍生自窗格[CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)。

### <a name="return-value"></a>傳回值

如果找到 [] 窗格中，則會傳回 [搜尋] 窗格的有效指標;否則為 NULL。

### <a name="remarks"></a>備註

呼叫這個方法來擷取位於指定索引標籤的窗格*nTabNum*參數。

##  <a name="floattab"></a>  Cbasetabbedpane:: Floattab

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
[in、 out]Float 窗格指標。

*nTabID*<br/>
[in]指定 float 索引標籤的以零為起始的索引。

*dockMethod*<br/>
[in]指定要用來讓窗格浮動方法。 如需詳細資訊，請參閱＜備註＞一節。

*bHide*<br/>
[in]若要隱藏窗格浮動; 之前，則為 TRUE否則為 FALSE。

### <a name="return-value"></a>傳回值

如果窗格浮動;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

呼叫這個方法，以將目前位於可卸離的索引標籤的窗格。

如果您想要以程式設計的方式卸離 窗格中，指定如 DM_SHOW *dockMethod*參數。 如果您想要浮動窗格中，它浮動先前的相同位置，指定為 DM_DBL_CLICK *dockMethod*參數。

##  <a name="getdefaulttabsorder"></a>  CBaseTabbedPane::GetDefaultTabsOrder

傳回在窗格中的索引標籤的預設順序。

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>傳回值

A`CArray`物件，指定在窗格中的索引標籤的預設順序。

### <a name="remarks"></a>備註

Outlook 功能區會重設為初始狀態時，架構會呼叫這個方法。

##  <a name="getfirstvisibletab"></a>  CBaseTabbedPane::GetFirstVisibleTab

擷取第一個顯示索引標籤的指標。

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>參數

*iTabNum*<br/>
[in]整數的參考。 這個方法會寫入第一個顯示索引標籤的以零起始的索引這個參數，則為-1 如果未顯示索引標籤上找到。

### <a name="return-value"></a>傳回值

如果成功，第一個顯示索引標籤; 的指標否則為 NULL。

##  <a name="getminsize"></a>  CBaseTabbedPane::GetMinSize

擷取最小允許大小的窗格。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>參數

*size*<br/>
[out]A`CSize`填滿允許大小的最小的物件。

### <a name="remarks"></a>備註

如果作用中的最小的窗格大小一致的處理 ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize))，*大小*填滿作用中的索引標籤的允許大小的最小值。否則，請*大小*的傳回值會填入[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。

##  <a name="getpaneicon"></a>  CBaseTabbedPane::GetPaneIcon

擷取最小允許大小的窗格。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>參數

*size*<br/>
[out]A`CSize`填滿允許大小的最小的物件。

### <a name="remarks"></a>備註

如果作用中的最小的窗格大小一致的處理 ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize))，*大小*填滿作用中的索引標籤的允許大小的最小值。否則，請*大小*的傳回值會填入[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。

##  <a name="getpanelist"></a>  CBaseTabbedPane::GetPaneList

傳回一份包含窗格的索引標籤式窗格。

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>參數

*lst*<br/>
[out]A`CObList`填入索引標籤式窗格中所包含的窗格。

*pRTCFilter*<br/>
[in]如果不是 NULL，則傳回的清單會包含屬於指定的執行階段類別的窗格。

##  <a name="gettabarea"></a>  CBaseTabbedPane::GetTabArea

傳回的頂端和底部的索引標籤區域的週框矩形。

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>參數

*rectTabAreaTop*<br/>
[out]接收上方的索引標籤區域的螢幕座標。

*rectTabAreaBottom*<br/>
[out]會接收較低的索引標籤區域的螢幕座標。

### <a name="remarks"></a>備註

呼叫這個方法來判斷螢幕座標，上限和下限 索引標籤區域中的週框矩形。

##  <a name="gettabsnum"></a>  CBaseTabbedPane::GetTabsNum

傳回索引標籤 視窗中的索引標籤的計數。

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>傳回值

在索引標籤式窗格中的索引標籤數目。

##  <a name="getunderlyingwindow"></a>  CBaseTabbedPane::GetUnderlyingWindow

取得基礎 （包裝） 索引標籤視窗。

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>傳回值

基礎的索引標籤視窗的指標。

##  <a name="getvisibletabsnum"></a>  CBaseTabbedPane::GetVisibleTabsNum

傳回可見索引標籤的計數。

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>傳回值

可見的索引標籤，將會大於或等於零的數字。

### <a name="remarks"></a>備註

呼叫這個方法，以判斷可見索引標籤的索引標籤式窗格數目。

##  <a name="hasautohidemode"></a>  Cbasetabbedpane:: Hasautohidemode

決定索引標籤式窗格是否可切換為自動隱藏模式。

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>傳回值

如果窗格可以切換為 自動隱藏模式，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

如果停用自動隱藏模式時，沒有 pin 碼 按鈕會顯示索引標籤式的窗格的標題。

##  <a name="ishidesingletab"></a>  CBaseTabbedPane::IsHideSingleTab

決定索引標籤式的窗格是否會隱藏如果只有一個索引標籤會顯示。

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>傳回值

如果只有一個可見的索引標籤; 時未顯示索引標籤 視窗，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

如果窗格不會顯示，因為只有一個索引標籤會開啟，您可以呼叫這個方法來判斷索引標籤式的窗格是否正常運作。

##  <a name="removepane"></a>  CBaseTabbedPane::RemovePane

從索引標籤式窗格中移除窗格。

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>參數

*pBar*<br/>
[in、 out]若要從索引標籤式窗格移除窗格指標。

### <a name="return-value"></a>傳回值

如果成功移除窗格從索引標籤式窗格和索引標籤式的窗格是否仍然有效，則為 TRUE。 如果已移除最後一個窗格從索引標籤式窗格，而且即將終結索引標籤式的窗格，則為 FALSE。 如果傳回的值為 FALSE，請勿使用索引標籤式的窗格了。

### <a name="remarks"></a>備註

呼叫這個方法來移除 [] 窗格中所指定*pBar*從索引標籤式窗格的參數。

##  <a name="setautodestroy"></a>  CBaseTabbedPane::SetAutoDestroy

判斷是否會自動終結索引標籤式的控制列。

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*bAutoDestroy*<br/>
[in]如果以動態方式建立索引標籤式的窗格，而且您不想要控制其存留期;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

設定自動-終結模式，則為 TRUE，如果您以動態方式建立索引標籤式的窗格，而且您不想要控制其存留期。 如果自動終結模式為 TRUE，將會自動終結索引標籤式的窗格，由架構。

##  <a name="showtab"></a>  CBaseTabbedPane::ShowTab

顯示或隱藏 索引標籤。

```
virtual BOOL ShowTab(
    CWnd* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>參數

*pBar*<br/>
[in]若要顯示或隱藏窗格指標。

*bShow*<br/>
[in]True 表示要顯示的窗格中;如果為 false，則隱藏窗格。

*bDelay*<br/>
[in]TRUE 表示延遲的調整 索引標籤的版面配置。否則為 FALSE。

*bActivate*<br/>
[in]True 表示將索引標籤作用中 索引標籤上;否則為 FALSE。

### <a name="return-value"></a>傳回值

如果 [] 索引標籤已顯示或隱藏成功，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

當您呼叫這個方法時，窗格顯示或隱藏的值而定*bShow*參數。 如果您隱藏索引標籤，而且是最後一個可見的索引標籤，在 [基礎] 視窗，則會隱藏索引標籤式的窗格。 如果有先前沒有索引標籤顯示時，您就會顯示索引標籤，會顯示索引標籤式的窗格。

##  <a name="recalclayout"></a>  CBaseTabbedPane::RecalcLayout

重新計算窗格的配置資訊。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>備註

如果窗格浮動窗格，則這個方法會通知架構，來調整窗格的迷你框架的目前大小的大小。

如果窗格即停駐，這個方法沒有任何作用。

##  <a name="setautohidemode"></a>  CBaseTabbedPane::SetAutoHideMode

中斷連結的索引標籤式窗格的窗格的設定自動隱藏模式。

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>參數

*bMode*<br/>
[in]TRUE 表示啟用自動隱藏模式;若要啟用一般停駐的模式，則為 FALSE。

*dwAlignment*<br/>
[in]指定要建立的 [自動隱藏] 窗格的對齊方式。 如需可能值的清單，請參閱 < [CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment)。

*pCurrAutoHideBar*<br/>
[in、 out]在目前的自動隱藏工具列的指標。 可以是 NULL。

*bUseTimer*<br/>
[in]指定要使用的自動隱藏 」 效果，當使用者切換窗格為 自動隱藏模式，還是要立即隱藏窗格。

### <a name="return-value"></a>傳回值

自動隱藏工具列切換為自動隱藏模式中，則為 NULL，如果沒有工具列建立時建立指標。

### <a name="remarks"></a>備註

當使用者選擇 [釘選] 按鈕，自動隱藏模式或一般停駐模式切換索引標籤式的窗格，架構會呼叫這個方法。

每個中斷連結的窗格，在索引標籤式窗格中設定自動隱藏模式。 不可中斷連結的窗格，會被忽略。 如需詳細資訊，請參閱 < [:: Enabletabdetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach)。

呼叫這個方法來以程式設計方式切換到 自動隱藏模式的索引標籤式的窗格。 必須停駐窗格中，於主框架視窗 ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider)必須傳回的有效指標[CPaneDivider](../../mfc/reference/cpanedivider-class.md))。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)
