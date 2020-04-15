---
title: COlePropertiesDialog 類別
ms.date: 11/04/2016
f1_keywords:
- COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::DoModal
- AFXODLGS/COlePropertiesDialog::OnApplyScale
- AFXODLGS/COlePropertiesDialog::m_gp
- AFXODLGS/COlePropertiesDialog::m_lp
- AFXODLGS/COlePropertiesDialog::m_op
- AFXODLGS/COlePropertiesDialog::m_psh
- AFXODLGS/COlePropertiesDialog::m_vp
helpviewer_keywords:
- COlePropertiesDialog [MFC], COlePropertiesDialog
- COlePropertiesDialog [MFC], DoModal
- COlePropertiesDialog [MFC], OnApplyScale
- COlePropertiesDialog [MFC], m_gp
- COlePropertiesDialog [MFC], m_lp
- COlePropertiesDialog [MFC], m_op
- COlePropertiesDialog [MFC], m_psh
- COlePropertiesDialog [MFC], m_vp
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
ms.openlocfilehash: f065894ff49af755ab4020f71b0213b19db49054
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374887"
---
# <a name="colepropertiesdialog-class"></a>COlePropertiesDialog 類別

封裝 Windows 通用 OLE 物件屬性對話方塊。

## <a name="syntax"></a>語法

