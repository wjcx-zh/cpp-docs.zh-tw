---
title: "CSpinButtonCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::Create
- AFXCMN/CSpinButtonCtrl::CreateEx
- AFXCMN/CSpinButtonCtrl::GetAccel
- AFXCMN/CSpinButtonCtrl::GetBase
- AFXCMN/CSpinButtonCtrl::GetBuddy
- AFXCMN/CSpinButtonCtrl::GetPos
- AFXCMN/CSpinButtonCtrl::GetRange
- AFXCMN/CSpinButtonCtrl::SetAccel
- AFXCMN/CSpinButtonCtrl::SetBase
- AFXCMN/CSpinButtonCtrl::SetBuddy
- AFXCMN/CSpinButtonCtrl::SetPos
- AFXCMN/CSpinButtonCtrl::SetRange
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [C++], CSpinButtonCtrl
- CSpinButtonCtrl class
- CSpinButtonCtrl class, common controls
- up-down controls, spin button control
- spin button control
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
caps.latest.revision: 23
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 91be67ccbf1fb7fb863aa4072d55bb3f330aa44f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="cspinbuttonctrl-class"></a>CSpinButtonCtrl 類別
提供 Windows 通用微調按鈕控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CSpinButtonCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|建構 `CSpinButtonCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSpinButtonCtrl::Create](#create)|建立微調按鈕控制項，並將它附加至`CSpinButtonCtrl`物件。|  
|[CSpinButtonCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式建立微調按鈕控制項，並將它附加至`CSpinButtonCtrl`物件。|  
|[CSpinButtonCtrl::GetAccel](#getaccel)|擷取加速微調按鈕控制項的資訊。|  
|[CSpinButtonCtrl::GetBase](#getbase)|擷取目前微調按鈕控制項的基底。|  
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|擷取目前的協同視窗的指標。|  
|[CSpinButtonCtrl::GetPos](#getpos)|擷取目前的微調按鈕控制項的位置。|  
|[CSpinButtonCtrl::GetRange](#getrange)|擷取的上限和下限限制 （範圍） 微調按鈕控制項。|  
|[CSpinButtonCtrl::SetAccel](#setaccel)|設定之微調按鈕控制項加速。|  
|[CSpinButtonCtrl::SetBase](#setbase)|設定微調按鈕控制項的基底。|  
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|設定微調按鈕控制項的協同視窗。|  
|[CSpinButtonCtrl::SetPos](#setpos)|設定控制項的目前位置。|  
|[Cspinbuttonctrl:: Setrange](#setrange)|設定的上限和下限限制 （範圍） 微調按鈕控制項。|  
  
## <a name="remarks"></a>備註  
 「 微調按鈕控制項 」 （也稱為上下按鈕控制項） 是一對箭號按鈕，讓使用者可以按一下要遞增或遞減值，例如捲動位置或附屬控制項中顯示的數字。 微調按鈕控制項相關聯的值稱為其目前位置。 微調按鈕控制項最常搭配附屬控制項稱為 「 協同視窗 」。  
  
 這個控制項 (因此`CSpinButtonCtrl`類別) 僅適用於 Windows 95/98、 Windows NT 的版本 3.51 下執行的程式和更新版本。  
  
 給使用者，微調按鈕控制項和協同視窗通常看起來像單一的控制項。 您可以指定的微調按鈕控制項定位本身其協同視窗旁邊，以及它會自動以其目前位置設定協同視窗的標題。 您可以使用微調按鈕控制項的編輯控制項來提示使用者輸入數字輸入。  
  
 按一下向上箭頭移往最大值，目前的位置並移動朝最小值的目前位置，按一下向下箭號。 根據預設，最小值是 100，最大值是 0。 最小設定是超過最大值設定 （例如，使用預設設定） 時，按一下向上箭號會減少任何時間的位置值，然後按一下向下箭號會遞增。  
  
 微調按鈕控制項而協同視窗不可以當做一種簡化的捲軸。 例如，索引標籤控制項有時會顯示要讓使用者捲動額外的索引標籤來檢視微調按鈕控制項。  
  
 如需有關使用`CSpinButtonCtrl`，請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSpinButtonCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="create"></a>CSpinButtonCtrl::Create  
 建立微調按鈕控制項，並將它附加至`CSpinButtonCtrl`物件...  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定微調按鈕控制項的樣式。 套用至控制項的任何微調按鈕控制項樣式的組合。 這些樣式中所述[上下按鈕控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb759885)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 指定微調按鈕控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構  
  
 `pParentWnd`  
 微調按鈕控制項的父視窗，通常是指向`CDialog`。 它不得為**NULL。**  
  
 `nID`  
 指定微調按鈕控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果初始化成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 您建構`CSpinButtonCtrl`先物件在兩個步驟中，呼叫建構函式，，然後呼叫**建立**，建立微調按鈕控制項，並將它附加至`CSpinButtonCtrl`物件。  
  
 若要使用延伸的視窗樣式建立微調按鈕控制項，呼叫[CSpinButtonCtrl::CreateEx](#createex)而不是**建立**。  
  
##  <a name="createex"></a>CSpinButtonCtrl::CreateEx  
 建立控制項 （子視窗），並將它與相關聯`CSpinButtonCtrl`物件。  
  
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
 指定正在建立的控制項的延伸的樣式。 如需延伸的視窗樣式的清單，請參閱`dwExStyle`參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定微調按鈕控制項的樣式。 套用至控制項的任何微調按鈕控制項樣式的組合。 這些樣式中所述[上下按鈕控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb759885)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 若要參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置來建立，用戶端座標中之視窗`pParentWnd`。  
  
 `pParentWnd`  
 為控制項的父視窗的指標。  
  
 `nID`  
 控制項的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而不是[建立](#create)套用延伸的視窗樣式，由 Windows 擴充的樣式序言**WS_EX_**。  
  
##  <a name="cspinbuttonctrl"></a>CSpinButtonCtrl::CSpinButtonCtrl  
 建構 `CSpinButtonCtrl` 物件。  
  
```  
CSpinButtonCtrl();
```  
  
##  <a name="getaccel"></a>CSpinButtonCtrl::GetAccel  
 擷取加速微調按鈕控制項的資訊。  
  
```  
UINT GetAccel(
    int nAccel,  
    UDACCEL* pAccel) const;  
