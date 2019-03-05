---
title: CFolderPickerDialog 類別
ms.date: 11/04/2016
f1_keywords:
- CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog::CFolderPickerDialog
helpviewer_keywords:
- CFolderPickerDialog [MFC], CFolderPickerDialog
ms.assetid: 8db01684-dd1d-4e9c-989e-07a2318a8156
ms.openlocfilehash: f1718919a4fe9019ef591d83473c118eba966900
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276178"
---
# <a name="cfolderpickerdialog-class"></a>CFolderPickerDialog 類別

CFolderPickerDialog 類別實作資料夾選擇器模式的 CFileDialog。

## <a name="syntax"></a>語法

```
class CFolderPickerDialog : public CFileDialog;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CFolderPickerDialog::~CFolderPickerDialog](#cfolderpickerdialog__~cfolderpickerdialog)|解構函式。|
|[CFolderPickerDialog::CFolderPickerDialog](#cfolderpickerdialog)|建構函式。|

## <a name="remarks"></a>備註

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[CFileDialog](../../mfc/reference/cfiledialog-class.md)

`CFolderPickerDialog`

## <a name="requirements"></a>需求

**標頭：** afxdlgs.h

##  <a name="cfolderpickerdialog"></a>  CFolderPickerDialog::CFolderPickerDialog

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
初始的資料夾。

*dwFlags*<br/>
可讓您自訂對話方塊中的一或多個旗標的組合。

*pParentWnd*<br/>
對話方塊物件的父系或擁有者視窗的指標。

*dwSize*<br/>
OPENFILENAME 結構的大小。

### <a name="remarks"></a>備註

##  <a name="_dtorcfolderpickerdialog"></a>  CFolderPickerDialog:: ~ CFolderPickerDialog

解構函式。

```
virtual ~CFolderPickerDialog();
```

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
