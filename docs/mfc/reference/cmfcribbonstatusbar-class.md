---
title: CMFCRibbonStatusBar 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddDynamicElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddSeparator
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::Create
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::CreateEx
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindByID
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExtendedArea
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetSpace
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsBottomFrame
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsInformationMode
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RecalcLayout
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveAll
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::SetInformation
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::OnDrawInformation
helpviewer_keywords:
- CMFCRibbonStatusBar [MFC], AddDynamicElement
- CMFCRibbonStatusBar [MFC], AddElement
- CMFCRibbonStatusBar [MFC], AddExtendedElement
- CMFCRibbonStatusBar [MFC], AddSeparator
- CMFCRibbonStatusBar [MFC], Create
- CMFCRibbonStatusBar [MFC], CreateEx
- CMFCRibbonStatusBar [MFC], FindByID
- CMFCRibbonStatusBar [MFC], FindElement
- CMFCRibbonStatusBar [MFC], GetCount
- CMFCRibbonStatusBar [MFC], GetElement
- CMFCRibbonStatusBar [MFC], GetExCount
- CMFCRibbonStatusBar [MFC], GetExElement
- CMFCRibbonStatusBar [MFC], GetExtendedArea
- CMFCRibbonStatusBar [MFC], GetSpace
- CMFCRibbonStatusBar [MFC], IsBottomFrame
- CMFCRibbonStatusBar [MFC], IsExtendedElement
- CMFCRibbonStatusBar [MFC], IsInformationMode
- CMFCRibbonStatusBar [MFC], RecalcLayout
- CMFCRibbonStatusBar [MFC], RemoveAll
- CMFCRibbonStatusBar [MFC], RemoveElement
- CMFCRibbonStatusBar [MFC], SetInformation
- CMFCRibbonStatusBar [MFC], OnDrawInformation
ms.assetid: 921eb57f-3b40-49fa-a38c-3f2fb6dc2893
ms.openlocfilehash: 8d90e01db022c33edd654e83af05e9986799f2b9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754052"
---
# <a name="cmfcribbonstatusbar-class"></a>CMFCRibbonStatusBar 類別

類`CMFCRibbonStatusBar`實現一個可以顯示功能區元素的狀態欄控件。

## <a name="syntax"></a>語法

```
class CMFCRibbonStatusBar : public CMFCRibbonBar
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC 功能狀態列:新增動態元素](#adddynamicelement)|向功能區狀態列添加動態元素。|
|[CMFC 功能狀態列:新增元素](#addelement)|向功能區狀態列添加新功能區元素。|
|[CMFC 功能狀態列:新增延伸元素](#addextendedelement)|將功能區元素添加到功能區狀態列的擴展區域。|
|[CMFC 狀態列:新增分離器](#addseparator)|向功能區狀態列添加分隔符。|
|[CMFC 功能狀態列:建立](#create)|創建功能區狀態列。|
|[CMFC 功能狀態列:建立Ex](#createex)|創建具有擴展樣式的功能區狀態列。|
|[CMFC 功能狀態列:尋找ByID](#findbyid)||
|[CMFC 功能狀態列:尋找元素](#findelement)|返回指向具有指定命令 ID 的元素的指標。|
|[CMFC 功能狀態列:取得計數](#getcount)|返回位於功能區狀態列主區域的元素數。|
|[CMFC 功能狀態列:取得元素](#getelement)|返回指向位於指定索引的元素的指標。|
|[CMFC 功能狀態列:取得ExCount](#getexcount)|返回位於功能區狀態列擴展區域的元素數。|
|[CMFC 功能狀態列:取得Exelement](#getexelement)|傳回指標，該指標指向功能區狀態列擴充區域中，位於指定索引上的元素。|
|[CMFC 功能狀態列:取得延伸區域](#getextendedarea)||
|[CMFC 功能狀態列:取得空間](#getspace)||
|[CMFC 功能狀態列::是底部框架](#isbottomframe)||
|[CMFC 功能狀態列:延伸元素](#isextendedelement)||
|[CMFC 功能狀態列:資訊模式](#isinformationmode)|確定功能區狀態列是否啟用了資訊模式。|
|[CMFC 功能狀態列:Recalclayout](#recalclayout)|(覆蓋[CMFC 功能列:recalclayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout).)|
|[CMFC 功能狀態列::刪除所有](#removeall)|從功能區狀態列中刪除所有元素。|
|[CMFC 狀態列:刪除元素](#removeelement)|從功能區狀態列中刪除具有指定命令 ID 的元素。|
|[CMFC 功能狀態列:設定資訊](#setinformation)|啟用或禁用功能區狀態欄的資訊模式。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFC 功能狀態列::繪製資訊](#ondrawinformation)|顯示啟用資訊模式時功能區狀態列上顯示的資訊字串。|

## <a name="remarks"></a>備註

用戶可以使用功能區狀態列的內建上下文功能表來更改功能區狀態列上的功能區元素的可見性。 您可以動態新增或刪除元素。

功能區狀態列有兩個區域:主區域和擴展區域。 擴展區域顯示在功能區狀態列的右側,以與主區域不同的顏色顯示。

通常,狀態列的主要區域顯示狀態通知,擴展區域顯示視圖控件。 當使用者調整功能區狀態列的大小時,擴展區域儘可能長時間可見。

## <a name="example"></a>範例

下例示範如何在 `CMFCRibbonStatusBar` 類別中使用各種方法。 該示例展示如何向功能區狀態列添加新功能區元素、向功能區狀態列的擴展區域添加功能區元素、添加分隔符以及啟用功能區狀態列的常規模式。

[!code-cpp[NVC_MFC_RibbonApp#15](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_1.cpp)]
[!code-cpp[NVC_MFC_RibbonApp#16](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)

[CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)

## <a name="requirements"></a>需求

**標題:** afxribbonstatusbar.h

## <a name="cmfcribbonstatusbaradddynamicelement"></a><a name="adddynamicelement"></a>CMFC 功能狀態列:新增動態元素

向功能區狀態列添加動態元素。

```cpp
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```

### <a name="parameters"></a>參數

*p 元素*<br/>
[在]指向動態元素的指標。

### <a name="remarks"></a>備註

與常規元素不同,動態元素不可自定義,狀態列的自定義功能表不顯示它們。

## <a name="cmfcribbonstatusbaraddelement"></a><a name="addelement"></a>CMFC 功能狀態列:新增元素

向功能區狀態列添加新功能區元素。

```cpp
void AddElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>參數