```  
  
### <a name="parameters"></a>參數  
 `nAccel`  
 中所指定之陣列的項目數`pAccel`。  
  
 `pAccel`  
 陣列的指標[UDACCEL](http://msdn.microsoft.com/library/windows/desktop/bb759897)接收加速資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 擷取對應的結構數目。  
  
##  <a name="getbase"></a>CSpinButtonCtrl::GetBase  
 擷取目前微調按鈕控制項的基底。  
  
```  
UINT GetBase() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的基底值。  
  
##  <a name="getbuddy"></a>CSpinButtonCtrl::GetBuddy  
 擷取目前的協同視窗的指標。  
  
```  
CWnd* GetBuddy() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的協同視窗的指標。  
  
##  <a name="getpos"></a>CSpinButtonCtrl::GetPos  
 擷取目前的微調按鈕控制項的位置。  
  
```  
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 *lpbError*  
 已成功擷取或非零發生錯誤時設定為零如果值為布林值的指標。 如果此參數設為**NULL**，不會報告錯誤。  
  
### <a name="return-value"></a>傳回值  
 第一個版本會傳回 16 位元低序位字組中的目前位置。 高序位文字不是零，如果發生錯誤。  
  
 第二個版本會傳回 32 位元位置。  
  
### <a name="remarks"></a>備註  
 當它處理傳回的值時，控制項就會更新其目前的位置根據協同視窗的標題。 如果沒有協同視窗，或標題指定無效或超出範圍的值，控制權會傳回錯誤。  
  
##  <a name="getrange"></a>CSpinButtonCtrl::GetRange  
 擷取的上限和下限限制 （範圍） 微調按鈕控制項。  
  
```  
DWORD GetRange() const;  
  
void GetRange(
    int& lower,  
    int& upper) const;  
  
void GetRange32(
    int& lower,  
    int &upper) const;  
```  
  