```
class COlePropertiesDialog : public COleDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COle 屬性對話框::COle 屬性對話框](#colepropertiesdialog)|建構 `COlePropertiesDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COle屬性對話::Do模態](#domodal)|顯示對話框,並允許用戶進行選擇。|
|[COle 屬性對話框::應用刻度](#onapplyscale)|當文檔項的縮放已更改時,由框架調用。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COle 屬性對話框::m_gp](#m_gp)|用於初始化`COlePropertiesDialog`物件的「一般」頁的結構。|
|[COle 屬性對話框::m_lp](#m_lp)|用於初始化`COlePropertiesDialog`物件的「連結」頁的結構。|
|[COle 屬性對話框::m_op](#m_op)|初始化物件的結構`COlePropertiesDialog`。|
|[COle屬性對話::m_psh](#m_psh)|用於添加其他自定義屬性頁的結構。|
|[COle屬性對話::m_vp](#m_vp)|用於自定義`COlePropertiesDialog`物件的「檢視」頁的結構。|

## <a name="remarks"></a>備註

通用 OLE 物件屬性對話方塊提供了一種以符合 Windows 標準的方式顯示和修改 OLE 文件項屬性的簡單方法。 這些屬性包括文件項表示的檔資訊、用於顯示圖示和圖像縮放的選項以及項連結上的資訊(如果項是連結的)。

要使用`COlePropertiesDialog`物件,請首先`COlePropertiesDialog`使用 建構函數創建物件。 建構對話框後,調用`DoModal`成員函數以顯示對話方塊,並允許使用者修改項的任何屬性。 `DoModal`返回使用者是否選擇了"確定 (IDOK)"還是"取消"(IDCANCEL)按鈕。 除了"確定"和"取消"按鈕外,還有一個"應用"按鈕。 當使用者選擇"應用"時,對文檔項屬性所做的任何更改將應用於該專案,其圖像將自動更新,但保持活動狀態。

[m_psh](#m_psh)資料成員是指向結構`PROPSHEETHEADER`的指標,在大多數情況下,您不需要顯式訪問它。 一個例外是,當您需要預設的"常規"、"視圖"和"链接"頁以外的其他屬性頁時。 在這種情況下,您可以在調用`m_psh``DoModal`成員函數之前修改數據成員以包括自定義頁面。

有關 OLE 對話框的詳細資訊,請參閱 OLE[中的「對話框](../../mfc/dialog-boxes-in-ole.md)」一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePropertiesDialog`

## <a name="requirements"></a>需求

**標題:** afxodlgs.h

## <a name="colepropertiesdialogcolepropertiesdialog"></a><a name="colepropertiesdialog"></a>COle 屬性對話框::COle 屬性對話框

建立 `COlePropertiesDialog` 物件。

```
COlePropertiesDialog(
    COleClientItem* pItem,
    UINT nScaleMin = 10,
    UINT nScaleMax = 500,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向正在訪問其屬性的文檔項的指標。

*nScaleMin*<br/>
文件項圖像的最小縮放百分比。

*nScaleMax*<br/>
文件項圖像的最大縮放百分比。

*pparentwnd*<br/>
指向對話框的父或所有者的指標。

### <a name="remarks"></a>備註

從`COlePropertiesDialog`派生常見的 OLE 物件屬性對話方塊類,以便實現文檔項的縮放。 此類實例實現的任何對話方塊都不支援文檔項的縮放。

預設情況下,常見的 OLE 物件屬性對話框有三個預設頁面:

- 一般

   此頁包含選取文件項表示的檔的系統資訊。 從此頁面中,用戶可以將所選專案轉換為其他類型。

- 檢視

   此頁包含用於顯示專案、更改圖示和更改圖像縮放的選項。

- 連結

   此頁包含用於更改連結專案的位置和更新連結項的選項。 從此頁面中,用戶可以斷開所選項目的連結。

要將頁面添加到預設提供的頁面之外,請在離開[m_psh](#m_psh)`COlePropertiesDialog`派生類的構造函數之前修改m_psh成員變數。 這是構造函數的高級`COlePropertiesDialog`實現。

## <a name="colepropertiesdialogdomodal"></a><a name="domodal"></a>COle屬性對話::Do模態

調用此成員函數以顯示 Windows 常見 OLE 物件屬性對話方塊,並允許使用者查看和/或更改文檔項的各種屬性。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

IDOK 或 IDCANCEL(如果成功);否則 0。 IDOK 和 IDCANCEL 是指示使用者選擇"確定"還是"取消"按鈕的常量。

如果返回 IDCANCEL,您可以調用 Windows [CommDlg 擴充錯誤](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)功能以確定是否發生了錯誤。

## <a name="colepropertiesdialogm_gp"></a><a name="m_gp"></a>COle 屬性對話框::m_gp

[OLEUIGNRLPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuignrlpropsw)類型的一種結構,用於初始化 OLE 物件屬性對話框的"常規"頁。

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>備註

此頁顯示嵌入的類型和大小,並允許使用者存取"轉換"對話框。 如果對像是連結,此頁面還會顯示連結目標。

有關結構的詳細資訊,`OLEUIGNRLPROPS`請參閱 Windows SDK。

## <a name="colepropertiesdialogm_lp"></a><a name="m_lp"></a>COle 屬性對話框::m_lp

用於初始化 OLE 物件屬性對話框的連結頁的類型[OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw)的結構。

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>備註

此頁顯示連結專案的位置,並允許使用者更新或中斷指向該專案的連結。

有關結構的詳細資訊,`OLEUILINKPROPS`請參閱 Windows SDK。

## <a name="colepropertiesdialogm_op"></a><a name="m_op"></a>COle 屬性對話框::m_op

[用於](/windows/win32/api/oledlg/ns-oledlg-oleuiobjectpropsw)初始化通用 OLE 物件屬性對話框的結構。

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>備註

此結構包含用於初始化常規、鏈接和檢視頁的成員。

有關詳細資訊,請參閱 Windows SDK 中的 OLEUIOBJECTPROPS 和[OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw)結構。

## <a name="colepropertiesdialogm_psh"></a><a name="m_psh"></a>COle屬性對話::m_psh

[PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)類型的一個結構,其成員存儲對話框對象的特徵。

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>備註

建構`COlePropertiesDialog`物件后,可以`m_psh`使用 在`DoModal`調用 成員函數之前設置對話框的各個方面。

如果直接修改`m_psh`數據成員,將覆蓋任何默認行為。

有關結構的詳細資訊,`PROPSHEETHEADER`請參閱 Windows SDK。

## <a name="colepropertiesdialogm_vp"></a><a name="m_vp"></a>COle屬性對話::m_vp

[用於](/windows/win32/api/oledlg/ns-oledlg-oleuiviewpropsw)初始化 OLE 物件屬性對話框的「檢視」頁的結構。

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>備註

此頁面允許使用者在物件的「內容」 和「標誌性」檢視之間切換,並在容器中更改其縮放。 它還允許使用者在物件顯示為圖示時訪問"更改圖示"對話方塊。

有關結構的詳細資訊,`OLEUIVIEWPROPS`請參閱 Windows SDK。

## <a name="colepropertiesdialogonapplyscale"></a><a name="onapplyscale"></a>COle 屬性對話框::應用刻度

當縮放值已更改並選擇了"確定"或"應用"時,由框架調用。

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向正在訪問其屬性的文檔項的指標。

*nCurrentScale*<br/>
對話框刻度的數值。

*b 相對托奧裡格*<br/>
指示縮放是否應用於文檔項的原始大小。

### <a name="return-value"></a>傳回值

處理時非零;否則 0。

### <a name="remarks"></a>備註

預設實作不做任何動作。 必須重寫此函數才能啟用縮放控制件。

> [!NOTE]
> 在顯示常見的 OLE 物件屬性對話框之前,框架呼叫此函數,該函數為*pItem*的 NULL,nCurrentScale 調用 1。 *nCurrentScale* 這樣做是為了確定是否應啟用縮放控件。

## <a name="see-also"></a>另請參閱

[MFC 樣品中國保監會](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[CPropertyPage 類別](../../mfc/reference/cpropertypage-class.md)
