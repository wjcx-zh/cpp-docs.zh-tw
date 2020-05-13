---
title: CFolderPickerDialog 類別
ms.date: 03/27/2019
f1_keywords:
- CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog::CFolderPickerDialog
helpviewer_keywords:
- CFolderPickerDialog [MFC], CFolderPickerDialog
ms.assetid: 8db01684-dd1d-4e9c-989e-07a2318a8156
ms.openlocfilehash: ed3dc151060519bce216cf4a2f3d6559d6b8937e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373857"
---
# <a name="cfolderpickerdialog-class"></a>CFolderPickerDialog 類別

CFolderPickerDialog 類在資料夾選取器模式下實現 CFileDialog。

## <a name="syntax"></a>語法

```
class CFolderPickerDialog : public CFileDialog;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[夾子拾取者對話::~CFOLDERPicker對話](#_dtorcfolderpickerdialog)|解構函式。|
|[夾子選取器對話框::CfolderPicker對話](#cfolderpickerdialog)|建構函式。|

## <a name="remarks"></a>備註

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[CFileDialog](../../mfc/reference/cfiledialog-class.md)

`CFolderPickerDialog`

## <a name="requirements"></a>需求

**標題:** afxdlgs.h

## <a name="cfolderpickerdialogcfolderpickerdialog"></a><a name="cfolderpickerdialog"></a>夾子選取器對話框::CfolderPicker對話

建構函式。

```
explicit CFolderPickerDialog(
    LPCTSTR lpszFolder = NULL,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL,
    DWORD dwSize = 0);
```

### <a name="parameters"></a>參數

*lpszFolder*<br/>
初始資料夾。

*dwFlags*<br/>
允許您自定義對話方塊的一個或多個標誌的組合。

*pparentwnd*<br/>
指向對話框物件的父視窗或所有者視窗的指標。

*dwSize*<br/>
OPENFILENAME 結構的大小。

### <a name="remarks"></a>備註

## <a name="cfolderpickerdialogcfolderpickerdialog"></a><a name="_dtorcfolderpickerdialog"></a>夾子拾取者對話::~CFOLDERPicker對話

解構函式。

```
virtual ~CFolderPickerDialog();
```

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
