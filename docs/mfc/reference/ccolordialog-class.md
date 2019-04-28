---
title: CColorDialog 類別
ms.date: 11/04/2016
f1_keywords:
- CColorDialog
- AFXDLGS/CColorDialog
- AFXDLGS/CColorDialog::CColorDialog
- AFXDLGS/CColorDialog::DoModal
- AFXDLGS/CColorDialog::GetColor
- AFXDLGS/CColorDialog::GetSavedCustomColors
- AFXDLGS/CColorDialog::SetCurrentColor
- AFXDLGS/CColorDialog::OnColorOK
- AFXDLGS/CColorDialog::m_cc
helpviewer_keywords:
- CColorDialog [MFC], CColorDialog
- CColorDialog [MFC], DoModal
- CColorDialog [MFC], GetColor
- CColorDialog [MFC], GetSavedCustomColors
- CColorDialog [MFC], SetCurrentColor
- CColorDialog [MFC], OnColorOK
- CColorDialog [MFC], m_cc
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
ms.openlocfilehash: bc9bc76b328359d4c8ec7796de7dfaa7d3a9cf2c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207720"
---
# <a name="ccolordialog-class"></a>CColorDialog 類別

可讓您併入您的應用程式中色彩選取範圍 對話方塊。

## <a name="syntax"></a>語法

