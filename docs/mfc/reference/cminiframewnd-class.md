---
title: CMiniFrameWnd 類別 |Microsoft 文件
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
ms.openlocfilehash: 766faaa50e4efead96ff72c67aee71fec2386b18
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038577"
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
|[CMiniFrameWnd::Create](#create)|建立`CMiniFrameWnd`完成建構後的物件。|  
|[CMiniFrameWnd::CreateEx](#createex)|建立`CMiniFrameWnd`完成建構後的物件 （使用其他選項）。|  
  
## <a name="remarks"></a>備註  
 這些迷你框架視窗的行為與一般的框架視窗中，不同之處在於它們之間沒有最小化/最大化按鈕或功能表，您只需要按一下 [系統] 功能表，若要關閉它們。  
  
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
 若要建立的視窗，呼叫[CMiniFrameWnd::Create](#create)。  
  
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
 *lpClassName*  
 指向以 null 結束的字元字串，Windows 類別命名。 類別名稱可以是任何名稱登錄與全域[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)函式。 如果**NULL**，將會為您登錄視窗類別，由架構。 MFC 提供的預設類別樣式，下列屬性：  
  
-   設定樣式位元**CS_DBLCLKS**，會將按兩下訊息至視窗程序在使用者按兩下滑鼠時。  
  
-   設定樣式位元**CS_HREDRAW**和**CS_VREDRAW**，其直接重新繪製視窗變更大小的工作區的內容。  
  
-   將類別資料指標設定為 Windows 標準**IDC_ARROW**。  
  
-   若要設定類別的背景筆刷**NULL**，因此視窗不會清除它的背景。  
  
-   將類別圖示設定為標準的旗標 Windows 標誌圖示。  
  
-   設定視窗的預設大小和位置，由 Windows 所示。  
  
 *lpWindowName*  
 指向以 null 結尾字元字串，包含視窗名稱。  
  
 *dwStyle*  
 指定視窗的樣式屬性。 這些可以包括標準的視窗樣式與一個或多個下列特殊的樣式：  
  
- **MFS_MOVEFRAME**可讓任何視窗，而不只是標題的邊緣上的 要移動迷你框架視窗。  
  
- **MFS_4THICKFRAME**停用迷你框架視窗的調整大小。  
  
- **MFS_SYNCACTIVE**同步處理的迷你框架視窗至其父視窗的啟用啟動。  
  
- **MFS_THICKFRAME**小因為用戶端區域內容允許的大小調整迷你框架視窗。  
  
- **MFS_BLOCKSYSMENU**會停用存取 [系統] 功能表和 [控制] 功能表中，並將它們轉換成標題 （標題列） 的一部分。  
  
 請參閱[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)如需可能的視窗樣式值的說明。 典型的迷你框架視窗使用，就是**WS_POPUP&#124;WS_CAPTION&#124;WS_SYSMENU**。  
  
 *rect*  
 A`RECT`結構，指定視窗的所需的維度。  
  
 *pParentWnd*  
 指向父視窗。 使用**NULL**為最上層視窗。  
  
 *nID*  
 如果做為子視窗建立迷你框架視窗時，這是識別項的子控制項，否則便是 0。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 **建立**初始化視窗的類別名稱和視窗名稱，並註冊其樣式和父代的預設值。  
  
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
 *dwExStyle*  
 指定的擴充的樣式`CMiniFrameWnd`所建立。 套用這其中任何[延伸視窗樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)至視窗。  
  
 *lpClassName*  
 指向以 null 結束的字元字串，名稱的 Windows 類別 ( [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)結構)。 類別名稱可以是任何名稱登錄與全域[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)函式或任何預先定義的控制項類別名稱。 它不得為**NULL**。  
  
 *lpWindowName*  
 指向以 null 結尾字元字串，包含視窗名稱。  
  
 *dwStyle*  
 指定視窗的樣式屬性。 請參閱[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)和[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)的可能值的描述。  
  
 *rect*  
 大小和視窗的位置，在用戶端座標*pParentWnd*。  
  
 *pParentWnd*  
 指向父視窗物件。  
  
 *nID*  
 子視窗的識別項。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 `CreateEx`參數會指定**WNDCLASS**，視窗樣式 （選擇性） 初始位置和視窗大小。 `CreateEx` 也會指定視窗的父代 （如果有的話） 和識別碼。  
  
 當`CreateEx`執行時，Windows 會傳送[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)， [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)視窗的訊息。  
  
 若要擴充的預設訊息處理，衍生自`CMiniFrameWnd`、 新增訊息對應到新的類別，並提供成員函式出現上述訊息。 覆寫`OnCreate`，例如，若要執行所需的初始化新的類別。  
  
 覆寫進一步 **上 * * * 訊息*訊息處理常式，以進一步將功能加入至您的衍生類別。  
  
 如果**WS_VISIBLE**樣式，Windows 會將視窗啟動並顯示視窗所需的所有訊息。 如果視窗樣式指定標題列，視窗標題所指*lpszWindowName*參數會顯示在標題列中。  
  
 *DwStyle*參數可以是任何的組合[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。  
  
 不再支援的舊樣式的調色盤 [工具箱] 視窗。 支援舊版的 Windows 上執行 MFC 應用程式時的舊樣式，並沒有"X"按鈕，但已不再支援 Visual c + +.NET 中。 只有新`WS_EX_TOOLWINDOW`樣式現在支援; 如需此樣式的說明，請參閱[延伸視窗樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)。  
  
## <a name="see-also"></a>另請參閱  
 [CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)
