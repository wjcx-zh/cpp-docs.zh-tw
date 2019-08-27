---
title: COleUpdateDialog 類別
ms.date: 11/04/2016
f1_keywords:
- COleUpdateDialog
- AFXODLGS/COleUpdateDialog
- AFXODLGS/COleUpdateDialog::COleUpdateDialog
- AFXODLGS/COleUpdateDialog::DoModal
helpviewer_keywords:
- COleUpdateDialog [MFC], COleUpdateDialog
- COleUpdateDialog [MFC], DoModal
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
ms.openlocfilehash: 150e78b7880a61343db21c3c787ffdd1f0b734a5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503161"
---
# <a name="coleupdatedialog-class"></a>COleUpdateDialog 類別

用於 OLE [編輯連結] 對話方塊的特殊狀況，當您只需要更新文件中現有的連結或內嵌物件時，應該使用此項。

## <a name="syntax"></a>語法

```
class COleUpdateDialog : public COleLinksDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|建構 `COleUpdateDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleUpdateDialog::DoModal](#domodal)|以更新模式顯示 [**編輯連結**] 對話方塊。|

## <a name="remarks"></a>備註

如需有關 OLE 特定對話方塊的詳細資訊, 請參閱[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章對話方塊。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

[COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

`COleUpdateDialog`

## <a name="requirements"></a>需求

**標頭:** afxodlgs。h

##  <a name="coleupdatedialog"></a>COleUpdateDialog::COleUpdateDialog

建構 `COleUpdateDialog` 物件。

```
explicit COleUpdateDialog(
    COleDocument* pDoc,
    BOOL bUpdateLinks = TRUE,
    BOOL bUpdateEmbeddings = FALSE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*pDoc*<br/>
指向包含可能需要更新之連結的檔。

*bUpdateLinks*<br/>
判斷是否要更新連結化物件的旗標。

*bUpdateEmbeddings*<br/>
判斷是否要更新内嵌物件的旗標。

*pParentWnd*<br/>
指向對話方塊物件所屬的父系或擁有者視窗物件`CWnd`(類型為)。 如果它是 Null, 則對話方塊的父視窗將會設定為主應用程式視窗。

### <a name="remarks"></a>備註

此函式只會`COleUpdateDialog`對物件進行結構。 若要顯示對話方塊, 請呼叫[DoModal](../../mfc/reference/colelinksdialog-class.md#domodal)。 `COleLinksDialog`當您只想要更新現有的連結或內嵌專案時, 應該使用這個類別, 而不是。

##  <a name="domodal"></a>COleUpdateDialog::D oModal

在更新模式中顯示 [編輯連結] 對話方塊。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話方塊的完成狀態。 下列其中一個值：

- 如果對話方塊傳回成功, 則 IDOK。

- 如果目前檔中沒有任何連結或內嵌專案需要更新, 則 IDCANCEL。

- 如果發生錯誤, 則 IDABORT。 如果傳回 IDABORT, 請呼叫[COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函式, 以取得所發生錯誤類型的詳細資訊。 如需可能錯誤的清單, 請參閱 Windows SDK 中的[OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw)函數。

### <a name="remarks"></a>備註

除非使用者選取 [取消] 按鈕, 否則所有連結和/或內嵌都會更新。

## <a name="see-also"></a>另請參閱

[MFC 範例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleLinksDialog 類別](../../mfc/reference/colelinksdialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleLinksDialog 類別](../../mfc/reference/colelinksdialog-class.md)
