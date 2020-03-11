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
ms.openlocfilehash: af84c5239a9cb3cbddb1ab4f0230e5b1a3373573
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883615"
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
|[CDialogBar：： CDialogBar](#cdialogbar)|建構 `CDialogBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDialogBar：： Create](#create)|建立 Windows 對話方塊列，並將它附加至 `CDialogBar` 物件。|

## <a name="remarks"></a>備註

對話方塊列類似于對話方塊，其中包含使用者可以在之間定位的標準 Windows 控制項。 另一個相似之處在于，您會建立對話方塊範本來代表對話方塊列。

建立和使用對話方塊列類似于建立和使用 `CFormView` 物件。 首先，使用[對話方塊編輯器](../../windows/dialog-editor.md)來定義具有樣式 WS_CHILD 的對話方塊範本，而不是其他樣式。 範本不能有 WS_VISIBLE 的樣式。 在您的應用程式程式碼中，呼叫函式來建立 `CDialogBar` 物件，然後呼叫 `Create` 以建立對話方塊視窗，並將它附加至 `CDialogBar` 物件。

如需 `CDialogBar`的詳細資訊，請參閱文章[對話方塊](../../mfc/dialog-bars.md)和[技術提示 31](../../mfc/tn031-control-bars.md)，控制列。

> [!NOTE]
>  在目前的版本中，`CDialogBar` 物件無法裝載 Windows Forms 控制項。 如需有關在 Visual C++中 Windows Forms 控制項的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>需求

**標頭：** afxext.h。h

##  <a name="cdialogbar"></a>CDialogBar：： CDialogBar

建構 `CDialogBar` 物件。

```
CDialogBar();
```

##  <a name="create"></a>CDialogBar：： Create

載入 `lpszTemplateName` 或 `nIDTemplate`所指定的對話方塊資源範本、建立對話方塊視窗、設定其樣式，並將其與 `CDialogBar` 物件產生關聯。

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

*pParentWnd*<br/>
父 `CWnd` 物件的指標。

*lpszTemplateName*<br/>
`CDialogBar` 物件之對話方塊資源範本名稱的指標。

*nStyle*<br/>
工具列樣式。 支援的其他工具列樣式包括：

- CBRS_TOP 控制列位於框架視窗的頂端。

- CBRS_BOTTOM 控制列位於框架視窗的底部。

- 當父代調整大小時，不會重新置放 CBRS_NOALIGN 控制列。

- CBRS_TOOLTIPS 控制列會顯示工具提示。

- CBRS_SIZE_DYNAMIC 控制列是動態的。

- 已修正 CBRS_SIZE_FIXED 控制列。

- CBRS_FLOATING 控制條是浮動的。

- CBRS_FLYBY 狀態列會顯示按鈕的相關資訊。

- 不會對使用者顯示 CBRS_HIDE_INPLACE 控制列。

*nID*<br/>
對話方塊列的控制項 ID。

*nIDTemplate*<br/>
`CDialogBar` 物件之對話方塊範本的資源識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果您指定 CBRS_TOP 或 CBRS_BOTTOM 對齊樣式，則對話方塊列的寬度會是框架視窗的寬度，而其高度則是*nIDTemplate*所指定的資源。 如果您指定 CBRS_LEFT 或 CBRS_RIGHT 對齊樣式，則對話方塊列的高度會是框架視窗的高度，而其寬度則是*nIDTemplate*所指定的資源。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFormView 類別](../../mfc/reference/cformview-class.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)