### <a name="parameters"></a>參數  
 *較低*  
 整數，接收控制項的較低限制的參考。  
  
 *上限*  
 接收控制項的最高上限的整數的參考。  
  
### <a name="return-value"></a>傳回值  
 第一個版本會傳回 32 位元值，包含上限和下限。 低序位字組的控制項，上限，而高序位文字較低的限制。  
  
### <a name="remarks"></a>備註  
 成員函式`GetRange32`擷取微調按鈕控制項的範圍為 32 位元整數。  
  
##  <a name="setaccel"></a>CSpinButtonCtrl::SetAccel  
 設定之微調按鈕控制項加速。  
  
```  
BOOL SetAccel(
    int nAccel,  
    UDACCEL* pAccel);
```  
  
### <a name="parameters"></a>參數  
 `nAccel`  
 數目[UDACCEL](http://msdn.microsoft.com/library/windows/desktop/bb759897)所指定的結構`pAccel`。  
  
 `pAccel`  
 陣列的指標`UDACCEL`結構，其中包含加速資訊。 應該排序項目以遞增順序依據**nSec**成員。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
##  <a name="setbase"></a>CSpinButtonCtrl::SetBase  
 設定微調按鈕控制項的基底。  
  
```  
int SetBase(int nBase);
```  
  
### <a name="parameters"></a>參數  
 `nBase`  
 新控制項的基底值。 它可以是十進位的 10 或 16 個十六進位。  
  
### <a name="return-value"></a>傳回值  
 先前的基底值，如果成功，則為零，如果指定的 base 無效。  
  
### <a name="remarks"></a>備註  
 基底值會決定是否協同視窗會顯示十進位或十六進位數字的數字。 十六進位數字都不帶正負號。十進位數字會進行簽署。  
  
##  <a name="setbuddy"></a>CSpinButtonCtrl::SetBuddy  
 設定微調按鈕控制項的協同視窗。  
  
```  
CWnd* SetBuddy(CWnd* pWndBuddy);
```  
  
### <a name="parameters"></a>參數  
 `pWndBuddy`  
 新的協同視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 先前的協同視窗的指標。  
  
### <a name="remarks"></a>備註  
 微調控制項幾乎都是與另一個視窗中，例如編輯控制項，可顯示某些內容相關聯。 其他視窗稱為微調控制項的 「 夥伴 」。  
  
##  <a name="setpos"></a>CSpinButtonCtrl::SetPos  
 設定微調按鈕控制項的目前位置。  
  
```  
int SetPos(int nPos);  
int SetPos32(int nPos);
```  
  
### <a name="parameters"></a>參數  
 `nPos`  
 控制項的新位置。 此值必須是控制項的上限和下限所指定的範圍中。  
  
### <a name="return-value"></a>傳回值  
 前一個位置 (16 位元的有效位數`SetPos`32 位元的有效位數`SetPos32`)。  
  
### <a name="remarks"></a>備註  
 `SetPos32`設定 32 位元位置。  
  
##  <a name="setrange"></a>Cspinbuttonctrl:: Setrange  
 設定的上限和下限限制 （範圍） 微調按鈕控制項。  
  
```  
void SetRange(
    short nLower,  
    short nUpper);

 
void SetRange32(
    int nLower,  
    int nUpper);
```  
  
### <a name="parameters"></a>參數  
 `nLower` 和 `nUpper`  
 上限和下限控制項。 如`SetRange`，都沒有限制可能會大於**UD_MAXVAL**或小於**UD_MINVAL**; 此外，不能超過兩個限制之間的差異**UD_MAXVAL**。 `SetRange32`沒有任何限制置於限制;使用任何整數。  
  
### <a name="remarks"></a>備註  
 成員函式`SetRange32`設定微調按鈕控制項的 32 位元範圍。  
  
> [!NOTE]
>  微調按鈕的預設範圍具有最大值為零 (0) 和最小值為 100。 因為最大值小於最小值，按一下向上箭號，將會降低位置並按一下向下箭號會增加它。 使用`CSpinButtonCtrl::SetRange`調整這些值。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CMNCTRL2](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CSliderCtrl 類別](../../mfc/reference/csliderctrl-class.md)

