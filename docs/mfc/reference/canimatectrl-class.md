---
title: CAnimateCtrl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimateCtrl
- AFXCMN/CAnimateCtrl
- AFXCMN/CAnimateCtrl::CAnimateCtrl
- AFXCMN/CAnimateCtrl::Close
- AFXCMN/CAnimateCtrl::Create
- AFXCMN/CAnimateCtrl::CreateEx
- AFXCMN/CAnimateCtrl::IsPlaying
- AFXCMN/CAnimateCtrl::Open
- AFXCMN/CAnimateCtrl::Play
- AFXCMN/CAnimateCtrl::Seek
- AFXCMN/CAnimateCtrl::Stop
dev_langs:
- C++
helpviewer_keywords:
- CAnimateCtrl [MFC], CAnimateCtrl
- CAnimateCtrl [MFC], Close
- CAnimateCtrl [MFC], Create
- CAnimateCtrl [MFC], CreateEx
- CAnimateCtrl [MFC], IsPlaying
- CAnimateCtrl [MFC], Open
- CAnimateCtrl [MFC], Play
- CAnimateCtrl [MFC], Seek
- CAnimateCtrl [MFC], Stop
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48c431ecbcc415776ff9accfb68004c7c8e46d34
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952322"
---
# <a name="canimatectrl-class"></a>CAnimateCtrl 類別
提供 Windows 通用動畫控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CAnimateCtrl : public CWnd  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimateCtrl::CAnimateCtrl](#canimatectrl)|建構 `CAnimateCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimateCtrl::Close](#close)|關閉 AVI 短片。|  
|[CAnimateCtrl::Create](#create)|建立動畫控制項，並將它附加至`CAnimateCtrl`物件。|  
|[CAnimateCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式建立動畫控制項，並將它附加至`CAnimateCtrl`物件。|  
|[CAnimateCtrl::IsPlaying](#isplaying)|指出是否要播放的音訊視訊交錯格式 (AVI) 剪輯。|  
|[CAnimateCtrl::Open](#open)|AVI 短片從開啟的檔案或資源，並且會顯示第一個框架。|  
|[CAnimateCtrl::Play](#play)|播放 AVI 短片，沒有聲音。|  
|[CAnimateCtrl::Seek](#seek)|顯示選取的單一畫面格的 AVI 短片。|  
|[CAnimateCtrl::Stop](#stop)|停止播放 AVI 短片。|  
  
## <a name="remarks"></a>備註  
 這個控制項 (因此`CAnimateCtrl`類別) 僅適用於 Windows 95、 Windows 98 和 Windows NT 的版本 3.51 下執行的程式和更新版本。  
  
 動畫控制項是矩形的視窗顯示 AVI （音訊視訊交錯格式） 格式的剪輯，標準的 Windows 視訊與音訊格式。 AVI 短片是一系列的點陣圖框架，例如電影。  
  
 動畫控制項可以播放只有簡單的 AVI 短片。 具體而言，無法播放動畫控制項項目必須符合下列需求：  
  
-   必須有正好一個視訊串流，且必須具有至少一個框架。  
  
-   有最多可達兩個資料流檔案中 （通常在其他資料流，如果有的話，是音訊串流，雖然動畫控制項會忽略音訊資訊）。  
  
-   剪輯必須為未壓縮或壓縮 RLE8 壓縮。  
  
-   不允許任何調色盤變更視訊資料流中。  
  
 您可以將 AVI 短片加入您的應用程式做為 AVI 資源，或其可隨附於您的應用程式做為個別的 AVI 檔案。  
  
 因為您的執行緒會繼續執行，同時會顯示在播放 AVI 短片，動畫控制項的常見用法之一是在長時間作業期間表示系統活動。 例如，檔案總管 的 尋找 對話方塊會顯示移動的放大鏡隨著系統搜尋檔案。  
  
 如果您建立`CAnimateCtrl`物件 對話方塊中，方塊中，或從使用對話方塊編輯器對話方塊資源，也會在自動終結當使用者關閉對話方塊。  
  
 如果您建立`CAnimateCtrl`物件內的視窗中，您可能要終結。 如果您建立`CAnimateCtrl`物件在堆疊上，會自動終結。 如果您建立`CAnimateCtrl`使用堆積上的物件**新**函式，您必須呼叫**刪除**終結該物件上。 如果您衍生新類別從`CAnimateCtrl`，會配置任何記憶體，該類別中的覆寫`CAnimateCtrl`解構函式來處置的配置。  
  
 如需有關使用`CAnimateCtrl`，請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CAnimateCtrl](../../mfc/using-canimatectrl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CAnimateCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="canimatectrl"></a>  CAnimateCtrl::CAnimateCtrl  
 建構 `CAnimateCtrl` 物件。  
  
```  
CAnimateCtrl();
```  
  
### <a name="remarks"></a>備註  
 您必須呼叫[建立](#create)成員函式，才能執行您所建立的物件上的任何其他作業。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]  
  
##  <a name="close"></a>  CAnimateCtrl::Close  
 關閉先前動畫控制項 （如果有的話） 中開啟 AVI 短片，並將它從記憶體移除。  
  
```  
BOOL Close();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="example"></a>範例  
  請參閱範例的[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
##  <a name="create"></a>  CAnimateCtrl::Create  
 建立動畫控制項，並將它附加至`CAnimateCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 *dwStyle*  
 指定動畫控制項的樣式。 適用於的 windows 中的 < 備註 > 一節和動畫控制項樣式中所述的樣式所述的任何組合[動畫控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb761886)Windows SDK 中。  
  
 *rect*  
 指定動畫控制項的位置和大小。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](../../mfc/reference/rect-structure1.md)結構。  
  
 *pParentWnd*  
 指定動畫控制項的父視窗，通常`CDialog`。 它不得為**NULL**。  
  
 *nID*  
 指定動畫控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CAnimateCtrl`分成兩個步驟。 首先，呼叫建構函式，然後再呼叫`Create`，建立動畫控制項，並將它附加至`CAnimateCtrl`物件。  
  
 套用下列[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)動畫控制項。  
  
- **WS_CHILD**一律  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
 如果您想要使用動畫控制項的延伸的視窗樣式，呼叫[CreateEx](#createex)而不是`Create`。  
  
 除了上述所列的視窗樣式，您可能想要將一或多個動畫控制項樣式套用至動畫控制項。 請參閱 Windows SDK，如需詳細資訊[動畫控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb761886)。  
  
### <a name="example"></a>範例  
  請參閱範例的[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
##  <a name="createex"></a>  CAnimateCtrl::CreateEx  
 建立控制項 （子視窗），並將它與相關聯`CAnimateCtrl`物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 *dwExStyle*  
 指定正在建立的控制項的延伸的樣式。 如需延伸的視窗樣式的清單，請參閱*dwExStyle*參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) Windows SDK 中。  
  
 *dwStyle*  
 指定動畫控制項的樣式。 套用視窗的任何組合和動畫控制項樣式中所述[動畫控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb761886)Windows SDK 中。  
  
 *rect*  
 若要參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置來建立，用戶端座標中之視窗*pParentWnd*。  
  
 *pParentWnd*  
 為控制項的父視窗的指標。  
  
 *nID*  
 控制項的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而不是[建立](#create)套用延伸的視窗樣式，由 Windows 擴充的樣式序言**WS_EX_**。  
  
##  <a name="isplaying"></a>  CAnimateCtrl::IsPlaying  
 指出是否要播放的音訊視訊交錯格式 (AVI) 剪輯。  
  
```  
BOOL IsPlaying() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `true` 如果正在播放 AVI 短片就;否則， `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[ACM_ISPLAYING](http://msdn.microsoft.com/library/windows/desktop/bb761895) Windows SDK 中所述的訊息。  
  
##  <a name="open"></a>  CAnimateCtrl::Open  
 呼叫此函式可開啟 AVI 短片，並顯示其第一個畫面格。  
  
```  
BOOL Open(LPCTSTR lpszFileName);  
BOOL Open(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 *lpszFileName*  
 A`CString`物件或指標以 null 終止的字串，包含 AVI 檔案的名稱或 AVI 資源的名稱。 如果這個參數是**NULL**，系統會關閉先前針對動畫控制項中，開啟 AVI 短片，如果有的話。  
  
 *nID*  
 AVI 資源識別項。 如果這個參數是**NULL**，系統會關閉先前針對動畫控制項中，開啟 AVI 短片，如果有的話。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="remarks"></a>備註  
 AVI 資源是從建立動畫控制項的模組載入。  
  
 **開啟**不支援音效中 AVI 短片; 您可以開啟僅無訊息的 AVI 短片。  
  
 如果動畫控制項有`ACS_AUTOPLAY`樣式，動畫控制項將會自動啟動它就會開啟之後，立即播放剪輯。 它會繼續在背景播放短片，而您的執行緒會繼續執行。 當完成剪輯播放時，它會自動重複。  
  
 如果動畫控制項有`ACS_CENTER`樣式 AVI 短片會置於控制項和控制項的大小不會變更。 如果動畫控制項沒有`ACS_CENTER`樣式的 AVI 短片中的影像大小開啟 AVI 短片時，將會調整大小的控制項。 控制項的左上角的位置不會變更，控制項的大小。  
  
 如果動畫控制項有`ACS_TRANSPARENT`樣式，第一個框架將會使用透明背景繪製而不是在指定的背景色彩動畫剪輯。  
  
### <a name="example"></a>範例  
  請參閱範例的[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
##  <a name="play"></a>  CAnimateCtrl::Play  
 呼叫此函式可播放 AVI 短片動畫控制項中。  
  
```  
BOOL Play(
    UINT nFrom,  
    UINT nTo,  
    UINT nRep);
```  
  
### <a name="parameters"></a>參數  
 *nFrom*  
 從播放開始畫面格的以零為起始索引。 值必須小於 65536。 值為 0 表示開頭為 AVI 短片中第一個框架。  
  
 *若要*  
 畫面格的以零為起始索引位置播放結束。 值必須小於 65536。 值為-1 表示結尾 AVI 短片中的最後一個畫面格。  
  
 *nRep*  
 若要重新執行 AVI 短片次數。 值為-1 表示無限期地重新執行檔案。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="remarks"></a>備註  
 動畫控制項將會在背景播放短片，而您的執行緒會繼續執行。 如果動畫控制項有`ACS_TRANSPARENT`樣式，在播放 AVI 短片就會播放使用透明背景，而不是動畫剪輯中指定的背景色彩。  
  
### <a name="example"></a>範例  
  請參閱範例的[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
##  <a name="seek"></a>  CAnimateCtrl::Seek  
 呼叫此函數會以靜態方式顯示 AVI 短片單一框架。  
  
```  
BOOL Seek(UINT nTo);
```  
  
### <a name="parameters"></a>參數  
 *若要*  
 要顯示的畫面格的以零為起始的索引。 值必須小於 65536。 值為 0 表示 AVI 短片中顯示第一個框架。 值為-1 表示顯示在播放 AVI 短片中最後一個畫面格。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="remarks"></a>備註  
 如果動畫控制項有`ACS_TRANSPARENT`樣式，將會使用透明背景繪製 AVI 短片而不是在中指定的背景色彩動畫剪輯。  
  
### <a name="example"></a>範例  
  請參閱範例的[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
##  <a name="stop"></a>  CAnimateCtrl::Stop  
 呼叫此函式可停止播放 AVI 短片動畫控制項中。  
  
```  
BOOL Stop();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="example"></a>範例  
  請參閱範例的[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
## <a name="see-also"></a>另請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CAnimateCtrl::Create](#create)   
 [ON_CONTROL](message-map-macros-mfc.md#on_control)

