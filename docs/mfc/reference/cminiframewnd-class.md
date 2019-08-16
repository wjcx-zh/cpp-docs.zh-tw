---
title: CMiniFrameWnd 類別
ms.date: 11/04/2016
f1_keywords:
- CMiniFrameWnd
- AFXWIN/CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::Create
- AFXWIN/CMiniFrameWnd::CreateEx
helpviewer_keywords:
- CMiniFrameWnd [MFC], CMiniFrameWnd
- CMiniFrameWnd [MFC], Create
- CMiniFrameWnd [MFC], CreateEx
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
ms.openlocfilehash: 45b4698cc70487a6c3fe1470fe27f7b5c4f95402
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504594"
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

|名稱|說明|
|----------|-----------------|
|[CMiniFrameWnd::Create](#create)|在結構之後建立物件。`CMiniFrameWnd`|
|[CMiniFrameWnd::CreateEx](#createex)|在結構之後建立物件(包含其他選項)。`CMiniFrameWnd`|

## <a name="remarks"></a>備註

這些迷你框架視窗的行為與一般框架視窗類似, 不同之處在于它們不會有最小化/最大化的按鈕或功能表, 而且您只需要按一下 [系統] 功能表即可關閉它們。

若要使用`CMiniFrameWnd`物件, 請先定義物件。 然後呼叫[Create](#create)成員函式以顯示迷你框架視窗。

如需如何使用`CMiniFrameWnd`物件的詳細資訊, 請參閱[銜接和浮動工具列](../../mfc/docking-and-floating-toolbars.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cminiframewnd"></a>CMiniFrameWnd::CMiniFrameWnd

會構造`CMiniFrameWnd`物件, 但不會建立視窗。

```
CMiniFrameWnd();
```

### <a name="remarks"></a>備註

若要建立視窗, 請呼叫[CMiniFrameWnd:: create](#create)。

##  <a name="create"></a>CMiniFrameWnd:: Create

建立 Windows 迷你框架視窗, 並將其附加至`CMiniFrameWnd`物件。

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
指向以 null 結束的字元字串, 其命名為 Windows 類別。 類別名稱可以是任何以全域[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)函數註冊的名稱。 如果是 Null, 則架構會為您註冊 window 類別。 MFC 會為預設類別提供下列樣式和屬性:

- 設定樣式位 CS_DBLCLKS, 這會在使用者按兩下滑鼠時, 將按兩下訊息傳送至視窗程式。

- 設定樣式位 CS_HREDRAW 和 CS_VREDRAW, 以指示當視窗變更大小時, 要重新繪製的工作區內容。

- 將類別游標設定為 Windows standard IDC_ARROW。

- 將類別背景筆刷設定為 Null, 讓視窗不會清除其背景。

- 將類別圖示設定為標準的揮手旗標 Windows 標誌圖示。

- 將視窗設定為預設大小和位置 (如 Windows 所示)。

*lpWindowName*<br/>
指向以 null 結束的字元字串, 其中包含視窗名稱。

*dwStyle*<br/>
指定視窗樣式屬性。 這些可以包含標準的視窗樣式, 以及下列一或多個特殊樣式:

- MFS_MOVEFRAME 可讓您藉由按一下視窗的任何邊緣, 而不只是標題, 來移動迷你框架視窗。

- MFS_4THICKFRAME 會停用迷你框架視窗的調整大小。

- MFS_SYNCACTIVE 會同步處理迷你框架視窗的啟用, 使其成為其父視窗的啟用。

- MFS_THICKFRAME 可讓迷你框架視窗的大小與工作區允許的內容一樣小。

- MFS_BLOCKSYSMENU 會停用 [系統] 功能表和 [控制] 功能表的存取, 並將其轉換成標題的一部分 (標題列)。

如需可能的視窗樣式值的描述, 請參閱[CWnd:: Create](../../mfc/reference/cwnd-class.md#create) 。 用於迷你框架視窗的一般組合是 WS_POPUP&#124;WS_CAPTION&#124;WS_SYSMENU。

*rect*<br/>
`RECT`結構, 指定所需的視窗維度。

*pParentWnd*<br/>
指向父視窗。 最上層視窗使用 Null。

*nID*<br/>
如果將迷你框架視窗建立為子視窗, 這就是子控制項的識別碼;否則為0。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`Create`初始化視窗的類別名稱和視窗名稱, 並為其樣式和父系註冊預設值。

##  <a name="createex"></a>CMiniFrameWnd:: CreateEx

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
指定要建立之的`CMiniFrameWnd`擴充樣式。 將任何[延伸視窗樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)套用至視窗。

*lpClassName*<br/>
指向以 null 結束的字元字串, 其命名為 Windows 類別 ( [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)結構)。 類別名稱可以是任何以全域[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)函數或任何預先定義的控制項類別名稱註冊的名稱。 不得為 Null。

*lpWindowName*<br/>
指向以 null 結束的字元字串, 其中包含視窗名稱。

*dwStyle*<br/>
指定視窗樣式屬性。 如需可能值的描述, 請參閱[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)和[CWnd:: Create](../../mfc/reference/cwnd-class.md#create) 。

*rect*<br/>
視窗的大小和位置, 以*pParentWnd*的用戶端座標表示。

*pParentWnd*<br/>
指向父視窗物件。

*nID*<br/>
子視窗的識別碼。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE, 失敗時傳回 FALSE。

### <a name="remarks"></a>備註

`CreateEx`參數會指定 WNDCLASS、視窗樣式, 以及 (選擇性) 視窗的初始位置和大小。 `CreateEx`同時指定視窗的父系 (如果有的話) 和識別碼。

當`CreateEx`執行時, Windows 會將[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)、 [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)、 [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)和[WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)訊息傳送至視窗。

若要擴充預設訊息處理, 請從`CMiniFrameWnd`衍生類別, 將訊息對應加入至新的類別, 並為上述訊息提供成員函式。 例如`OnCreate`, 覆寫以執行新類別所需的初始化。

覆寫`On`進一步的*訊息*訊息處理常式, 以將進一步的功能加入至您的衍生類別。

如果指定了 WS_VISIBLE 樣式, Windows 就會傳送所有啟動和顯示視窗所需的訊息給視窗。 如果視窗樣式指定標題列, *lpszWindowName*參數所指向的視窗標題就會顯示在標題列中。

*DwStyle*參數可以是[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)的任意組合。

不再支援舊的樣式調色板 [工具箱] 視窗。 在舊版 Windows 上執行 MFC 應用程式時, 支援不具有 [X] [關閉] 按鈕的舊樣式, 但 Visual C++.net 已不再支援。 現在只支援新的 WS_EX_TOOLWINDOW 樣式;如需此樣式的說明, 請參閱[擴充的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)。

## <a name="see-also"></a>另請參閱

[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)
