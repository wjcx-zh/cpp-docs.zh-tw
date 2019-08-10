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
ms.openlocfilehash: bdae64ff4a7bcfef761eaf3dd70a85a54efc28b7
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916964"
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
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|建構 `COlePropertiesDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[COlePropertiesDialog::DoModal](#domodal)|顯示對話方塊, 並允許使用者進行選取。|
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|當檔專案的縮放比例變更時由架構呼叫。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[COlePropertiesDialog::m_gp](#m_gp)|用來初始化`COlePropertiesDialog`物件的 [一般] 頁面的結構。|
|[COlePropertiesDialog::m_lp](#m_lp)|用來初始化`COlePropertiesDialog`物件之「連結」頁面的結構。|
|[COlePropertiesDialog::m_op](#m_op)|用來初始化`COlePropertiesDialog`物件的結構。|
|[COlePropertiesDialog::m_psh](#m_psh)|用來加入其他自訂屬性頁的結構。|
|[COlePropertiesDialog::m_vp](#m_vp)|用來自訂`COlePropertiesDialog`物件之「視圖」頁面的結構。|

## <a name="remarks"></a>備註

[一般 OLE 物件屬性] 對話方塊提供簡單的方式, 以與 Windows 標準一致的方式來顯示和修改 OLE 檔專案的屬性。 這些屬性會包含檔專案所代表之檔案的相關資訊、顯示圖示和影像縮放比例的選項, 以及專案連結的相關資訊 (如果專案已連結)。

若要使用`COlePropertiesDialog`物件, 請先使用此`COlePropertiesDialog`函數建立物件。 在結構化對話方塊之後, 呼叫`DoModal`成員函式以顯示對話方塊, 並允許使用者修改專案的任何屬性。 `DoModal`傳回使用者是否選取 [確定] (IDOK) 或 [取消] (IDCANCEL) 按鈕。 除了 [確定] 和 [取消] 按鈕, 還有 [套用] 按鈕。 當使用者選取 [套用] 時, 對檔專案的屬性所做的任何變更都會套用至該專案, 而且其影像會自動更新, 但會保持作用中狀態。

[M_psh](#m_psh)資料成員是`PROPSHEETHEADER`結構的指標, 在大多數情況下, 您不需要明確地存取它。 其中一個例外狀況是當您需要的其他屬性頁超出預設的 [一般]、[視圖] 和 [連結] 頁面時。 在此情況下, 您可以在`m_psh` `DoModal`呼叫成員函式之前, 修改資料成員以包含您的自訂頁面。

如需有關 OLE 對話方塊的詳細資訊, 請參閱[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章對話方塊。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePropertiesDialog`

## <a name="requirements"></a>需求

**標頭:** afxodlgs。h

##  <a name="colepropertiesdialog"></a>COlePropertiesDialog::COlePropertiesDialog

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
要存取其屬性之檔專案的指標。

*nScaleMin*<br/>
檔專案影像的最小縮放百分比。

*nScaleMax*<br/>
檔專案影像的最大縮放百分比。

*pParentWnd*<br/>
對話方塊的父系或擁有者的指標。

### <a name="remarks"></a>備註

從`COlePropertiesDialog`衍生您的一般 OLE 物件屬性對話方塊類別, 以便為您的檔專案進行調整。 這個類別的實例所執行的任何對話方塊都不支援縮放檔專案。

根據預設, [一般 OLE 物件屬性] 對話方塊有三個預設頁面:

- 一般

   此頁面包含所選檔專案所代表之檔案的系統資訊。 在此頁面中, 使用者可以將選取的專案轉換成另一種類型。

- 檢視

   此頁面包含的選項可顯示專案、變更圖示, 以及變更影像的縮放比例。

- 連結

   此頁面包含變更連結專案位置及更新連結專案的選項。 在此頁面中, 使用者可以中斷所選取專案的連結。

