---
title: CDialogEx 類別
ms.date: 11/04/2016
f1_keywords:
- CDialogEx
- AFXDIALOGEX/CDialogEx
- AFXDIALOGEX/CDialogEx::CDialogEx
- AFXDIALOGEX/CDialogEx::SetBackgroundColor
- AFXDIALOGEX/CDialogEx::SetBackgroundImage
helpviewer_keywords:
- CDialogEx [MFC], CDialogEx
- CDialogEx [MFC], SetBackgroundColor
- CDialogEx [MFC], SetBackgroundImage
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
ms.openlocfilehash: 717e560035d42957c16168097577d0c8c589e3c7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753358"
---
# <a name="cdialogex-class"></a>CDialogEx 類別

`CDialogEx` 類別會指定對話方塊的背景影像和背景色彩。

## <a name="syntax"></a>語法

```
class CDialogEx : public CDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDialogEx::CDialogEx](#cdialogex)|建構 `CDialogEx` 物件。|
|`CDialogEx::~CDialogEx`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDialogEx::SetBackgroundColor](#setbackgroundcolor)|設定對話方塊的背景色彩。|
|[CDialogEx::SetBackgroundImage](#setbackgroundimage)|設定對話方塊的背景影像。|

## <a name="remarks"></a>備註

若要使用 `CDialogEx` 類別，請將您的對話方塊類別從 `CDialogEx` 類別進行衍生，而不是從 `CDialog` 類別。

對話方塊影像會儲存在資源檔中。 架構會自動刪除從資源檔載入的任何影像。 要以程式設計方式刪除當前背景圖像,請調用[CDialogEx::Set背景影像](#setbackgroundimage)方法`OnDestroy`或實現 事件處理程式。 呼叫[CDialogEx::Set背景影像](#setbackgroundimage)方法時,`HBITMAP`將參數 作為圖像句柄傳遞。 `CDialogEx` 物件會取得影像的擁有權，而若 `m_bAutoDestroyBmp` 旗標是 `TRUE` 的話，則會將它刪除。

對`CDialogEx`象 可以是[CMFCPopupMenu 類](../../mfc/reference/cmfcpopupmenu-class.md)物件的父物件。 [CMFCPopupMenu 類](../../mfc/reference/cmfcpopupmenu-class.md)`CDialogEx::SetActiveMenu`物件在[CMFCPopupMenu 類](../../mfc/reference/cmfcpopupmenu-class.md)物件打開時調用該方法。 之後,`CDialogEx`物件處理任何功能表事件,直到[CMFCPopupMenu 類](../../mfc/reference/cmfcpopupmenu-class.md)物件關閉。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

## <a name="requirements"></a>需求

**標題:** afxdialogex.h

## <a name="cdialogexcdialogex"></a><a name="cdialogex"></a>CDialogEx:CDialogEx

建構 `CDialogEx` 物件。

```
CDialogEx(
    UINT nIDTemplate,
    CWnd* pParent=NULL);

CDialogEx(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd=NULL);
```

### <a name="parameters"></a>參數

*nIDTemplate*<br/>
[在]對話框範本的資源 ID。

*lpszTemplate 名稱*<br/>
[在]對話框範本的資源名稱。

*pParent*<br/>
[在]指向父視窗的指標。 預設值是 NULL。

*pparentwnd*<br/>
[在]指向父視窗的指標。 預設值是 NULL。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdialogexsetbackgroundcolor"></a><a name="setbackgroundcolor"></a>CDialogEx::設定背景顏色

設定對話方塊的背景色彩。

```cpp
void SetBackgroundColor(
    COLORREF color,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>參數

*顏色*<br/>
[在]RGB 顏色值。

*bRepaint*<br/>
[在]TRUE 可立即更新螢幕;否則,FALSE。 預設值為 TRUE。

### <a name="remarks"></a>備註

## <a name="cdialogexsetbackgroundimage"></a><a name="setbackgroundimage"></a>CDialogEx::設定背景影像

設定對話方塊的背景影像。

```cpp
void SetBackgroundImage(
    HBITMAP hBitmap,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bAutoDestroy=TRUE,
    BOOL bRepaint=TRUE);

BOOL SetBackgroundImage(
    UINT uiBmpResId,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>參數

*hBitmap*<br/>
[在]背景圖像的句柄。

*烏布佈雷西德*<br/>
[在]背景圖像的資源識別碼。

*location*<br/>
[在]指定影像位置`CDialogEx::BackgroundLocation`的值之一。 有效值包括BACKGR_TILE、BACKGR_TOPLEFT、BACKGR_TOPRIGHT、BACKGR_BOTTOMLEFT和BACKGR_BOTTOMRIGHT。 默認值為BACKGR_TILE。

*bAuto銷毀*<br/>
[在]TRUE 自動銷毀背景圖像;否則,FALSE。

*bRepaint*<br/>
[在]TRUE 可立即重繪對話方塊;否則,FALSE。

### <a name="return-value"></a>傳回值

在第二個方法重載語法中,如果該方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

指定的圖像不會拉伸以適合對話框工作區。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)<br/>
[CContextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)
