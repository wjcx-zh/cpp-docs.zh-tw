---
title: "CAnimateCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- animation controls [C++], CAnimateCtrl class
- Windows common controls [C++], CAnimateCtrl class
- CAnimateCtrl class
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
caps.latest.revision: 25
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: cef1d6274d5334804ee028fa296c77faf124a496
ms.lasthandoff: 02/24/2017

---
# <a name="canimatectrl-class"></a>CAnimateCtrl 類別
提供 Windows 通用動畫控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CAnimateCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CAnimateCtrl::CAnimateCtrl](#canimatectrl)|建構 `CAnimateCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAnimateCtrl::Close](#close)|關閉在播放 AVI 短片。|  
|[CAnimateCtrl::Create](#create)|建立動畫控制項並將它附加`CAnimateCtrl`物件。|  
|[CAnimateCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式建立動畫控制項，並附加至該`CAnimateCtrl`物件。|  
|[CAnimateCtrl::IsPlaying](#isplaying)|指出是否要播放音訊視訊交錯格式 (AVI) 剪輯。|  
|[CAnimateCtrl::Open](#open)|開啟檔案或資源的 AVI 短片並顯示第一個框架。|  
|[CAnimateCtrl::Play](#play)|播放音效不在播放 AVI 短片。|  
|[CAnimateCtrl::Seek](#seek)|顯示選取的單一畫面格在播放 AVI 短片。|  
|[CAnimateCtrl::Stop](#stop)|停止播放 AVI 短片。|  
  
## <a name="remarks"></a>備註  
 這個控制項 (並因此`CAnimateCtrl`類別) 僅適用於執行 Windows 95、 Windows 98 和 Windows NT 版本 3.51 下的程式和更新版本。  
  
 動畫控制項是以 AVI （音訊視訊交錯格式） 格式顯示剪輯矩形視窗 — 標準的 Windows 視訊與音訊格式。 AVI 短片是一系列的點陣圖框架，例如電影。  
  
 動畫控制項可以播放只有簡單的 AVI 短片。 具體來說，動畫控制項的播放剪輯必須符合下列需求︰  
  
-   必須有一個視訊串流，而且必須至少一個框架。  
  
-   可以有最多兩個資料流檔案中 （通常是其他資料流，如果存在，則音訊串流，雖然動畫控制項會忽略除了音訊資訊）。  
  
-   美工圖案必須是未壓縮或壓縮 RLE8 壓縮。  
  
-   不允許任何調色盤變更視訊資料流中。  
  
 您可以加入您的應用程式做為 AVI 資源，在播放 AVI 短片，或它可以幫助您完成您的應用程式做為個別的 AVI 檔案。  
  
 因為您的執行緒會繼續執行 AVI 短片的同時，動畫控制項的常見用途之一是長時間作業期間表示系統的活動。 例如，檔案總管 的 尋找 對話方塊會顯示移動的放大鏡，隨著系統搜尋檔案。  
  
 如果您建立`CAnimateCtrl`物件 對話方塊中，方塊中，或從使用對話方塊編輯器對話方塊資源，也會在自動終結當使用者關閉對話方塊。  
  
 如果您建立`CAnimateCtrl`物件在視窗中，您可能必須摧毀它。 如果您建立`CAnimateCtrl`物件在堆疊上，它會自動終結。 如果您建立`CAnimateCtrl`使用堆積上的物件**新**函式，您必須呼叫**刪除**終結該物件上。 如果您衍生新類別從`CAnimateCtrl`、 配置任何記憶體，該類別中的覆寫`CAnimateCtrl`解構函式配置的處置。  
  
 如需有關使用`CAnimateCtrl`，請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CAnimateCtrl](../../mfc/using-canimatectrl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CAnimateCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="canimatectrl"></a>CAnimateCtrl::CAnimateCtrl  
 建構 `CAnimateCtrl` 物件。  
  
```  
CAnimateCtrl();
```  
  
### <a name="remarks"></a>備註  
 您必須呼叫[建立](#create)成員函式，才能執行您所建立的物件上的任何其他作業。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCControlLadenDialog #&56;](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]  
  
##  <a name="close"></a>CAnimateCtrl::Close  
 關閉先前動畫控制項 （如果有的話） 中開啟在播放 AVI 短片，並將它從記憶體移除。  
  
```  
BOOL Close();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例  
  請參閱範例[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
##  <a name="create"></a>CAnimateCtrl::Create  
 建立動畫控制項並將它附加`CAnimateCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定動畫控制項的樣式。 適用於的 windows 下的 < 備註 > 一節和動畫控制項樣式中所述的樣式中所述的任何組合[動畫控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb761886)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 指定動畫控制項的位置和大小。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](../../mfc/reference/rect-structure1.md)結構。  
  
 `pParentWnd`  
 指定動畫控制項的父視窗，通常`CDialog`。 它不得為**NULL。**  
  
 `nID`  
 指定動畫控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 您建構`CAnimateCtrl`兩個步驟。 首先，呼叫建構函式，並接著呼叫**建立**，其建立動畫控制項，並將它附加`CAnimateCtrl`物件。  
  
 適用於下列[視窗樣式](../../mfc/reference/window-styles.md)動畫控制項。  
  
- **WS_CHILD**一律  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
 如果您想要使用動畫控制項的延伸的視窗樣式，呼叫[CreateEx](#createex)而不是**建立**。  
  
 除了上面所列的視窗樣式，您可能想要將一或多個動畫控制項樣式套用至動畫控制項。 請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需有關[動畫控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb761886)。  
  
### <a name="example"></a>範例  
  請參閱範例[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
##  <a name="createex"></a>CAnimateCtrl::CreateEx  
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
 `dwExStyle`  
 指定正在建立的控制項的延伸的樣式。 如需延伸視窗樣式，請參閱`dwExStyle`參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定動畫控制項的樣式。 套用視窗的任意組合，動畫控制項樣式中所述[動畫控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb761886)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置來建立、 用戶端座標中的視窗的`pParentWnd`。  
  
 `pParentWnd`  
 是控制項的父視窗的指標。  
  
 `nID`  
 控制項的子視窗的 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而不是[建立](#create)套用延伸的視窗樣式，指定 Windows 延伸的樣式序言**WS_EX_**。  
  
##  <a name="isplaying"></a>CAnimateCtrl::IsPlaying  
 指出是否要播放音訊視訊交錯格式 (AVI) 剪輯。  
  
```  
BOOL IsPlaying() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `true`如果正在播放 AVI 短片。否則， `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[ACM_ISPLAYING](http://msdn.microsoft.com/library/windows/desktop/bb761895)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="open"></a>CAnimateCtrl::Open  
 呼叫此函式可開啟 AVI 短片，並顯示其第一個框架。  
  
```  
BOOL Open(LPCTSTR lpszFileName);  
BOOL Open(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `lpszFileName`  
 A`CString`物件或 AVI 檔案的名稱或 AVI 資源的名稱含有 null 結尾字串的指標。 如果這個參數是**NULL**，如果有的話，系統會關閉先前開啟動畫控制項，在播放 AVI 短片。  
  
 `nID`  
 AVI 資源識別項。 如果這個參數是**NULL**，如果有的話，系統會關閉先前開啟動畫控制項，在播放 AVI 短片。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 AVI 資源是從建立動畫控制項的模組載入。  
  
 **開啟**不支援音效中 AVI 短片，您可以開啟僅無訊息的 AVI 短片。  
  
 如果動畫控制項有`ACS_AUTOPLAY`樣式，動畫控制項將自動開始播放短片，它會開啟後立即。 它會繼續在背景播放短片，而您的執行緒會繼續執行。 完成剪輯播放時，它會自動重複。  
  
 如果動畫控制項有`ACS_CENTER`樣式，在播放 AVI 短片置中在控制項中並不會變更控制項的大小。 如果動畫控制項並沒有`ACS_CENTER`樣式，在播放 AVI 短片的 AVI 短片中的映像大小開啟時控制項將會調整大小。 控制項的左上角的位置不會變更，控制項的大小。  
  
 如果動畫控制項有`ACS_TRANSPARENT`樣式，將會使用透明背景繪製的第一個框架，而非中指定的背景色彩的動畫剪輯。  
  
### <a name="example"></a>範例  
  請參閱範例[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
##  <a name="play"></a>CAnimateCtrl::Play  
 呼叫此函式以動畫控制項在播放 AVI 短片。  
  
```  
BOOL Play(
    UINT nFrom,  
    UINT nTo,  
    UINT nRep);
```  
  
### <a name="parameters"></a>參數  
 `nFrom`  
 框架播放的開始處的以零為起始的索引。 值必須小於 65536。 值為 0 表示開頭為 AVI 短片中的第一個框架。  
  
 `nTo`  
 框架的以零為起始的索引位置播放結束。 值必須小於 65536。 值為-1 表示結尾最後一個畫面格在播放 AVI 短片。  
  
 *nRep*  
 若要重新播放 AVI 短片的次數。 值為-1 表示無限期地重新執行檔案。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 動畫控制項將會在背景播放短片，而您的執行緒會繼續執行。 如果動畫控制項有`ACS_TRANSPARENT`樣式，在播放 AVI 短片，就會播放使用透明背景，而不是動畫剪輯中指定的背景色彩。  
  
### <a name="example"></a>範例  
  請參閱範例[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
##  <a name="seek"></a>CAnimateCtrl::Seek  
 呼叫此函數會以靜態方式顯示 AVI 短片的單一畫面。  
  
```  
BOOL Seek(UINT nTo);
```  
  
### <a name="parameters"></a>參數  
 `nTo`  
 要顯示的框架以零為起始的索引。 值必須小於 65536。 值為 0 表示顯示在播放 AVI 短片中的第一個框架。 –&1; 的值表示會顯示最後一個畫面格在播放 AVI 短片。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 如果動畫控制項有`ACS_TRANSPARENT`樣式，將會使用透明背景繪製在播放 AVI 短片，而非中指定的背景色彩的動畫剪輯。  
  
### <a name="example"></a>範例  
  請參閱範例[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
##  <a name="stop"></a>CAnimateCtrl::Stop  
 呼叫此函式，若要停止播放 AVI 短片動畫控制項中。  
  
```  
BOOL Stop();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例  
  請參閱範例[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
## <a name="see-also"></a>另請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CAnimateCtrl::Create](#create)   
 [ON_CONTROL](http://msdn.microsoft.com/library/2cb7ebdf-296b-4606-b191-3449835003db)