```
class CColorDialog : public CCommonDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CColorDialog::CColorDialog](#ccolordialog)|建構 `CColorDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CColorDialog::DoModal](#domodal)|顯示 [色彩] 對話方塊，並可讓使用者進行選取。|
|[CColorDialog::GetColor](#getcolor)|傳回`COLORREF`結構，其中包含所選取之色彩的值。|
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|擷取使用者所建立的自訂色彩。|
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|強制執行目前的色彩選取範圍，以指定的色彩。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CColorDialog::OnColorOK](#oncolorok)|覆寫，以驗證輸入到對話方塊中的色彩。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CColorDialog::m_cc](#m_cc)|結構，用來自訂 [] 對話方塊中的設定。|

## <a name="remarks"></a>備註

A`CColorDialog`物件是針對顯示系統定義的色彩清單對話方塊。 使用者可以選取，或從清單中，會接著回報給應用程式 對話方塊中結束時建立特定的色彩。

若要建構`CColorDialog`物件，使用提供的建構函式或衍生新類別，並使用您自己的自訂建構函式。

一旦建構的對話方塊中，您可以設定或修改中的任何值[m_cc](#m_cc)結構，以初始化對話方塊的控制項的值。 *M_cc*結構的類型是[CHOOSECOLOR](/windows/desktop/api/commdlg/ns-commdlg-tagchoosecolora)。

在初始化對話方塊的控制項之後, 呼叫`DoModal`成員函式來顯示對話方塊，並允許使用者選取一種色彩。 `DoModal` 傳回使用者的選取範圍的其中一個對話方塊的 [確定] (IDOK)] 或 [取消 (IDCANCEL) 按鈕。

如果`DoModal`傳回 IDOK，您可以使用其中一個`CColorDialog`的成員函式來擷取使用者所輸入的資訊。

您可以使用 Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror)函式來判斷是否在對話方塊的初始化期間發生錯誤，以及了解錯誤的詳細資訊。

`CColorDialog` 依賴 COMMDLG。隨附於 Windows 版本 3.1 和更新版本的 DLL 檔案。

若要自訂對話方塊中，衍生的類別`CColorDialog`、 提供自訂對話方塊範本，及新增的訊息對應來處理從擴充的控制項通知訊息。 任何未處理的訊息應傳遞至基底類別。

自訂攔截函式不需要。

> [!NOTE]
>  在某些安裝`CColorDialog`如果您已使用架構來進行其他物件不會以灰色背景顯示`CDialog`物件灰色。

如需有關使用`CColorDialog`，請參閱[通用對話方塊類別](../../mfc/common-dialog-classes.md)

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>需求

**標頭：** afxdlgs.h

##  <a name="ccolordialog"></a>  CColorDialog::CColorDialog

建構 `CColorDialog` 物件。

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*clrInit*<br/>
預設色彩選取範圍。 如果未不指定任何值，預設會為 RGB(0,0,0) （黑色）。

*dwFlags*<br/>
一組自訂的功能與外觀上的對話方塊中的旗標。 如需詳細資訊，請參閱 < [CHOOSECOLOR](/windows/desktop/api/commdlg/ns-commdlg-tagchoosecolora) Windows SDK 中的結構。

*pParentWnd*<br/>
對話方塊的父代或擁有者視窗的指標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

##  <a name="domodal"></a>  CColorDialog::DoModal

呼叫此函式來顯示 Windows 通用色彩對話方塊中，而且允許使用者選取一種色彩。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

IDOK 或 IDCANCEL。 如果傳回 IDCANCEL，呼叫 Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror)函式來判斷是否發生錯誤。

IDOK 及 IDCANCEL 是常數，指出使用者是否已選取 [確定] 或 [取消] 按鈕。

### <a name="remarks"></a>備註

如果您想要設定的成員初始化的各種色彩對話方塊選項[m_cc](#m_cc)結構，您應該執行這項操作之前先呼叫`DoModal`但在建構對話方塊物件之後。

之後呼叫`DoModal`，您可以呼叫其他成員函式來擷取在對話方塊中的 設定 或 使用者的資訊輸入。

### <a name="example"></a>範例

  範例，請參閱[CColorDialog::CColorDialog](#ccolordialog)。

##  <a name="getcolor"></a>  CColorDialog::GetColor

呼叫此函式之後呼叫`DoModal`來擷取有關使用者選取的色彩。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

A [COLORREF](/windows/desktop/gdi/colorref)包含 [色彩] 對話方塊中選取的色彩的 RGB 資訊的值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

##  <a name="getsavedcustomcolors"></a>  CColorDialog::GetSavedCustomColors

`CColorDialog` 物件可讓使用者，除了選擇色彩，定義最多 16 個自訂的色彩。

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>傳回值

儲存使用者所建立的自訂色彩 16 的 RGB 色彩值的陣列指標。

### <a name="remarks"></a>備註

`GetSavedCustomColors`成員函式可存取這些色彩。 之後，就可以擷取這些色彩[DoModal](#domodal)傳回 IDOK。

每個 16 RGB 值中傳回的陣列會初始化為 RGB(255,255,255) （白色）。 在應用程式中的 [對話方塊] 方塊引動過程之間只儲存由使用者選擇自訂色彩。 如果您想要儲存這些應用程式的引動過程之間的色彩，您必須將它們儲存以其他方式，例如在初始化期間 (。INI) 檔案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

##  <a name="m_cc"></a>  CColorDialog::m_cc

類型的結構[CHOOSECOLOR](/windows/desktop/api/commdlg/ns-commdlg-tagchoosecolora)，其成員儲存的特性和對話方塊中的值。

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>備註

在建構之後`CColorDialog`物件，您可以使用*m_cc*來設定各種層面的對話方塊中，然後再呼叫[DoModal](#domodal)成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

##  <a name="oncolorok"></a>  CColorDialog::OnColorOK

覆寫，以驗證輸入到對話方塊中的色彩。

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>傳回值

如果不應該關閉對話方塊，為非零否則為 0 表示接受輸入的色彩。

### <a name="remarks"></a>備註

只有當您想要提供自訂驗證的使用者選取 [色彩] 對話方塊中的色彩，請覆寫這個函式。

使用者可以選取一個色彩，由下列兩種方法之一：

- 按一下色彩調色盤上的色彩。 所選取之的色彩的 RGB 值接著會反映在適當的 [RGB] 編輯方塊中。

- 輸入 RGB 值的編輯方塊

覆寫`OnColorOK`可讓您拒絕使用者進入特定應用程式因故常見的 [色彩] 對話方塊的色彩。

一般來說，您不需要使用此函式，因為架構提供的色彩的預設驗證，並顯示訊息方塊，如果輸入無效的色彩。

您可以呼叫[SetCurrentColor](#setcurrentcolor)內在`OnColorOK`強制中色彩選取範圍。 一次`OnColorOK`已經引發 (也就是使用者按下 **[確定]** 以接受變更的色彩)，您可以呼叫[GetColor](#getcolor)取得新色彩的 RGB 值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

##  <a name="setcurrentcolor"></a>  CColorDialog::SetCurrentColor

呼叫此函式之後呼叫`DoModal`強制目前色彩選取範圍中指定的色彩值*clr*。

```
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>參數

*clr*<br/>
RGB 色彩值。

### <a name="remarks"></a>備註

訊息處理常式中呼叫此函式或`OnColorOK`。 對話方塊會自動更新使用者的選取範圍的值為基礎*clr*參數。

### <a name="example"></a>範例

  範例，請參閱[CColorDialog::OnColorOK](#oncolorok)。

## <a name="see-also"></a>另請參閱

[MFC 範例 MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