*p 元素*<br/>
[在]指向添加元素的指標。

*lpszLabel*<br/>
[在]元素的文本標籤。

*b 可見*<br/>
[在]如果要將元素添加為可見元素,則為 FALSE,如果要將元素添加為隱藏元素,則為 FALSE。

## <a name="cmfcribbonstatusbaraddextendedelement"></a><a name="addextendedelement"></a>CMFC 功能狀態列:新增延伸元素

將功能區元素添加到功能區狀態列的擴展區域。

```cpp
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>參數

*p 元素*<br/>
[在]指向添加元素的指標。

*lpszLabel*<br/>
[在]元素的文本標籤。

*b 可見*<br/>
[在]如果要將元素添加為可見元素,則為 FALSE,如果要將元素添加為隱藏元素,則為 FALSE。

### <a name="remarks"></a>備註

擴充區域位於狀態列控制項右邊。

## <a name="cmfcribbonstatusbaraddseparator"></a><a name="addseparator"></a>CMFC 狀態列:新增分離器

向功能區狀態列添加分隔符。

```cpp
void AddSeparator();
```

### <a name="remarks"></a>備註

框架在方法[CMFCRibbonStatus 狀態列後加入分隔符:addElement](#addelement)。 插入最後一個元素。

## <a name="cmfcribbonstatusbarcreate"></a><a name="create"></a>CMFC 功能狀態列:建立

創建功能區狀態列。

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
[在]指向父視窗的指標。

*dwStyle*<br/>
[在]控件樣式的邏輯 OR 組合。

*nID*<br/>
[在]狀態列的控制 ID。

### <a name="return-value"></a>傳回值

如果成功創建狀態列,則為 TRUE,否則為 FALSE。

## <a name="cmfcribbonstatusbarcreateex"></a><a name="createex"></a>CMFC 功能狀態列:建立Ex

創建具有擴展樣式的功能區狀態列。

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle=0,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
指向父視窗的指標。

*dwCtrl風格*<br/>
用於創建狀態列物件的其他樣式的邏輯 OR 組合。

*dwStyle*<br/>
狀態欄的控制樣式。

*nID*<br/>
狀態列的控制 ID。

### <a name="return-value"></a>傳回值

如果成功創建狀態列,則為 TRUE,否則為 FALSE。

## <a name="cmfcribbonstatusbarfindbyid"></a><a name="findbyid"></a>CMFC 功能狀態列:尋找ByID

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```

### <a name="parameters"></a>參數

[在]*烏伊CmdID*<br/>
[在]*波爾*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbonstatusbarfindelement"></a><a name="findelement"></a>CMFC 功能狀態列:尋找元素

返回指向具有指定命令 ID 的元素的指標。

```
CMFCRibbonBaseElement* FindElement(UINT uiID);
```

### <a name="parameters"></a>參數

*uiID*<br/>
[在]元素的識別碼。

### <a name="return-value"></a>傳回值

指向具有指定命令 ID 的元素的指標。 如果沒有此類元素,則為 NULL。

## <a name="cmfcribbonstatusbargetcount"></a><a name="getcount"></a>CMFC 功能狀態列:取得計數

返回位於功能區狀態列主區域的元素數。

```
int GetCount() const;
```

### <a name="return-value"></a>傳回值

位於功能區狀態列主區域的元素數。

