---
title: CCommonDialog 類別
ms.date: 11/04/2016
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
helpviewer_keywords:
- CCommonDialog [MFC], CCommonDialog
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
ms.openlocfilehash: 853a4756df3b70f4f33deb7159b4d1aee610092c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369451"
---
# <a name="ccommondialog-class"></a>CCommonDialog 類別

封裝 Windows 通用對話方塊功能之類別的基底類別。

## <a name="syntax"></a>語法

```
class CCommonDialog : public CDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C 公共對話:C 公共對話](#ccommondialog)|建構 `CCommonDialog` 物件。|

## <a name="remarks"></a>備註

以下類別封裝 Windows 通用對話框的功能:

- [CFileDialog](../../mfc/reference/cfiledialog-class.md)

- [CFontDialog](../../mfc/reference/cfontdialog-class.md)

- [CColorDialog](../../mfc/reference/ccolordialog-class.md)

- [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)

- [CPrintDialog](../../mfc/reference/cprintdialog-class.md)

- [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)

- [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)

- [COleDialog](../../mfc/reference/coledialog-class.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CCommonDialog`

## <a name="requirements"></a>需求

**標題:** afxdlgs.h

## <a name="ccommondialogccommondialog"></a><a name="ccommondialog"></a>C 公共對話:C 公共對話

建構 `CCommonDialog` 物件。

```
explicit CCommonDialog(CWnd* pParentWnd);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
指向對話框物件所屬的父視窗或所有者視窗物件[(CWnd](../../mfc/reference/cwnd-class.md)類型)。 如果為 NULL,則對話方塊物件的父視窗將設置為主應用程式視窗。

### <a name="remarks"></a>備註

有關詳細資訊[,請參閱 CDialog:CDialog。](../../mfc/reference/cdialog-class.md#cdialog)

## <a name="see-also"></a>另請參閱

[CDialog 類別](../../mfc/reference/cdialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)<br/>
[CFontDialog 類別](../../mfc/reference/cfontdialog-class.md)<br/>
[CColorDialog 類別](../../mfc/reference/ccolordialog-class.md)<br/>
[CPageSetupDialog 類別](../../mfc/reference/cpagesetupdialog-class.md)<br/>
[CPrintDialog 類別](../../mfc/reference/cprintdialog-class.md)<br/>
[CFindReplaceDialog 類別](../../mfc/reference/cfindreplacedialog-class.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
