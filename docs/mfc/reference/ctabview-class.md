---
title: CTabView 類別
ms.date: 11/04/2016
f1_keywords:
- CTabView
- AFXTABVIEW/CTabView
- AFXTABVIEW/CTabView::AddView
- AFXTABVIEW/CTabView::FindTab
- AFXTABVIEW/CTabView::GetActiveView
- AFXTABVIEW/CTabView::GetTabControl
- AFXTABVIEW/CTabView::RemoveView
- AFXTABVIEW/CTabView::SetActiveView
- AFXTABVIEW/CTabView::IsScrollBar
- AFXTABVIEW/CTabView::OnActivateView
helpviewer_keywords:
- CTabView [MFC], AddView
- CTabView [MFC], FindTab
- CTabView [MFC], GetActiveView
- CTabView [MFC], GetTabControl
- CTabView [MFC], RemoveView
- CTabView [MFC], SetActiveView
- CTabView [MFC], IsScrollBar
- CTabView [MFC], OnActivateView
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
ms.openlocfilehash: ad30cbbf5de195708d2d357a76c38b661d095c2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365927"
---
# <a name="ctabview-class"></a>CTabView 類別

該`CTabView`類簡化了在使用 MFC 的文檔/視圖體系結構的應用程式中使用選項卡控制類 ( [CMFCTabCtrl](../../mfc/reference/ctabview-class.md))。

## <a name="syntax"></a>語法

```
class CTabbedView : public CView
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTabView::添加檢視](#addview)|向選項卡控制件添加新檢視。|
|[CTabView::尋找選項卡](#findtab)|在選項卡控制項中返回指定檢視的索引。|
|[CTabView:取得活動檢視](#getactiveview)|傳回目前活動檢視的指標|
|[CTabView:取得Tab控制](#gettabcontrol)|返回對與檢視關聯的選項卡控制件的引用。|
|[CTabView:刪除檢視](#removeview)|從選項卡控制項中刪除檢視。|
|[CTabView:設定活動檢視](#setactiveview)|使視圖處於活動狀態。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CTabView::IsScrollBar](#isscrollbar)|創建選項卡檢視時由框架呼叫,以確定選項卡檢視是否具有共用的水準滾動條。|
|[CTabView:開啟啟動檢視](#onactivateview)|當選項卡檢視變為活動或非活動時,由框架調用。|

## <a name="remarks"></a>備註

此類可以輕鬆地將選項卡式視圖放入文檔/視圖應用程式中。 `CTabView`是包含`CView`嵌`CMFCTabCtrl`入 物件的派生類。 `CTabView`處理支援`CMFCTabCtrl`該物件所需的所有消息。 只需從`CTabView`派生類並將其插入應用程式,然後使用`CView``AddView`方法添加派生類。 選項卡控制項將這些檢視顯示為選項卡。

例如,您可能有一個文檔可以以不同的方式表示:作為電子錶格、圖表、可編輯窗體等。 您可以根據需要創建繪製數據的單個檢視,將它們插入到`CTabView`派生物件中,並在不進行任何其他編碼的情況下對其進行選項卡化。

[選項卡式檢視範例:MFC 選項卡式視圖應用程式](../../overview/visual-cpp-samples.md)`CTabView`演示了 的用法。

## <a name="example"></a>範例

下面的範例顯示了在`CTabView`TabbedView示例中的使用方式。

[!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]

## <a name="requirements"></a>需求

**標題:** afxTabView.h

## <a name="ctabviewaddview"></a><a name="addview"></a>CTabView::添加檢視

向選項卡控制件添加檢視。

```
int AddView(
    CRuntimeClass* pViewClass,
    const CString& strViewLabel,
    int iIndex=-1,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>參數

*pView 類別*<br/>
[在]指向插入檢視的運行時類的指標。

*strViewLabel*<br/>
[在]指定選項卡的文本。

*iIndex*<br/>
[在]指定要插入檢視的零基位置。 如果位置為 -1,則新選項卡將插入到末尾。

*pContext*<br/>
[在]指向視圖`CCreateContext`的指標。

### <a name="return-value"></a>傳回值

如果此方法成功,則為視圖索引。 否則為 -1。

### <a name="remarks"></a>備註

調用此函數以向嵌入在幀中的選項卡控制件添加檢視。

## <a name="ctabviewfindtab"></a><a name="findtab"></a>CTabView::尋找選項卡

在選項卡控制項中返回指定檢視的索引。

```
int FindTab(HWND hWndView) const;
```

### <a name="parameters"></a>參數

*hWndView*<br/>
[在]視圖的句柄。

### <a name="return-value"></a>傳回值

如果找到視圖,則為視圖的索引;否則,-1。

### <a name="remarks"></a>備註

調用此函數以檢索具有指定句柄的檢視的索引。

## <a name="ctabviewgetactiveview"></a><a name="getactiveview"></a>CTabView:取得活動檢視

返回指向當前活動視圖的指標。

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>傳回值

指向活動檢視的有效指標,如果沒有活動檢視,則指向 NULL。

### <a name="remarks"></a>備註

## <a name="ctabviewgettabcontrol"></a><a name="gettabcontrol"></a>CTabView:取得Tab控制

返回對與檢視關聯的選項卡控制件的引用。

```
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```

### <a name="return-value"></a>傳回值

對與檢視關聯的選項卡控制件的引用。

## <a name="ctabviewisscrollbar"></a><a name="isscrollbar"></a>CTabView::IsScrollBar

創建選項卡檢視時由框架呼叫,以確定選項卡檢視是否具有共用的水準滾動條。

```
virtual BOOL IsScrollBar() const;
```

### <a name="return-value"></a>傳回值

如果選項卡檢視應與共用滾動條一起創建,則為 TRUE。 否則，FALSE。

### <a name="remarks"></a>備註

創建*CTabView*物件時,框架呼叫此方法。

覆蓋*CTabView*派生類中的*IsScrollBar*方法,如果要創建具有共用水平滾動條的檢視,則返回 TRUE。

## <a name="ctabviewonactivateview"></a><a name="onactivateview"></a>CTabView:開啟啟動檢視

當選項卡檢視變為活動或非活動時,由框架調用。

```
virtual void OnActivateView(CView* view);
```

### <a name="parameters"></a>參數

*檢視*<br/>
[在]指向視圖的指標。

### <a name="remarks"></a>備註

預設實作不做任何動作。 重寫`CTabView`派生類中的此方法以處理此通知。

## <a name="ctabviewremoveview"></a><a name="removeview"></a>CTabView:刪除檢視

從選項卡控制項中刪除檢視。

```
BOOL RemoveView(int iTabNum);
```

### <a name="parameters"></a>參數

*伊塔布納姆*<br/>
[在]要刪除的檢視的索引。

### <a name="return-value"></a>傳回值

如果此方法成功,則刪除檢視的索引。 否則 -1。

### <a name="remarks"></a>備註

## <a name="ctabviewsetactiveview"></a><a name="setactiveview"></a>CTabView:設定活動檢視

使視圖處於活動狀態。

```
BOOL SetActiveView(int iTabNum);
```

### <a name="parameters"></a>參數

*伊塔布納姆*<br/>
[在]選項卡視圖的零基索引。

### <a name="return-value"></a>傳回值

如果指定的檢視處於活動狀態,則為 TRUE;如果視圖的索引無效,則 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[CMFCTabCtrl::設定活動選項卡](../../mfc/reference/cmfctabctrl-class.md#setactivetab)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTabCtrl](../../mfc/reference/ctabview-class.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)
