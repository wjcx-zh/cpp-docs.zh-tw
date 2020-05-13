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
ms.openlocfilehash: e9b91161f4207f4d2215d8777beade93617ddfac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319811"
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
|[CMiniFramewnd::CMiniFramewnd](#cminiframewnd)|建構 `CMiniFrameWnd` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMiniFramewnd::創建](#create)|在構造`CMiniFrameWnd`後創建物件。|
|[CMiniFramewnd::創建Ex](#createex)|在建構`CMiniFrameWnd`後創建物件(具有附加選項)。|

## <a name="remarks"></a>備註

這些微型框架視窗與普通框架視窗一樣,只是它們沒有最小化/最大化按鈕或功能表,您只需要單擊系統功能表即可將其關閉。

要使用物件`CMiniFrameWnd`,請先定義該物件。 然後調用[「創建](#create)成員」函數以顯示微型框架視窗。

有關如何使用`CMiniFrameWnd`物件的詳細資訊,請參閱文章[「停靠」和「浮動工具列](../../mfc/docking-and-floating-toolbars.md)」。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cminiframewndcminiframewnd"></a><a name="cminiframewnd"></a>CMiniFramewnd::CMiniFramewnd

建構`CMiniFrameWnd`物件,但不創建視窗。

```
CMiniFrameWnd();
```

### <a name="remarks"></a>備註

要建立視窗,請致電[CMiniFramewnd::建立](#create)。

## <a name="cminiframewndcreate"></a><a name="create"></a>CMiniFramewnd::創建

創建 Windows 迷你框架視窗並將其`CMiniFrameWnd`附加到 物件。

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

*lpClass 名稱*<br/>
指向命名 Windows 類的 null 連接字串。 類名稱可以是註冊到全域[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)函數的任何名稱。 如果 NULL,則框架將為您註冊視窗類。 MFC 為預設類別提供以下樣式和屬性:

- 設置樣式位CS_DBLCLKS,當用戶按兩下滑鼠時,將按兩下消息發送到視窗過程。

- 設置樣式位CS_HREDRAW和CS_VREDRAW,引導工作區的內容在視窗更改大小時重繪。

- 將類游標設置到 Windows 標準IDC_ARROW。

- 將類背景畫筆設定為 NULL,因此視窗不會擦除其背景。

- 將類圖示設置為標準、揮舞標誌的 Windows 徽標圖示。

- 將視窗設置為預設大小和位置,如 Windows 所示。

*lpWindow 名稱*<br/>
包含視窗名稱的 null 連接字串。

*dwStyle*<br/>
指定視窗樣式屬性。 這些可以包括標準視窗樣式與一個或多個以下特殊樣式:

- MFS_MOVEFRAME允許通過按一下視窗的任何邊緣(而不僅僅是標題)移動微型框架視窗。

- MFS_4THICKFRAME禁用小型框架視窗大小。

- MFS_SYNCACTIVE將小型框架視窗的啟動同步到其父窗口的啟動。

- MFS_THICKFRAME 允許將微型框架視窗的大小調整為用戶端區域允許的大小。

- MFS_BLOCKSYSMENU禁用對系統功能表和控制選單的訪問,並將其轉換為標題的一部分(標題列)。

請參閱[CWnd::創建](../../mfc/reference/cwnd-class.md#create)有關可能的視窗樣式值的說明。 用於微型框架視窗的典型組合WS_POPUP&#124;WS_CAPTION&#124;WS_SYSMENU。

*矩形*<br/>
指定`RECT`視窗所需尺寸的結構。

*pparentwnd*<br/>
指向父視窗。 對頂級視窗使用 NULL。

*nID*<br/>
如果將小框架視窗創建為子視窗,則這是子控制件的標識符;如果將微型框架窗口創建為子視窗,則為子控制項的標識符。否則 0。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`Create`初始化視窗的類名稱和視窗名稱,並註冊其樣式和父項的預設值。

## <a name="cminiframewndcreateex"></a><a name="createex"></a>CMiniFramewnd::創建Ex

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
指定正在建立的擴展`CMiniFrameWnd`樣式。 將任何[擴展的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)應用於視窗。

*lpClass 名稱*<br/>
指向命名 Windows 類[(WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)結構)的 null 連接端接字串。 類名稱可以是註冊到全域[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)函數或任何預定義的控制類名稱的名稱。 它不得為 NULL。

*lpWindow 名稱*<br/>
包含視窗名稱的 null 連接字串。

*dwStyle*<br/>
指定視窗樣式屬性。 請參閱[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)和[CWnd::創建](../../mfc/reference/cwnd-class.md#create)可能的值的說明。

*矩形*<br/>
視窗的大小和位置,在*pParentWnd*的用戶端座標中。

*pparentwnd*<br/>
指向父視窗物件。

*nID*<br/>
子窗口的標識碼。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

參數`CreateEx`指定視窗的 WNDCLASS、視窗樣式和(可選)視窗的初始位置和大小。 `CreateEx`還指定視窗的父級(如果有)和 ID。

執行`CreateEx`時,Windows 會向視窗發送[WM_GETMINMAXINFO、WM_NCCREATE、WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccreate)和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)[WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)[WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)消息。

要擴展預設消息處理,請從`CMiniFrameWnd`派生類,向新類添加消息映射,併為上述消息提供成員函數。 例如`OnCreate`,重寫以執行新類所需的初始化。

覆蓋其他`On`*消息消息*處理程式,以向派生類添加更多功能。

如果提供了WS_VISIBLE樣式,Windows會向視窗發送激活和顯示視窗所需的所有消息。 如果視窗樣式指定標題列,*則 lpszWindowName*參數指向的視窗標題將顯示在標題列中。

*dwStyle*參數可以是[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)的任意組合。

舊樣式調色板工具箱視窗不再受支援。 在以前版本的 Windows 上運行 MFC 應用程式時,支援舊樣式,該樣式沒有「X」關閉按鈕,但在 Visual C++.NET 中不再支援。 現在僅支援新的WS_EX_TOOLWINDOW樣式;有關此樣式的說明,請參閱[延伸視窗樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)。

## <a name="see-also"></a>另請參閱

[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)
