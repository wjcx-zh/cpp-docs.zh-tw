---
title: "CMiniFrameWnd 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- CMiniFrameWnd class
- mini-frame windows
- toolbars [C++]
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 1229f5405c9eeb90abcdc54108ed26e28d94f0e0
ms.lasthandoff: 02/24/2017

---
# <a name="cminiframewnd-class"></a>CMiniFrameWnd 類別
表示通常在浮動工具列周圍出現的半高度框架視窗。  
  
## <a name="syntax"></a>語法  
  
```  
class CMiniFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMiniFrameWnd::CMiniFrameWnd](#cminiframewnd)|建構 `CMiniFrameWnd` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMiniFrameWnd::Create](#create)|建立`CMiniFrameWnd`建構完成之後的物件。|  
|[CMiniFrameWnd::CreateEx](#createex)|建立`CMiniFrameWnd`建構完成之後的物件 （包括其他選項）。|  
  
## <a name="remarks"></a>備註  
 這些迷你框架視窗的行為類似一般框架視窗，不同之處在於它們沒有最小化/最大化按鈕或功能表，您只需要按一下功能表中的系統關閉它們。  
  
 若要使用`CMiniFrameWnd`物件，請先定義物件。 然後呼叫[建立](#create)成員函式，以顯示迷你框架視窗。  
  
 如需有關如何使用`CMiniFrameWnd`物件，請參閱文章[停駐和浮動工具列](../../mfc/docking-and-floating-toolbars.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMiniFrameWnd`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cminiframewnd"></a>CMiniFrameWnd::CMiniFrameWnd  
 建構`CMiniFrameWnd`物件，但不是會建立視窗。  
  
```  
CMiniFrameWnd();
```  
  
### <a name="remarks"></a>備註  
 若要建立視窗，呼叫[CMiniFrameWnd::Create](#create)。  
  
##  <a name="create"></a>CMiniFrameWnd::Create  
 建立 Windows 迷你框架視窗，並將它附加`CMiniFrameWnd`物件。  
  
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
 `lpClassName`  
 指向以 null 結束的字元字串的名稱的 Windows 類別。 類別名稱可以是任何名稱與全域登錄[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)函式。 如果**NULL**，為您架構註冊視窗類別。 MFC 提供的預設類別，下列的樣式和屬性︰  
  
-   設定樣式位元**CS_DBLCLKS**，會將按兩下訊息至視窗程序當使用者按兩下滑鼠。  
  
-   設定樣式位元**CS_HREDRAW**和**CS_VREDRAW**，其直接重新繪製視窗變更大小的工作區的內容。  
  
-   將類別資料指標設定為 Windows 標準**IDC_ARROW**。  
  
-   若要設定類別的背景筆刷**NULL**，因此，視窗不會清除它的背景。  
  
-   將類別圖示設定為標準的旗標 Windows 標誌圖示。  
  
-   將設定視窗的預設大小和位置，由 Windows 所示。  
  
 `lpWindowName`  
 指向以 null 結束的字元字串，包含視窗名稱。  
  
 `dwStyle`  
 指定的視窗樣式屬性。 這些可以包括標準的視窗樣式和一或多個下列特殊的樣式︰  
  
- **MFS_MOVEFRAME**允許可移動] 視窗中，不只是標題的邊緣上的 [迷你框架視窗。  
  
- **MFS_4THICKFRAME**調整大小的迷你框架視窗會停用。  
  
- **MFS_SYNCACTIVE**同步處理的迷你框架視窗至其父視窗的啟用啟動。  
  
- **MFS_THICKFRAME**允許迷你框架視窗，因為用戶端區域內容允許小調整。  
  
- **MFS_BLOCKSYSMENU**停用存取 [系統] 功能表和 [控制] 功能表中，並將它們轉換成標題 （標題列） 的一部分。  
  
 請參閱[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)如需可能的視窗樣式值的說明。 迷你框架視窗所用的一般組合是**WS_POPUP |WS_CAPTION |WS_SYSMENU**。  
  
 `rect`  
 A`RECT`結構，指定視窗的所需的維度。  
  
 `pParentWnd`  
 父視窗的指標。 使用**NULL**為最上層視窗。  
  
 `nID`  
 如果迷你框架視窗建立做為子視窗，這是識別項的子控制項，否則為 0。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 **建立**初始化視窗的類別名稱與視窗名稱並註冊其樣式和父代的預設值。  
  
##  <a name="createex"></a>CMiniFrameWnd::CreateEx  
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
 `dwExStyle`  
 指定的延伸的樣式`CMiniFrameWnd`所建立。 套用的任何[延伸視窗樣式](../../mfc/reference/extended-window-styles.md)至視窗。  
  
 `lpClassName`  
 指向以 null 結束的字元字串，名稱的 Windows 類別 ( [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)結構)。 類別名稱可以是任何名稱與全域登錄[AfxRegisterWndClass](http://msdn.microsoft.com/library/62c7d4b1-7a29-4abb-86f7-dec541659db0)函式或任何預先定義的控制項類別名稱。 它不得為**NULL**。  
  
 `lpWindowName`  
 指向以 null 結束的字元字串，包含視窗名稱。  
  
 `dwStyle`  
 指定的視窗樣式屬性。 請參閱[視窗樣式](../../mfc/reference/window-styles.md)和[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)的可能值的描述。  
  
 `rect`  
 大小和位置 視窗中，在工作區座標的`pParentWnd`。  
  
 `pParentWnd`  
 父視窗物件的指標。  
  
 `nID`  
 子視窗的識別項。  
  
### <a name="return-value"></a>傳回值  
 成功時，會傳回 TRUE 失敗，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 `CreateEx`參數會指定**WNDCLASS**，視窗樣式 （選擇性） 初始位置和視窗的大小。 `CreateEx`也會指定視窗的父代 （如果有的話） 和 id。  
  
 當`CreateEx`執行時，Windows 會傳送[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)， [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)至視窗的訊息。  
  
 若要擴充的預設訊息處理，衍生自`CMiniFrameWnd`，將訊息對應新增到新的類別，並提供成員函式出現上述訊息。 覆寫`OnCreate`，例如，執行所需的初始化新的類別。  
  
 覆寫進一步**上***訊息*訊息處理常式，以進一步將功能加入至您的衍生類別。  
  
 如果**WS_VISIBLE**樣式，Windows 會傳送視窗啟動，並顯示視窗所需的所有訊息。 如果視窗的樣式會指定的標題列，視窗標題所指`lpszWindowName`參數會顯示在標題列中。  
  
 `dwStyle`參數可以是任意[視窗樣式](../../mfc/reference/window-styles.md)。  
  
 不再支援舊的樣式調色盤工具箱視窗。 在舊版 Windows 中，執行 MFC 應用程式時支援舊的樣式並沒有"X"關閉 按鈕，但已不再支援 Visual c + +.NET 中。 只有新`WS_EX_TOOLWINDOW`樣式現在支援; 這種樣式的說明，請參閱[延伸視窗樣式](../../mfc/reference/extended-window-styles.md)。  
  
## <a name="see-also"></a>另請參閱  
 [CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)