若要新增超過預設提供的頁面, 請先修改[m_psh](#m_psh)成員變數, 再`COlePropertiesDialog`結束衍生類別的函式。 這是此函式的先進`COlePropertiesDialog`實作為函數。

##  <a name="domodal"></a>COlePropertiesDialog::D oModal

呼叫這個成員函式以顯示 [Windows 通用 OLE 物件屬性] 對話方塊, 並允許使用者查看和 (或) 變更檔專案的各種屬性。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

IDOK 或 IDCANCEL (如果成功);否則為0。 IDOK 和 IDCANCEL 是常數, 指出使用者是否選取 [確定] 或 [取消] 按鈕。

如果傳回 IDCANCEL, 您可以呼叫 Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror)函數來判斷是否發生錯誤。

##  <a name="m_gp"></a>COlePropertiesDialog::m_gp

類型的結構[OLEUIGNRLPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuignrlpropsa)，用來初始化 OLE 物件屬性對話方塊的 [一般] 頁面。

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>備註

此頁面會顯示內嵌的類型和大小, 並允許使用者存取 [轉換] 對話方塊。 如果物件是連結, 此頁面也會顯示連結目的地。

如需`OLEUIGNRLPROPS`結構的詳細資訊, 請參閱 Windows SDK。

##  <a name="m_lp"></a>COlePropertiesDialog::m_lp

類型的結構[OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa)，用來初始化 OLE 物件屬性對話方塊的 [連結] 頁面。

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>備註

此頁面會顯示連結專案的位置, 並允許使用者更新或中斷專案的連結。

如需`OLEUILINKPROPS`結構的詳細資訊, 請參閱 Windows SDK。

##  <a name="m_op"></a>COlePropertiesDialog::m_op

[OLEUIOBJECTPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiobjectpropsa)類型的結構, 用來初始化 [一般 OLE 物件屬性] 對話方塊。

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>備註

此結構包含用來初始化 [一般]、[連結] 和 [視圖] 頁面的成員。

如需詳細資訊, 請參閱 Windows SDK 中的 OLEUIOBJECTPROPS 和[OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa)結構。

##  <a name="m_psh"></a>COlePropertiesDialog::m_psh

[PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-propsheetheadera_v2)類型的結構, 其成員會儲存對話方塊物件的特性。

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>備註

在建立`COlePropertiesDialog`物件之後, 您可以在`m_psh`呼叫`DoModal`成員函式之前, 使用來設定對話方塊的各個層面。

如果您直接修改`m_psh`資料成員, 將會覆寫任何預設行為。

如需`PROPSHEETHEADER`結構的詳細資訊, 請參閱 Windows SDK。

##  <a name="m_vp"></a>COlePropertiesDialog::m_vp

類型的結構[OLEUIVIEWPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiviewpropsa)，用來初始化 OLE 物件屬性對話方塊的 [檢視] 頁面。

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>備註

此頁面可讓使用者切換物件的「內容」和「iconic」視圖, 以及變更其在容器內的縮放比例。 當物件顯示為圖示時, 它也可讓使用者存取 [變更圖示] 對話方塊。

如需`OLEUIVIEWPROPS`結構的詳細資訊, 請參閱 Windows SDK。

##  <a name="onapplyscale"></a>COlePropertiesDialog::OnApplyScale

當調整值已變更, 且已選取 [確定] 或 [套用] 時, 由架構呼叫。

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>參數

*pItem*<br/>
要存取其屬性之檔專案的指標。

*nCurrentScale*<br/>
對話方塊小數位數的數值。

*bRelativeToOrig*<br/>
指出縮放是否適用于檔專案的原始大小。

### <a name="return-value"></a>傳回值

若已處理, 則為非零否則為0。

### <a name="remarks"></a>備註

預設實作不做任何動作。 您必須覆寫這個函式, 才能啟用縮放控制項。

> [!NOTE]
>  在顯示 [一般 OLE 物件屬性] 對話方塊之前, 架構會呼叫此函式, 並以 Null 表示*pItem* , 而*nCurrentScale*則會使用-1。 這麼做是為了判斷是否應啟用縮放控制項。

## <a name="see-also"></a>另請參閱

[MFC 範例 CIRC](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[CPropertyPage 類別](../../mfc/reference/cpropertypage-class.md)