## <a name="cmfcribbonstatusbargetelement"></a><a name="getelement"></a>CMFC 功能狀態列:取得元素

返回指向位於指定索引的元素的指標。

```
CMFCRibbonBaseElement* GetElement(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[在]指定位於狀態列控制項主區域的元素的零基索引。

### <a name="return-value"></a>傳回值

指向位於指定索引的元素的指標。 如果索引為負或超過狀態列中的元素數,則為 NULL。

### <a name="remarks"></a>備註

## <a name="cmfcribbonstatusbargetexcount"></a><a name="getexcount"></a>CMFC 功能狀態列:取得ExCount

返回位於功能區狀態列擴展區域的元素數。

```
int GetExCount() const;
```

### <a name="return-value"></a>傳回值

位於功能區狀態列擴展區域的元素數。

## <a name="cmfcribbonstatusbargetexelement"></a><a name="getexelement"></a>CMFC 功能狀態列:取得Exelement

傳回指標，該指標指向功能區狀態列擴充區域中，位於指定索引上的元素。 擴充區域位於狀態列控制項右邊。

```
CMFCRibbonBaseElement* GetExElement(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[在]指定位於狀態列控制元件擴展區域的元素的零基索引。

### <a name="return-value"></a>傳回值

此指標指向功能區狀態列擴充區域中，位於指定索引上的元素。 如果*nIndex*為負或超過功能區狀態列擴展區域中的元素數,則 NULL。

### <a name="remarks"></a>備註

## <a name="cmfcribbonstatusbargetextendedarea"></a><a name="getextendedarea"></a>CMFC 功能狀態列:取得延伸區域

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>參數

[在]*rect*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbonstatusbargetspace"></a><a name="getspace"></a>CMFC 功能狀態列:取得空間

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
int GetSpace() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbonstatusbarisbottomframe"></a><a name="isbottomframe"></a>CMFC 功能狀態列::是底部框架

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
BOOL IsBottomFrame() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbonstatusbarisextendedelement"></a><a name="isextendedelement"></a>CMFC 功能狀態列:延伸元素

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;
```

### <a name="parameters"></a>參數

[在]*p 元素*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbonstatusbarisinformationmode"></a><a name="isinformationmode"></a>CMFC 功能狀態列:資訊模式

確定功能區狀態列是否啟用了資訊模式。

```
BOOL IsInformationMode() const;
```

### <a name="return-value"></a>傳回值

如果狀態列可以在資訊模式下工作,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

在資訊模式下,狀態列隱藏所有常規窗格並顯示消息字串。

## <a name="cmfcribbonstatusbarondrawinformation"></a><a name="ondrawinformation"></a>CMFC 功能狀態列::繪製資訊

顯示啟用資訊模式時功能區狀態列上顯示的字串。

```
virtual void OnDrawInformation(
    CDC* pDC,
    CString& strInfo,
    CRect rectInfo);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*斯特資訊*<br/>
[在]資訊字串。

*rectInfo*<br/>
[在]邊界矩形。

### <a name="remarks"></a>備註

如果要自定義狀態列上資訊字串的外觀,請在派生類中重寫此方法。 使用[CMFC 功能狀態列::設定資訊](#setinformation)方法將狀態列置於資訊模式。 在此模式下,狀態列隱藏所有窗格並顯示*strInfo*指定的資訊字串。

## <a name="cmfcribbonstatusbarrecalclayout"></a><a name="recalclayout"></a>CMFC 功能狀態列:Recalclayout

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>備註

## <a name="cmfcribbonstatusbarremoveall"></a><a name="removeall"></a>CMFC 功能狀態列::刪除所有

從功能區狀態列中刪除所有元素。

```cpp
void RemoveAll();
```

## <a name="cmfcribbonstatusbarremoveelement"></a><a name="removeelement"></a>CMFC 狀態列:刪除元素

從功能區狀態列中刪除具有指定命令 ID 的元素。

```
BOOL RemoveElement(UINT uiID);
```

### <a name="parameters"></a>參數

*uiID*<br/>
[在]要從狀態列中刪除的元素的 ID。

### <a name="return-value"></a>傳回值

如果刪除了具有指定*uiID*的元素,則為 TRUE。 否則為 FALSE。

## <a name="cmfcribbonstatusbarsetinformation"></a><a name="setinformation"></a>CMFC 功能狀態列:設定資訊

啟用或禁用功能區狀態欄的資訊模式。

```cpp
void SetInformation(LPCTSTR lpszInfo);
```

### <a name="parameters"></a>參數

*lpszInfo*<br/>
[在]資訊字串。

### <a name="remarks"></a>備註

使用此方法將狀態列置於資訊模式。 在此模式下,狀態列隱藏所有窗格並顯示*lpszInfo*指定的資訊字串。

當 lpszInfo 為 NULL 時,狀態列將恢復為常規模式。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)<br/>
[CMFCRibbonBaseElement 類別](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)
