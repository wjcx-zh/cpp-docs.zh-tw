---
title: CDialogBar 類別
ms.date: 11/04/2016
f1_keywords:
- CDialogBar
- AFXEXT/CDialogBar
- AFXEXT/CDialogBar::CDialogBar
- AFXEXT/CDialogBar::Create
helpviewer_keywords:
- CDialogBar [MFC], CDialogBar
- CDialogBar [MFC], Create
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
ms.openlocfilehash: cf9a2658807959108b3bb0af672d4c1835b58bc5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375667"
---
# <a name="cdialogbar-class"></a>CDialogBar 類別

在控制列中提供 Windows 非強制回應對話方塊的功能。

## <a name="syntax"></a>語法

```
class CDialogBar : public CControlBar
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C對話列:CDialog列](#cdialogbar)|建構 `CDialogBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDialog列:建立](#create)|創建 Windows 對話方塊列並將`CDialogBar`其附加到 物件。|

## <a name="remarks"></a>備註

對話框列類似於對話框,因為它包含用戶可以在中間選項卡的標準 Windows 控制件。 另一個相似之處是創建一個對話框範本來表示對話方塊欄。

創建和使用對話方塊列類似於創建和`CFormView`使用 物件。 首先,使用[對話框編輯器](../../windows/dialog-editor.md)定義具有樣式WS_CHILD沒有其他樣式的對話框範本。 範本不能具有樣式WS_VISIBLE。 在應用程式代碼中,調用建構函數建構物件,`CDialogBar`然後呼`Create`叫以建立對話方塊列視窗並將其`CDialogBar`附加到 物件。

有關的詳細資訊`CDialogBar`,請參閱文章[對話方塊條](../../mfc/dialog-bars.md)[和技術說明 31](../../mfc/tn031-control-bars.md),控制欄。

> [!NOTE]
> 在目前的版本中,`CDialogBar`物件無法承載 Windows 窗體控制件。 有關視覺化C++中的 Windows 表單元件的詳細資訊,請參閱[在 MFC 中使用 Windows 元件使用者控制件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[C控制列](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>需求

**標題:** afxext.h

## <a name="cdialogbarcdialogbar"></a><a name="cdialogbar"></a>C對話列:CDialog列

建構 `CDialogBar` 物件。

```
CDialogBar();
```

## <a name="cdialogbarcreate"></a><a name="create"></a>CDialog列:建立

載入`lpszTemplateName``nIDTemplate`或 指定的對話方塊資源樣本,建立對話方塊列視窗,設定其樣式,`CDialogBar`並將其與 物件關聯。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID);

virtual BOOL Create(
    CWnd* pParentWnd,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
指向父`CWnd`物件的指標。

*lpszTemplate 名稱*<br/>
指向`CDialogBar`物件的對話框資源範本名稱的指標。

*nStyle*<br/>
工具欄樣式。 支援的其他工具列樣式包括:

- CBRS_TOP控制欄位於框架視窗的頂部。

- CBRS_BOTTOM控制欄位於框架視窗的底部。

- CBRS_NOALIGN調整父控件欄的大小時,不會重新置放。

- CBRS_TOOLTIPS控制列顯示工具提示。

- CBRS_SIZE_DYNAMIC控制欄是動態的。

- CBRS_SIZE_FIXED控制欄已固定。

- CBRS_FLOATING控制欄是浮動的。

- CBRS_FLYBY 狀態列顯示有關按鈕的資訊。

- CBRS_HIDE_INPLACE控件欄不向用戶顯示。

*nID*<br/>
對話框列的控制 ID。

*nIDTemplate*<br/>
`CDialogBar`對象的對話方塊樣本的資源 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果指定CBRS_TOP或CBRS_BOTTOM對齊樣式,則對話方塊欄的寬度是框架視窗的寬度,其高度是*nIDTemplate*指定的資源。 如果指定CBRS_LEFT或CBRS_RIGHT對齊樣式,則對話方塊列的高度是框架視窗的高度,其寬度是*nIDTemplate*指定的資源的高度。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFormView 類別](../../mfc/reference/cformview-class.md)<br/>
[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)
