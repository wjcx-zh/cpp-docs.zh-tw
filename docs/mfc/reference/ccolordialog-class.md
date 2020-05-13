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
ms.openlocfilehash: 99b4ff27a7686972bcbc85478998b52ed713ab5b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754268"
---
# <a name="ccolordialog-class"></a>CColorDialog 類別

允許您將顏色選擇對話方塊合併到應用程式中。

## <a name="syntax"></a>語法

```
class CColorDialog : public CCommonDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CColor對話:CColorDialog](#ccolordialog)|建構 `CColorDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CColorDialog::Do模態](#domodal)|顯示顏色對話框,並允許用戶進行選擇。|
|[CColor對話:抓取顏色](#getcolor)|返回包含`COLORREF`所選顏色值的結構。|
|[CColorDialog:抓取儲存的自訂顏色](#getsavedcustomcolors)|檢索用戶創建的自定義顏色。|
|[CColor對話::設定目前的顏色](#setcurrentcolor)|將目前顏色選擇強制為指定顏色。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CColorDialog::在ColorOK上](#oncolorok)|覆蓋以驗證輸入到對話框中的顏色。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CColorDialog:m_cc](#m_cc)|用於自定義對話框設置的結構。|

## <a name="remarks"></a>備註

對`CColorDialog`像是一個對話框,其中包含為顯示系統定義的顏色清單。 用戶可以從清單中選擇或創建特定顏色,然後在對話方塊退出時向應用程式報告該顏色。

要建構`CColorDialog`物件,請使用提供的構造函數或派生一個新類,並使用您自己的自定義構造函數。

建構對話框後,可以設置或修改[m_cc](#m_cc)結構中的任何值,以初始化對話方塊控制項的值。 *m_cc*結構的類型[是CHOOSECOLOR。](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1)

初始化對話框的控制項後,呼叫`DoModal`成員函數以顯示對話方塊並允許使用者選擇顏色。 `DoModal`返回使用者選擇的對話框的「確定」(IDOK)或「取消」(IDCANCEL)按鈕。

如果`DoModal`返回 IDOK,則可以使用 『`CColorDialog`的成員 函數之一來檢索用戶輸入的資訊。

您可以使用 Windows [CommDlg 擴充錯誤](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)功能來確定在對話方塊的初始化過程中是否發生了錯誤,並瞭解有關該錯誤的詳細資訊。

`CColorDialog`依賴於 COMMDLG。隨 Windows 版本 3.1 及更高版本一起附帶的 DLL 檔。

要自定義對話框,請從`CColorDialog`派生類,並提供自定義對話框範本,並添加消息映射來處理來自擴展控制項的通知消息。 任何未處理的消息都應傳遞到基類。

不需要自定義挂鉤功能。

> [!NOTE]
> 在某些安裝上,如果使用`CColorDialog`框架使其他`CDialog`物件變為灰色,則物件將不會以灰色背景顯示。

有關`CColorDialog`使用的詳細資訊,請參閱[通用對話方塊類別](../../mfc/common-dialog-classes.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>需求

**標題:** afxdlgs.h

## <a name="ccolordialogccolordialog"></a><a name="ccolordialog"></a>CColor對話:CColorDialog

建構 `CColorDialog` 物件。

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*克利尼特*<br/>
默認顏色選擇。 如果未指定值,則預設值為 RGB(0,0,0)(黑色)。

*dwFlags*<br/>
自定義對話框的功能和外觀的一組標誌。 有關詳細資訊,請參閱 Windows SDK 中的[CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1)結構。

*pparentwnd*<br/>
指向對話框的父視窗或所有者視窗的指標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

## <a name="ccolordialogdomodal"></a><a name="domodal"></a>CColorDialog::Do模態

呼叫此函數以顯示 Windows 通用顏色對話框,並允許使用者選擇顏色。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

IDOK 或 IDCANCEL。 如果返回 IDCANCEL,請呼叫 Windows [CommDlg 擴充錯誤](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)功能以確定是否發生了錯誤。

IDOK 和 IDCANCEL 是指示使用者選擇"確定"還是"取消"按鈕的常量。

### <a name="remarks"></a>備註

如果要通過設置[m_cc](#m_cc)結構的成員來初始化各種顏色對話方塊選項,則應`DoModal`在調用 之前在建構對話方物件之後執行此操作。

調用`DoModal`後 ,可以調用其他成員函數來檢索使用者輸入到對話方塊中的設置或資訊。

### <a name="example"></a>範例

  請參考[CColorDialog 的範例:CColorDialog](#ccolordialog)。

## <a name="ccolordialoggetcolor"></a><a name="getcolor"></a>CColor對話:抓取顏色

調用`DoModal`後調用此功能以檢索有關用戶選擇的顏色的資訊。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

包含顏色對話框中選擇顏色的 RGB 資訊的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

## <a name="ccolordialoggetsavedcustomcolors"></a><a name="getsavedcustomcolors"></a>CColorDialog:抓取儲存的自訂顏色

`CColorDialog`對象允許使用者除了選擇顏色外,還允許定義多達 16 種自定義顏色。

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>傳回值

指向 16 個 RGB 顏色值的陣列的指標,用於儲存使用者創建的自定義顏色。

### <a name="remarks"></a>備註

成員`GetSavedCustomColors`函數提供對這些顏色的訪問。 這些顏色可以在[DoModal](#domodal)傳回 IDOK 後檢索。

返回的陣列中的 16 個 RGB 值中的每一個都初始化為 RGB(255,255,255)(白色)。 用戶選擇的自定義顏色僅在應用程式中的對話框調用之間保存。 如果要在應用程式的調用之間保存這些顏色,則必須以其他某種方式(如初始化 () 保存這些顏色。INI) 檔案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

## <a name="ccolordialogm_cc"></a><a name="m_cc"></a>CColorDialog:m_cc

類型[CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1)的結構,其成員存儲對話框的特徵和值。

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>備註

建構`CColorDialog`物件後,可以使用*m_cc*在調用[DoModal](#domodal)成員函數之前設置對話框的各個方面。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

## <a name="ccolordialogoncolorok"></a><a name="oncolorok"></a>CColorDialog::在ColorOK上

覆蓋以驗證輸入到對話框中的顏色。

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>傳回值

如果不應取消對話框,則非零;否則 0 接受輸入的顏色。

### <a name="remarks"></a>備註

僅當要提供使用者在顏色對話框中選擇的顏色的自定義驗證時,才覆蓋此函數。

使用者可以通過以下兩種方法之一選擇顏色:

- 按一下調色板上的顏色。 然後,所選顏色的 RGB 值將反映在相應的 RGB 編輯框中。

- 在 RGB 編輯框中輸入值

重寫`OnColorOK`允許您拒絕使用者出於任何應用程式特定原因輸入到公共顏色對話方塊中的顏色。

通常,您不需要使用此函數,因為框架提供預設的顏色驗證,並在輸入無效顏色時顯示消息框。

可以從內部`OnColorOK`調用[SetCurrentColor](#setcurrentcolor)以強制選擇顏色。 一`OnColorOK`旦已觸發(即,使用者按下 **"確定"** 以接受顏色更改),您可以調用[GetColor](#getcolor)獲取新顏色的 RGB 值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

## <a name="ccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a>CColor對話::設定目前的顏色

呼叫`DoModal`後呼叫此函數以強制目前的顏色選擇到*clr*中指定的顏色值。

```cpp
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>參數

*Clr*<br/>
RGB 顏色值。

### <a name="remarks"></a>備註

此函數是從消息處理程式或`OnColorOK`調用的。 該對話框將根據*clr*參數的值自動更新使用者的選擇。

### <a name="example"></a>範例

  請參閱[CColorDialog 的範例::在ColorOK](#oncolorok)上。

## <a name="see-also"></a>另請參閱

[MFC 樣品 MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
