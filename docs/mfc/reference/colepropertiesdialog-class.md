---
title: COlePropertiesDialog 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0bd1e6953d936106f272aa8bef4243728d742d8c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078189"
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

|名稱|描述|
|----------|-----------------|
|[COlePropertiesDialog::DoModal](#domodal)|顯示對話方塊，並可讓使用者進行選取。|
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|調整文件項目變更時由架構呼叫。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COlePropertiesDialog::m_gp](#m_gp)|用來初始化 [一般] 頁面的結構`COlePropertiesDialog`物件。|
|[COlePropertiesDialog::m_lp](#m_lp)|結構，用來初始化的 「 連結 」 頁面`COlePropertiesDialog`物件。|
|[COlePropertiesDialog::m_op](#m_op)|結構，用來初始化`COlePropertiesDialog`物件。|
|[COlePropertiesDialog::m_psh](#m_psh)|結構，用來新增額外的自訂屬性頁。|
|[COlePropertiesDialog::m_vp](#m_vp)|若要自訂的 「 檢視 」 頁面所用的結構`COlePropertiesDialog`物件。|

## <a name="remarks"></a>備註

通用 OLE 物件屬性對話方塊提供簡單的方式來顯示和修改 OLE 文件項目與 Windows 標準一致的方式的屬性。 這些屬性包括，其他項目，表示文件項目，顯示的圖示和影像縮放，和資訊的項目連結 （如果項目連結） 的選項之檔案的詳細資訊。

若要使用`COlePropertiesDialog`物件，請先建立物件使用`COlePropertiesDialog`建構函式。 在建構對話方塊之後，請呼叫`DoModal`顯示對話方塊，並允許使用者修改項目的任何屬性的成員函式。 `DoModal` 傳回使用者選取 [確定] (IDOK) 或 [取消 (IDCANCEL)] 按鈕。 除了 [確定] 和 [取消] 按鈕時，還有 [套用] 按鈕。 當使用者選取 [套用] 時，文件項目的屬性所做的變更會套用至項目和其映像會自動更新，但會維持使用中。

[M_psh](#m_psh)資料成員是一個指向`PROPSHEETHEADER`結構，並在大部分情況下，您不需要明確存取它。 當您需要預設的一般、 檢視和連結頁面以外的其他屬性頁時，就會是一個例外。 在此情況下，您可以在其中修改`m_psh`資料成員，以包含您的自訂頁面，然後再呼叫`DoModal`成員函式。

如需有關 OLE 對話方塊的詳細資訊，請參閱文章[對話方塊，在 OLE 中](../../mfc/dialog-boxes-in-ole.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePropertiesDialog`

## <a name="requirements"></a>需求

**標頭：** afxodlgs.h

##  <a name="colepropertiesdialog"></a>  COlePropertiesDialog::COlePropertiesDialog

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
目前正在存取其屬性的文件項目的指標。

*nScaleMin*<br/>
最小縮放比例百分比為文件項目影像。

*nScaleMax*<br/>
最大縮放比例百分比為文件項目影像。

*pParentWnd*<br/>
至對話方塊的父成員或擁有者的指標。

### <a name="remarks"></a>備註

衍生您通用 OLE 物件屬性的對話方塊類別從`COlePropertiesDialog`才能實作調整您的文件項目。 藉由將這個類別的執行個體的任何對話方塊將不支援文件項目的縮放比例。

根據預設，通用 OLE 物件屬性對話方塊中會有三個預設頁面：

- 一般

   此頁面包含所選取的文件項目表示之檔案的系統資訊。 從這個頁面上，使用者可以將選取的項目轉換成另一種類型。

- 檢視

   此頁面包含顯示的項目、 變更圖示，以及變更影像的縮放選項。

- 連結

   此頁面包含選項來變更連結項目的位置和更新連結的項目。 從這個頁面上，使用者可能會中斷選取的項目連結。

若要新增超過所提供的預設頁面，請修改[m_psh](#m_psh)成員變數的建構函式在結束之前您`COlePropertiesDialog`-衍生的類別。 這是進階的實作`COlePropertiesDialog`建構函式。

##  <a name="domodal"></a>  COlePropertiesDialog::DoModal

呼叫此成員函式，以顯示 [Windows 通用 OLE 物件屬性] 對話方塊中，並允許使用者檢視及/或變更文件項目的各種屬性。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

IDOK 或 IDCANCEL 如果登錄成功。否則為 0。 IDOK 及 IDCANCEL 是常數，指出使用者是否已選取 [確定] 或 [取消] 按鈕。

如果傳回 IDCANCEL，您可以呼叫 Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror)函式來判斷是否發生錯誤。

##  <a name="m_gp"></a>  COlePropertiesDialog::m_gp

類型的結構[OLEUIGNRLPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuignrlpropsa)，用來初始化 OLE 物件屬性] 對話方塊的 [一般] 頁面。

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>備註

此頁面會顯示型別和內嵌的大小，並允許使用者存取轉換對話方塊。 此頁面也會顯示連結目的地的物件是否連結。

如需有關`OLEUIGNRLPROPS`結構，請參閱 Windows SDK。

##  <a name="m_lp"></a>  COlePropertiesDialog::m_lp

類型的結構[OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa)，用來初始化 OLE 物件屬性] 對話方塊的 [連結] 頁面。

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>備註

此頁面會顯示連結項目的位置，並可讓使用者更新或中斷，項目的連結。

如需有關`OLEUILINKPROPS`結構，請參閱 Windows SDK。

##  <a name="m_op"></a>  COlePropertiesDialog::m_op

類型的結構[OLEUIOBJECTPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiobjectpropsa)，用來初始化通用 OLE 物件屬性對話方塊。

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>備註

此結構包含用來初始化的一般、 連結和檢視頁面的成員。

如需詳細資訊，請參閱 OLEUIOBJECTPROPS 並[OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa) Windows SDK 中的結構。

##  <a name="m_psh"></a>  COlePropertiesDialog::m_psh

類型的結構[PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2)，其成員儲存對話方塊物件的特性。

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>備註

在建構之後`COlePropertiesDialog`物件，您可以使用`m_psh`若要設定的對話方塊中，然後再呼叫的各個層面`DoModal`成員函式。

如果您修改`m_psh`資料成員直接，您將會覆寫任何預設行為。

如需有關`PROPSHEETHEADER`結構，請參閱 Windows SDK。

##  <a name="m_vp"></a>  COlePropertiesDialog::m_vp

類型的結構[OLEUIVIEWPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiviewpropsa)，用來初始化 OLE 物件屬性] 對話方塊的 [檢視] 頁面。

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>備註

此頁面可讓使用者切換 「 內容 」 和 「 圖示 」 檢視的物件，並變更其調整容器內。 物件會被顯示為圖示時，它也可讓 [變更圖示] 對話方塊中的使用者存取。

如需有關`OLEUIVIEWPROPS`結構，請參閱 Windows SDK。

##  <a name="onapplyscale"></a>  COlePropertiesDialog::OnApplyScale

縮放比例的值已變更，並選取 確定 或 套用時由架構呼叫。

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>參數

*pItem*<br/>
目前正在存取其屬性的文件項目的指標。

*nCurrentScale*<br/>
對話方塊標尺的數值。

*bRelativeToOrig*<br/>
指出是否調整套用至原始文件項目的大小。

### <a name="return-value"></a>傳回值

非零值，如果處理;否則為 0。

### <a name="remarks"></a>備註

預設實作不做任何動作。 您必須覆寫此函式可啟用縮放控制項。

> [!NOTE]
>  通用 OLE 物件屬性對話方塊隨即出現之前，架構會呼叫此函式具有的 NULL *pItem* -1 *nCurrentScale*。 這是為了判斷是否應該啟用縮放控制項。

## <a name="see-also"></a>另請參閱

[MFC 範例 CIRC](../../visual-cpp-samples.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[CPropertyPage 類別](../../mfc/reference/cpropertypage-class.md)
