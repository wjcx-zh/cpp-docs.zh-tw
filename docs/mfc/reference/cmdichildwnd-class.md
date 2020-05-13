---
title: CMDIChildWnd 類別
ms.date: 11/04/2016
f1_keywords:
- CMDIChildWnd
- AFXWIN/CMDIChildWnd
- AFXWIN/CMDIChildWnd::CMDIChildWnd
- AFXWIN/CMDIChildWnd::Create
- AFXWIN/CMDIChildWnd::GetMDIFrame
- AFXWIN/CMDIChildWnd::MDIActivate
- AFXWIN/CMDIChildWnd::MDIDestroy
- AFXWIN/CMDIChildWnd::MDIMaximize
- AFXWIN/CMDIChildWnd::MDIRestore
- AFXWIN/CMDIChildWnd::SetHandles
helpviewer_keywords:
- CMDIChildWnd [MFC], CMDIChildWnd
- CMDIChildWnd [MFC], Create
- CMDIChildWnd [MFC], GetMDIFrame
- CMDIChildWnd [MFC], MDIActivate
- CMDIChildWnd [MFC], MDIDestroy
- CMDIChildWnd [MFC], MDIMaximize
- CMDIChildWnd [MFC], MDIRestore
- CMDIChildWnd [MFC], SetHandles
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
ms.openlocfilehash: a547a21b96d035f507e749aeb19f891175498d5d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754572"
---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd 類別

提供 Windows 多重文件介面 (MDI) 子視窗的功能，以及管理視窗的成員。

## <a name="syntax"></a>語法

