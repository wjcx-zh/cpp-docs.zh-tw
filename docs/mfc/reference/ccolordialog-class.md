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
ms.openlocfilehash: f5c235008b72996424e01ee912ca78ecffab450a
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741582"
---
# <a name="ccolordialog-class"></a>CColorDialog 類別

可讓您將色彩選取對話方塊併入應用程式中。

## <a name="syntax"></a>語法

```
class CColorDialog : public CCommonDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CColorDialog::CColorDialog](#ccolordialog)|建構 `CColorDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CColorDialog::DoModal](#domodal)|顯示 [色彩] 對話方塊，並允許使用者進行選取。|
|[CColorDialog::GetColor](#getcolor)|`COLORREF`傳回結構，其中包含所選色彩的值。|
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|抓取使用者所建立的自訂色彩。|
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|強制目前的色彩選取範圍指定的色彩。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CColorDialog::OnColorOK](#oncolorok)|覆寫以驗證在對話方塊中輸入的色彩。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CColorDialog::m_cc](#m_cc)|用來自訂對話方塊設定的結構。|

## <a name="remarks"></a>備註

`CColorDialog`物件是一個對話方塊，其中包含針對顯示系統定義的色彩清單。 使用者可以從清單中選取或建立特定的色彩，然後在對話方塊結束時回報給應用程式。

若要建立`CColorDialog`物件，請使用所提供的函式，或衍生新的類別，並使用您自己的自訂函式。

建立對話方塊之後，您可以設定或修改[m_cc](#m_cc)結構中的任何值，以初始化對話方塊控制項的值。 *M_cc*結構的類型為[CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1)。

在初始化對話方塊的控制項之後，呼叫`DoModal`成員函式以顯示對話方塊，並允許使用者選取色彩。 `DoModal`傳回使用者選取對話方塊的 [確定] （IDOK）或 [取消] （IDCANCEL）按鈕。

如果`DoModal`傳回 IDOK，您可以使用`CColorDialog`的其中一個成員函式來取出使用者輸入的資訊。

您可以使用 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)函式來判斷對話方塊初始化期間是否發生錯誤，並深入瞭解錯誤。

`CColorDialog`依賴 COMMDLG。Windows 3.1 和更新版本隨附的 DLL 檔案。

若要自訂對話方塊、從`CColorDialog`衍生類別，請提供自訂對話方塊範本，並加入訊息對應以處理來自擴充控制項的通知訊息。 任何未處理的訊息都應該傳遞至基類。

不需要自訂攔截函數。

> [!NOTE]
>  在某些安裝上`CColorDialog` ，如果您已經使用架構讓其他`CDialog`物件變成灰色，物件就不會以灰色背景顯示。

如需使用`CColorDialog`的詳細資訊，請參閱[通用對話方塊類別](../../mfc/common-dialog-classes.md)

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>需求

**標頭：** afxdlgs。h

##  <a name="ccolordialog"></a>CColorDialog::CColorDialog

建構 `CColorDialog` 物件。

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*clrInit*<br/>
預設色彩選取範圍。 如果未指定任何值，則預設值為 RGB （0，0，0）（黑色）。

*dwFlags*<br/>
一組旗標，可自訂對話方塊的功能和外觀。 如需詳細資訊，請參閱 Windows SDK 中的[CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1)結構。

*pParentWnd*<br/>
對話方塊的父代或擁有者視窗的指標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

##  <a name="domodal"></a>CColorDialog：:D oModal

呼叫此函式以顯示 [Windows 通用色彩] 對話方塊，並允許使用者選取色彩。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

IDOK 或 IDCANCEL。 如果傳回 IDCANCEL，請呼叫 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)函數來判斷是否發生錯誤。

IDOK 和 IDCANCEL 是常數，指出使用者是否選取 [確定] 或 [取消] 按鈕。

### <a name="remarks"></a>備註

如果您想要藉由設定[m_cc](#m_cc)結構的成員來初始化各種 [色彩] 對話方塊選項，您應該在呼叫`DoModal`之前執行此動作，但在構造對話方塊物件之後。

呼叫`DoModal`之後，您可以呼叫其他成員函式，以抓取使用者在對話方塊中輸入的設定或資訊。

### <a name="example"></a>範例

  請參閱[CColorDialog：： CColorDialog](#ccolordialog)的範例。

##  <a name="getcolor"></a>CColorDialog：： GetColor

呼叫`DoModal`以抓取使用者所選取之色彩的相關資訊之後，呼叫這個函式。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

[COLORREF](/windows/win32/gdi/colorref)值，其中包含 [色彩] 對話方塊中所選取之色彩的 RGB 資訊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

##  <a name="getsavedcustomcolors"></a>CColorDialog::GetSavedCustomColors

`CColorDialog`除了選擇色彩以外，物件也允許使用者定義多達16個自訂色彩。

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>傳回值

16 RGB 色彩值陣列的指標，可儲存使用者所建立的自訂色彩。

### <a name="remarks"></a>備註

成員`GetSavedCustomColors`函式提供這些色彩的存取權。 這些色彩可以在[DoModal](#domodal)傳回 IDOK 之後取得。

傳回之陣列中的每個 16 RGB 值都會初始化為 RGB （255255255）（白色）。 使用者選擇的自訂色彩只會儲存在應用程式內的對話方塊調用。 如果您想要在應用程式的調用之間儲存這些色彩，您必須以其他方式儲存它們，例如在初始化中（。INI）檔案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

##  <a name="m_cc"></a>CColorDialog::m_cc

[CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1)類型的結構，其成員會儲存對話方塊的特性和值。

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>備註

在建立`CColorDialog`物件之後，您可以在呼叫[DoModal](#domodal)成員函式之前，使用*m_cc*來設定對話方塊的各個層面。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

##  <a name="oncolorok"></a>CColorDialog::OnColorOK

覆寫以驗證在對話方塊中輸入的色彩。

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>傳回值

如果不應關閉對話方塊，則為非零。否則為0，表示接受所輸入的色彩。

### <a name="remarks"></a>備註

只有當您想要為使用者在 [色彩] 對話方塊中選取的色彩提供自訂驗證時，才覆寫此函數。

使用者可以使用下列兩種方法的其中一種來選取色彩：

- 按一下色彩色板上的色彩。 選取的色彩 RGB 值接著會反映在適當的 RGB 編輯方塊中。

- 在 RGB 編輯方塊中輸入值

覆`OnColorOK`寫可讓您拒絕使用者針對任何應用程式特定原因，進入通用色彩對話方塊的色彩。

一般來說，您不需要使用此函式，因為架構會提供色彩的預設驗證，並在輸入不正確色彩時顯示訊息方塊。

您可以從中`OnColorOK`呼叫 [SetCurrentColor](#setcurrentcolor)，以強制選取色彩。 一旦`OnColorOK`引發（也就是使用者按一下 **[確定]** 以接受色彩變更），您可以呼叫[GetColor](#getcolor)來取得新色彩的 RGB 值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

##  <a name="setcurrentcolor"></a>CColorDialog::SetCurrentColor

在呼叫`DoModal`之後呼叫此函式，以強制目前的色彩選取範圍為*clr*中指定的色彩值。

```
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>參數

*clr*<br/>
RGB 色彩值。

### <a name="remarks"></a>備註

此函式是從訊息處理常式或`OnColorOK`內呼叫。 對話方塊會根據*clr*參數的值，自動更新使用者的選取專案。

### <a name="example"></a>範例

  請參閱[CColorDialog：： OnColorOK](#oncolorok)的範例。

## <a name="see-also"></a>另請參閱

[MFC 範例 MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
