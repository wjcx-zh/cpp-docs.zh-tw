---
title: COleDialog 類別
ms.date: 11/04/2016
f1_keywords:
- COleDialog
- AFXODLGS/COleDialog
- AFXODLGS/COleDialog::GetLastError
helpviewer_keywords:
- COleDialog [MFC], GetLastError
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
ms.openlocfilehash: 6a1983d426e97dd8063aee2857dc36557aa20677
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366087"
---
# <a name="coledialog-class"></a>COleDialog 類別

提供 OLE 對話方塊通用的功能。

## <a name="syntax"></a>語法

```
class COleDialog : public CCommonDialog
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDialog:取得最後錯誤](#getlasterror)|獲取對話框返回的錯誤代碼。|

## <a name="remarks"></a>備註

Microsoft 基礎類別庫提供`COleDialog`來自的多個類別:

- [COleInsert 對話](../../mfc/reference/coleinsertdialog-class.md)

- [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)

- [COleChangeIcon對話](../../mfc/reference/colechangeicondialog-class.md)

- [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

- [COleBusy對話](../../mfc/reference/colebusydialog-class.md)

- [COle 更新對話](../../mfc/reference/coleupdatedialog-class.md)

- [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)

- [COle 屬性對話](../../mfc/reference/colepropertiesdialog-class.md)

- [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)

有關特定於 OLE 的對話方塊的詳細資訊,請參閱 OLE[中的「對話框](../../mfc/dialog-boxes-in-ole.md)」一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`COleDialog`

## <a name="requirements"></a>需求

**標題:** afxodlgs.h

## <a name="coledialoggetlasterror"></a><a name="getlasterror"></a>COleDialog:取得最後錯誤

調用`GetLastError`成員函數以在返回 IDABORT`DoModal`時獲取其他錯誤資訊。

```
UINT GetLastError() const;
```

### <a name="return-value"></a>傳回值

傳`GetLastError`回的錯誤代碼取決於顯示的特定對話框。

### <a name="remarks"></a>備註

有關特定`DoModal`錯誤消息的資訊,請參閱派生類中的成員函數。

## <a name="see-also"></a>另請參閱

[CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
