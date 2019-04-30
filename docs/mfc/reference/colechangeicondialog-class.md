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
ms.openlocfilehash: eb5fe38d7cf4058e8de31da3de39dca906671a85
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396167"
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

|名稱|描述|
|----------|-----------------|
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|執行在對話方塊中指定的變更。|
|[COleChangeIconDialog::DoModal](#domodal)|會顯示 OLE 2 變更圖示 對話方塊。|
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|取得與這個項目的圖示格式相關聯的中繼檔的控制代碼。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleChangeIconDialog::m_ci](#m_ci)|結構，以控制對話方塊的行為。|

## <a name="remarks"></a>備註

建立類別的物件`COleChangeIconDialog`當您想要呼叫此對話方塊。 在後`COleChangeIconDialog`在建構物件，您可以使用[m_ci](#m_ci)結構初始化的值或在對話方塊中控制項的狀態。 `m_ci`結構屬於 OLEUICHANGEICON 的型別。 如需使用這個對話方塊類別的詳細資訊，請參閱 < [DoModal](#domodal)成員函式。

如需詳細資訊，請參閱 < [OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) Windows SDK 中的結構。

如需有關特定 OLE 對話方塊的詳細資訊，請參閱[對話方塊，在 OLE 中](../../mfc/dialog-boxes-in-ole.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>需求

**標頭：** afxodlgs.h

##  <a name="colechangeicondialog"></a>  COleChangeIconDialog::COleChangeIconDialog

此函式會建構只`COleChangeIconDialog`物件。

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*pItem*<br/>
要轉換之項目的點。

*dwFlags*<br/>
建立旗標，其中包含任意數目的下列值可讓您結合使用位元的 or 運算子：

- CIF_SELECTCURRENT 指定目前的選項按鈕將會選取一開始時呼叫對話方塊。 這是預設值。

- CIF_SELECTDEFAULT 指定預設選項按鈕將成為最初選取對話方塊中呼叫時。

- CIF_SELECTFROMFILE 指定檔案中的選項按鈕將成為最初選取對話方塊中呼叫時。

- CIF_SHOWHELP 指定對話方塊中呼叫時，會顯示 [說明] 按鈕。

- CIF_USEICONEXE 可讓您指定可執行檔中指定，應該擷取圖示`szIconExe`欄位[m_ci](#m_ci)而不是擷取自型別。 這是適用於內嵌或連結至非 OLE 檔案。

*pParentWnd*<br/>
指向的父系或擁有者的視窗物件 (類型的`CWnd`) 所屬之對話方塊物件。 如果它是 NULL 時，對話方塊中的父視窗將回到主應用程式視窗。

### <a name="remarks"></a>備註

若要顯示的對話方塊，請呼叫[DoModal](#domodal)函式。

如需詳細資訊，請參閱 < [OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) Windows SDK 中的結構。

##  <a name="dochangeicon"></a>  COleChangeIconDialog::DoChangeIcon

呼叫此函式來變更表示在之後的對話方塊中選取一個項目圖示[DoModal](#domodal)傳回 IDOK。

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向其圖示已變更的項目。

### <a name="return-value"></a>傳回值

如果變更成功則為非零否則為 0。

##  <a name="domodal"></a>  COleChangeIconDialog::DoModal

呼叫此函式可顯示 OLE 變更圖示 對話方塊。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話方塊中的完成狀態。 下列其中一個值：

- 如果對話方塊已成功顯示，IDOK。

- 如果使用者已取消對話方塊，IDCANCEL。

- IDABORT 發生錯誤。 如果傳回 IDABORT，呼叫`COleDialog::GetLastError`成員函式，以取得有關所發生的錯誤類型的詳細資訊。 如需可能的錯誤的清單，請參閱 < [OleUIChangeIcon](/windows/desktop/api/oledlg/nf-oledlg-oleuichangeicona) Windows SDK 中的函式。

### <a name="remarks"></a>備註

如果您想要設定的成員初始化各種不同的對話方塊控制項[m_ci](#m_ci)結構，您應該執行這項操作之前先呼叫`DoModal`，但在建構對話方塊物件之後。

如果`DoModal`傳回 IDOK，您可以呼叫其他成員函式來擷取 [設定] 或 [已由使用者輸入] 對話方塊中的資訊。

##  <a name="geticonicmetafile"></a>  COleChangeIconDialog::GetIconicMetafile

呼叫此函式可取得包含選取的項目圖示的層面之中繼檔的控制代碼。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>傳回值

如果已關閉對話方塊，選擇包含 [新增] 圖示，圖示的層面之中繼檔的控制代碼 **[確定]**; 否則對話方塊顯示之前為它的圖示。

##  <a name="m_ci"></a>  COleChangeIconDialog::m_ci

類型 OLEUICHANGEICON 結構用來控制 [變更圖示] 對話方塊中的行為。

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>備註

直接或透過成員函式，則可以修改此結構的成員。

如需詳細資訊，請參閱 < [OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) Windows SDK 中的結構。

## <a name="see-also"></a>另請參閱

[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
