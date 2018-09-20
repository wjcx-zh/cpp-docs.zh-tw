---
title: CMiniFrameWnd 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMiniFrameWnd
- AFXWIN/CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::Create
- AFXWIN/CMiniFrameWnd::CreateEx
dev_langs:
- C++
helpviewer_keywords:
- CMiniFrameWnd [MFC], CMiniFrameWnd
- CMiniFrameWnd [MFC], Create
- CMiniFrameWnd [MFC], CreateEx
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9fc66a725cdd9ed5f77b572c70e385f3f32c91b6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446153"
---
# <a name="cminiframewnd-class"></a>CMiniFrameWnd 類別

表示通常在浮動工具列周圍出現的半高度框架視窗。

## <a name="syntax"></a>語法

```
class CMiniFrameWnd : public CFrameWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMiniFrameWnd::CMiniFrameWnd](#cminiframewnd)|建構 `CMiniFrameWnd` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMiniFrameWnd::Create](#create)|建立`CMiniFrameWnd`建構完成之後的物件。|
|[CMiniFrameWnd::CreateEx](#createex)|建立`CMiniFrameWnd`建構完成之後的物件 （與其他選項）。|

## <a name="remarks"></a>備註

這些迷你框架視窗的行為像一般的框架視窗中，不同之處在於它們並沒有最小化/最大化按鈕或功能表，您只需要按一下 [系統] 功能表關閉它們。

若要使用`CMiniFrameWnd`物件，請先定義的物件。 然後呼叫[建立](#create)顯示迷你框架視窗的成員函式。

如需有關如何使用`CMiniFrameWnd`物件，請參閱文章[停駐和浮動工具列](../../mfc/docking-and-floating-toolbars.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cminiframewnd"></a>  CMiniFrameWnd::CMiniFrameWnd

建構`CMiniFrameWnd`物件，但不會建立視窗。

```
CMiniFrameWnd();
```

### <a name="remarks"></a>備註

若要建立視窗，呼叫[CMiniFrameWnd::Create](#create)。

##  <a name="create"></a>  CMiniFrameWnd::Create

建立 Windows 迷你框架視窗，並將它附加至`CMiniFrameWnd`物件。

```
virtual BOOL Create(
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>參數

*lpClassName*<br/>
指向以 null 結束的字元字串，可命名 Windows 類別。 類別名稱可以是任何名稱向全域[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)函式。 如果是 NULL，會為您註冊視窗類別，由架構。 MFC 提供的預設類別，將下列樣式和屬性：

- 設定樣式位元的 CS_DBLCLKS，會將按兩下訊息至視窗程序當使用者按兩下滑鼠。

- 設定樣式位元 CS_HREDRAW 和 CS_VREDRAW，直接重新繪製視窗變更大小時的工作區的內容。

- 設定 Windows 標準 IDC_ARROW 類別資料指標。

- 設定為 NULL，類別的背景筆刷，讓視窗不會清除其背景。

- 將類別圖示設定標準的旗標 Windows 標誌圖示。

- 將設定視窗的預設大小和位置，如 Windows 所示。

*lpWindowName*<br/>
指向以 null 結束的字元字串，包含視窗的名稱。

*cheaderctrl:: Create*<br/>
指定視窗的樣式屬性。 這些可以包括標準的視窗樣式和一或多個下列特殊的樣式：

- MFS_MOVEFRAME 可讓要移動的任何視窗，而不只是標題的邊緣上的 迷你框架視窗。

- 迷你框架視窗的調整大小 MFS_4THICKFRAME 停用。

- MFS_SYNCACTIVE 會同步處理其父視窗啟動迷你框架視窗的啟用。

- 允許 MFS_THICKFRAME 允許迷你框架視窗，而無法調整大小越小，做為工作區的內容。

- MFS_BLOCKSYSMENU 停用存取 [系統] 功能表和 [控制] 功能表中，並將它們轉換成 caption （標題列） 的一部分。

請參閱[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)如需可能的視窗樣式值的描述。 一般用於迷你框架視窗的組合是 WS_POPUP&#124;WS_CAPTION&#124;WS_SYSMENU。

*rect*<br/>
A`RECT`結構，指定視窗的所需的維度。

*pParentWnd*<br/>
父視窗的點。 使用 NULL 為最上層視窗。

*nID*<br/>
如果在迷你框架視窗建立做為子視窗，這會是子控制項; 的識別碼否則為 0。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`Create` 初始化視窗的類別名稱和視窗名稱，並註冊其樣式和父代的預設值。

##  <a name="createex"></a>  CMiniFrameWnd::CreateEx

建立 `CMiniFrameWnd` 物件。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>參數

*dwExStyle*<br/>
指定的擴充的樣式`CMiniFrameWnd`所建立。 套用的任何[延伸視窗樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)至視窗。

*lpClassName*<br/>
指向以 null 結尾的字元字串，可命名 Windows 類別 ( [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576)結構)。 類別名稱可以是任何名稱向全域[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)函式或任何預先定義的控制項類別名稱。 它必須不是 NULL。

*lpWindowName*<br/>
指向以 null 結束的字元字串，包含視窗的名稱。

*cheaderctrl:: Create*<br/>
指定視窗的樣式屬性。 請參閱[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)並[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)如需可能值的描述。

*rect*<br/>
大小和位置的視窗，在用戶端座標*pParentWnd*。

*pParentWnd*<br/>
指向父視窗物件。

*nID*<br/>
子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

`CreateEx`參數會指定 WNDCLASS、 視窗樣式，以及 （選擇性） 初始位置以及視窗的大小。 `CreateEx` 也會指定視窗的父代 （如果有的話） 和識別碼。

當`CreateEx`執行時，Windows 會傳送[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)， [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，並[WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)視窗的訊息。

若要擴充的預設訊息處理，衍生的類別`CMiniFrameWnd`、 將訊息對應新增至新的類別，並出現上述訊息提供成員函式。 覆寫`OnCreate`，例如，若要執行的新類別所需的初始設定。

覆寫進一步`On`*訊息*訊息處理常式，以進一步將功能新增至您的衍生類別。

如果 WS_VISIBLE 樣式已有指定，Windows 會將視窗才能啟動，並顯示視窗的所有訊息。 如果視窗樣式指定的標題列，視窗標題所指*lpszWindowName*參數會顯示在標題列。

*Cheaderctrl:: Create*參數可以是任何組合[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

不再支援舊的樣式調色盤 [工具箱] 視窗。 在舊版 Windows，執行 MFC 應用程式時支援舊的樣式中，沒有"X"按鈕，但已不再支援 Visual c + +.NET 中。 現在支援新 WS_EX_TOOLWINDOW 樣式;如需此樣式的描述，請參閱 <<c0> [ 延伸視窗樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)。

## <a name="see-also"></a>另請參閱

[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)
