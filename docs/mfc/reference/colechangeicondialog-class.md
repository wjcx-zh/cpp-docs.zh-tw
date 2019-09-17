---
title: COleChangeIconDialog 類別
ms.date: 11/04/2016
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
helpviewer_keywords:
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
ms.openlocfilehash: 4cbf1137a15a9f86a6377980526e6d188f4d0a69
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504773"
---
# <a name="colechangeicondialog-class"></a>COleChangeIconDialog 類別

用於 OLE 的 [變更圖示] 對話方塊。

## <a name="syntax"></a>語法

```
class COleChangeIconDialog : public COleDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|建構 `COleChangeIconDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|執行對話方塊中所指定的變更。|
|[COleChangeIconDialog::DoModal](#domodal)|顯示 [OLE 2 變更圖示] 對話方塊。|
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|取得與這個專案的 iconic 表單相關聯之中繼檔的控制碼。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleChangeIconDialog::m_ci](#m_ci)|結構，控制對話方塊的行為。|

## <a name="remarks"></a>備註

當您想要呼叫`COleChangeIconDialog`此對話方塊時，請建立類別的物件。 在結構化物件之後，您可以使用 [m_ci](#m_ci) 結構，在對話方塊中初始化控制項的值或`COleChangeIconDialog`狀態。 `m_ci`結構的型別為 OLEUICHANGEICON。 如需使用此對話方塊類別的詳細資訊，請參閱[DoModal](#domodal)成員函式。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw)結構。

如需有關 OLE 特定對話方塊的詳細資訊，請參閱[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章對話方塊。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>需求

**標頭：** afxodlgs。h

##  <a name="colechangeicondialog"></a>COleChangeIconDialog::COleChangeIconDialog

此函式只會`COleChangeIconDialog`對物件進行結構。

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向要轉換的專案。

*dwFlags*<br/>
建立旗標，其中包含使用位 or 運算子結合的下列任何數目的值：

- CIF_SELECTCURRENT 指定在呼叫對話方塊時，一開始會選取目前的選項按鈕。 這是預設值。

- CIF_SELECTDEFAULT 指定在呼叫對話方塊時，一開始會選取 [預設] 選項按鈕。

- CIF_SELECTFROMFILE 指定在呼叫對話方塊時，一開始會選取 [從檔案] 選項按鈕。

- CIF_SHOWHELP 指定對話方塊被呼叫時，將會顯示 [說明] 按鈕。

- CIF_USEICONEXE 指定應該從`szIconExe` [m_ci](#m_ci)欄位中指定的可執行檔中解壓縮圖示，而不是從類型抓取。 這適用于內嵌或連結至非 OLE 檔案。

*pParentWnd*<br/>
指向對話方塊物件所屬的父系或擁有者視窗物件`CWnd`（類型為）。 如果它是 Null，則對話方塊的父視窗將會設定為主應用程式視窗。

### <a name="remarks"></a>備註

若要顯示對話方塊，請呼叫[DoModal](#domodal)函式。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw)結構。

##  <a name="dochangeicon"></a>COleChangeIconDialog：:D oChangeIcon

呼叫此函式可在[DoModal](#domodal)傳回 IDOK 之後，將代表專案的圖示變更為對話方塊中所選取的元素。

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向其圖示正在變更的專案。

### <a name="return-value"></a>傳回值

如果變更成功，則為非零值;否則為0。

##  <a name="domodal"></a>COleChangeIconDialog：:D oModal

呼叫此函式以顯示 [OLE 變更圖示] 對話方塊。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話方塊的完成狀態。 下列其中一個值：

- 如果已成功顯示對話方塊，則 IDOK。

- 如果使用者取消對話方塊，則 IDCANCEL。

- 如果發生錯誤，則 IDABORT。 如果傳回 IDABORT，請呼叫`COleDialog::GetLastError`成員函式，以取得所發生錯誤類型的詳細資訊。 如需可能錯誤的清單，請參閱 Windows SDK 中的[OleUIChangeIcon](/windows/win32/api/oledlg/nf-oledlg-oleuichangeiconw)函數。

### <a name="remarks"></a>備註

如果您想要藉由設定[m_ci](#m_ci)結構的成員來初始化各種對話方塊控制項，您應該在呼叫`DoModal`之前執行此動作，但在構造對話方塊物件之後。

如果`DoModal`傳回 IDOK，您可以呼叫其他成員函式，以抓取使用者在對話方塊中輸入的設定或資訊。

##  <a name="geticonicmetafile"></a>COleChangeIconDialog::GetIconicMetafile

呼叫此函式可取得中繼檔的控制碼，其中包含所選取專案的 iconic 層面。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>傳回值

包含新圖示之 iconic 層面的中繼檔控制碼（如果已選擇 **[確定**] 關閉對話方塊）。否則，顯示對話方塊之前的圖示。

##  <a name="m_ci"></a>COleChangeIconDialog::m_ci

OLEUICHANGEICON 類型的結構，用來控制 [變更圖示] 對話方塊的行為。

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>備註

這個結構的成員可以直接或透過成員函式來修改。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw)結構。

## <a name="see-also"></a>另請參閱

[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