```
class CMDIChildWnd : public CFrameWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMDIChildwnd:CMDIChildwnd](#cmdichildwnd)|建構 `CMDIChildWnd` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMDIChildwnd:創建](#create)|創建與`CMDIChildWnd`物件關聯的 Windows MDI 子視窗。|
|[CMDIChildwnd::GetMDIFrame](#getmdiframe)|返回 MDI 用戶端視窗的父 MDI 幀。|
|[CMDIChildwnd:MDIActivate](#mdiactivate)|啟動此 MDI 子視窗。|
|[CMDIChildwnd:MDI銷毀](#mdidestroy)|銷毀此 MDI 子視窗。|
|[CMDIChildwnd::MDI最大化](#mdimaximize)|最大化此 MDI 子視窗。|
|[CMDIChildwnd::MDI恢復](#mdirestore)|從最大大小或最小化大小還原此 MDI 子視窗。|
|[CMDIChildwnd::設置手柄](#sethandles)|設置功能表和快捷鍵資源的句柄。|

## <a name="remarks"></a>備註

MDI 子視窗與典型的框架視窗非常類似,只不過 MDI 子視窗顯示在 MDI 框架視窗內,而不是桌面上。 MDI 子視窗沒有自己的功能表欄,而是共用 MDI 框架視窗的功能表。 框架會自動更改 MDI 框架功能表以表示當前處於活動狀態的 MDI 子視窗。

要為應用程式創建有用的 MDI 子視窗,`CMDIChildWnd`請從 派生類。 將成員變數添加到派生類以存儲特定於應用程式的數據。 實作訊息處理常式成員函式，和衍生類別中對應的訊息，以指定訊息被導向至視窗時會發生什麼事。

有三種方法可以建構 MDI 子視窗:

- 使用`Create`直接構造它。

- 使用`LoadFrame`直接構造它。

- 通過文檔範本間接構造它。

在調用`Create``LoadFrame`或之前,必須**使用新運算符**C++在堆上構造幀視窗物件。 在調用`Create`之前,您還可以使用[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全域函數註冊視窗類,以設置框架的圖示和類樣式。

使用`Create`成員函數將幀的創建參數作為即時參數傳遞。

`LoadFrame`需要的參數少於`Create`,而是從資源檢索其大部分預設值,包括框架的標題、圖示、快速鍵表和菜單。 要被`LoadFrame`訪問,所有這些資源必須具有相同的資源 ID(例如,IDR_MAINFRAME)。

當物件`CMDIChildWnd`包含檢視和文檔時,它們由框架間接創建,而不是由程式師直接創建。 該`CDocTemplate`物件協調框架的創建、包含檢視的創建以及檢視與相應文件的連接。 建構函數的`CDocTemplate`參數指定所涉及的`CRuntimeClass`三 個類(文檔、框架和檢視)的參數。 框架`CRuntimeClass`使用物件在使用者指定時動態創建新框架(例如,通過使用"檔案新建"命令或 MDI Window New 命令)。

必須用DECLARE_DYNCREATE聲明派生的`CMDIChildWnd`幀視窗類,以便上述RUNTIME_CLASS機制正常工作。

類`CMDIChildWnd``CFrameWnd`從 繼承其大部分預設實現。 有關這些功能的詳細清單,請參閱[CFrameWnd](../../mfc/reference/cframewnd-class.md)類說明。 該`CMDIChildWnd`類別有以下附加功能:

- 與類結合,`CMultiDocTemplate`同一`CMDIChildWnd`文檔 範本中的多個物件共用同一個功能表,從而節省了 Windows 系統資源。

- 當前活動的 MDI 子視窗功能表完全取代 MDI 框架視窗的選單,目前活動 MDI 子視窗的標題將添加到 MDI 框架視窗的標題中。 有關與 MDI 框架視窗結合實現的 MDI 子視窗函數的進一步示例`CMDIFrameWnd`,請參閱 類說明。

請勿使用C++**刪除**運算元來破壞框架視窗。 請改用 `CWnd::DestroyWindow`。 當`CFrameWnd`視窗`PostNcDestroy`被破壞時,將刪除C++物件。 當使用者關閉畫面視窗時,預設`OnClose`處理程式將呼`DestroyWindow`叫 。

有關 的詳細`CMDIChildWnd`資訊 ,請參閱[框架視窗](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cmdichildwndcmdichildwnd"></a><a name="cmdichildwnd"></a>CMDIChildwnd:CMDIChildwnd

呼叫以建構物件`CMDIChildWnd`。

```
CMDIChildWnd();
```

### <a name="remarks"></a>備註

呼叫`Create`以建立可見視窗。

### <a name="example"></a>範例

  請參考[CMDIChildWnd 的範例::建立](#create)。

## <a name="cmdichildwndcreate"></a><a name="create"></a>CMDIChildwnd:創建

調用此成員函數以創建 Windows MDI 子視窗並將`CMDIChildWnd`其附加到 物件。

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_OVERLAPPEDWINDOW,
    const RECT& rect = rectDefault,
    CMDIFrameWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>參數

*lpszClass 名稱*<br/>
指向命名 Windows 類[(WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)結構)的 null 連接端接字串。 類名稱可以是註冊為[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全域函數的任何名稱。 標準 應`CMDIChildWnd`為 NULL。

*lpsz 視窗名稱*<br/>
指向表示視窗名稱的 null 連接字串。 用作標題列的文字。

*dwStyle*<br/>
指定視窗[樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)屬性。 WS_CHILD樣式是必需的。

*矩形*<br/>
包含視窗的大小和位置。 該`rectDefault`值允許 Windows`CMDIChildWnd`指定新的大小和位置。

*pparentwnd*<br/>
指定視窗的父級。 如果為 NULL,則使用主應用程式視窗。

*pContext*<br/>
指定[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)結構。 此參數可以是 NULL。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

當前處於活動狀態的 MDI 子框架視窗可以確定父框架視窗的標題。 此功能通過關閉子框架視窗的FWS_ADDTOTITLE樣式位而禁用。

框架呼叫此成員函數以回應使用者指令以建立子視窗,並且框架使用*pContext*參數將子視窗正確連接到應用程式。 呼叫`Create`時 *,pContext*可以為 NULL。

### <a name="example"></a>範例

範例 1：

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>範例

範例 2：

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

## <a name="cmdichildwndgetmdiframe"></a><a name="getmdiframe"></a>CMDIChildwnd::GetMDIFrame

調用此函數以返回 MDI 父幀。

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>傳回值

指向 MDI 父框架視窗的指標。

### <a name="remarks"></a>備註

返回的幀是從 中刪除的兩`CMDIChildWnd`個 父級,是管理物件的 MDICLIENT`CMDIChildWnd`類型視窗的 父級。 調用[GetParent](../../mfc/reference/cwnd-class.md#getparent)成員函`CMDIChildWnd`數以返回物件的直接 MDICLIENT`CWnd`父級作為臨時指標。

### <a name="example"></a>範例

  請參閱[CMDIFrameWnd 的範例::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu)。

## <a name="cmdichildwndmdiactivate"></a><a name="mdiactivate"></a>CMDIChildwnd:MDIActivate

調用此成員函數以獨立於 MDI 框架視窗啟動 MDI 子視窗。

```cpp
void MDIActivate();
```

### <a name="remarks"></a>備註

當幀變為活動狀態時,上次啟動的子視窗也將啟動。

### <a name="example"></a>範例

  請參考[CMDIFrameWnd 的範例:抓取視窗選單彈出](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup)。

## <a name="cmdichildwndmdidestroy"></a><a name="mdidestroy"></a>CMDIChildwnd:MDI銷毀

調用此成員函數以銷毀 MDI 子視窗。

```cpp
void MDIDestroy();
```

### <a name="remarks"></a>備註

成員函數從框架視窗中刪除子視窗的標題,並停用子視窗。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

## <a name="cmdichildwndmdimaximize"></a><a name="mdimaximize"></a>CMDIChildwnd::MDI最大化

調用此成員函數以最大化 MDI 子視窗。

```cpp
void MDIMaximize();
```

### <a name="remarks"></a>備註

最大化子視窗時,Windows 會調整其大小,使其工作區填充框架視窗的工作區。 Windows 將子視窗的「控制件」功能表放在框架的選單欄中,以便使用者可以還原或關閉子視窗,並將子視窗的標題添加到框架視窗標題中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

## <a name="cmdichildwndmdirestore"></a><a name="mdirestore"></a>CMDIChildwnd::MDI恢復

調用此成員函數以從最大大小或最小化大小還原 MDI 子視窗。

```cpp
void MDIRestore();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

## <a name="cmdichildwndsethandles"></a><a name="sethandles"></a>CMDIChildwnd::設置手柄

設置功能表和快捷鍵資源的句柄。

```cpp
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>參數

*hMenu*<br/>
功能表資源的句柄。

*哈克爾*<br/>
加速器資源的句柄。

### <a name="remarks"></a>備註

調用此函數以設置 MDI 子視窗物件使用的功能表和快速鍵資源。

## <a name="see-also"></a>另請參閱

[MFC 樣品 MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd 類別](../../mfc/reference/cmdiframewnd-class.md)
