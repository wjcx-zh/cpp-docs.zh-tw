---
title: "CSpinButtonCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSpinButtonCtrl
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 486a0842ed04f0e760bbb332986a97a35ce9851f
ms.lasthandoff: 02/24/2017

---
# <a name="cspinbuttonctrl-class"></a>CSpinButtonCtrl 類別
提供 Windows 通用微調按鈕控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CSpinButtonCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|建構 `CSpinButtonCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSpinButtonCtrl::Create](#create)|建立使用微調按鈕控制項並將它附加`CSpinButtonCtrl`物件。|  
|[CSpinButtonCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式建立微調按鈕控制項，並附加至該`CSpinButtonCtrl`物件。|  
|[CSpinButtonCtrl::GetAccel](#getaccel)|擷取加速微調按鈕控制項的資訊。|  
|[CSpinButtonCtrl::GetBase](#getbase)|擷取目前的基底的微調按鈕控制項。|  
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|擷取目前的協同視窗的指標。|  
|[CSpinButtonCtrl::GetPos](#getpos)|擷取目前的微調按鈕控制項的位置。|  
|[CSpinButtonCtrl::GetRange](#getrange)|擷取上限和下限 （範圍） 的微調按鈕控制項。|  
|[CSpinButtonCtrl::SetAccel](#setaccel)|設定使用微調按鈕控制項的加速功能。|  
|[CSpinButtonCtrl::SetBase](#setbase)|設定為使用微調按鈕控制項的基底。|  
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|設定為使用微調按鈕控制項協同視窗。|  
|[CSpinButtonCtrl::SetPos](#setpos)|設定控制項的目前位置。|  
|[Cspinbuttonctrl:: Setrange](#setrange)|設定上限和下限 （範圍） 的微調按鈕控制項。|  
  
## <a name="remarks"></a>備註  
 「 微調按鈕控制項 」 （也稱為上下按鈕控制項） 是一對箭號按鈕，使用者可以按一下以遞增或遞減值，例如捲動位置或附屬控制項中顯示的數字。 微調按鈕控制項相關聯的值會呼叫其目前位置。 微調按鈕控制項最常搭配附屬控制項稱為 「 協同視窗 」。  
  
 這個控制項 (並因此`CSpinButtonCtrl`類別) 僅適用於執行 Windows 95/98 和 Windows NT 版本 3.51 下的程式和更新版本。  
  
 給使用者，微調按鈕控制項和協同視窗通常看起來像單一控制項。 您可以指定，微調按鈕控制項自動置於本身及其協同視窗旁邊，而且它會自動為其目前位置設定協同視窗的標題。 您可以使用具有編輯控制項的微調按鈕控制項來提示使用者輸入數字。  
  
 按一下向上箭頭移往最大值，目前的位置，並按一下向下箭號移到最小值的目前位置。 根據預設，最小值是 100，而最大值為 0。 最小的設定值大於最大值設定 （例如，當使用預設設定），按一下向上箭號會減少任何時間的位置值，然後按一下向下箭號會遞增。  
  
 微調按鈕控制項，而不需要協同視窗函式做為一種簡化的捲軸。 例如，索引標籤控制項有時會顯示微調按鈕控制項，讓使用者来捲動進入檢視的其他索引標籤。  
  
 如需有關使用`CSpinButtonCtrl`，請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSpinButtonCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="a-namecreatea--cspinbuttonctrlcreate"></a><a name="create"></a>CSpinButtonCtrl::Create  
 建立使用微調按鈕控制項並將它附加`CSpinButtonCtrl`物件...  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定微調按鈕控制項的樣式。 套用至控制項的任何組合的微調按鈕控制項的樣式。 這些樣式中所述[上下按鈕控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb759885)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 指定微調按鈕控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構  
  
 `pParentWnd`  
 微調按鈕控制項的父視窗，通常是指向`CDialog`。 它不得為**NULL。**  
  
 `nID`  
 指定微調按鈕控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果初始化成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CSpinButtonCtrl`第一次物件在兩個步驟中，呼叫建構函式，然後呼叫**建立**，其建立微調按鈕控制項，並將它附加`CSpinButtonCtrl`物件。  
  
 若要建立延伸的視窗樣式微調按鈕控制項，呼叫[CSpinButtonCtrl::CreateEx](#createex)而不是**建立**。  
  
##  <a name="a-namecreateexa--cspinbuttonctrlcreateex"></a><a name="createex"></a>CSpinButtonCtrl::CreateEx  
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
 指定正在建立的控制項的延伸的樣式。 如需延伸的視窗樣式，請參閱`dwExStyle`參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定微調按鈕控制項的樣式。 套用至控制項的任何組合的微調按鈕控制項的樣式。 這些樣式中所述[上下按鈕控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb759885)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
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
  
##  <a name="a-namecspinbuttonctrla--cspinbuttonctrlcspinbuttonctrl"></a><a name="cspinbuttonctrl"></a>CSpinButtonCtrl::CSpinButtonCtrl  
 建構 `CSpinButtonCtrl` 物件。  
  
```  
CSpinButtonCtrl();
```  
  
##  <a name="a-namegetaccela--cspinbuttonctrlgetaccel"></a><a name="getaccel"></a>CSpinButtonCtrl::GetAccel  
 擷取加速微調按鈕控制項的資訊。  
  
```  
UINT GetAccel(
    int nAccel,  
    UDACCEL* pAccel) const;  
```  
  
### <a name="parameters"></a>參數  
 `nAccel`  
 所指定之陣列中的項目數`pAccel`。  
  
 `pAccel`  
 陣列的指標[UDACCEL](http://msdn.microsoft.com/library/windows/desktop/bb759897)接收加速資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 擷取對應的結構數目。  
  
##  <a name="a-namegetbasea--cspinbuttonctrlgetbase"></a><a name="getbase"></a>CSpinButtonCtrl::GetBase  
 擷取目前的基底的微調按鈕控制項。  
  
```  
UINT GetBase() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的基底值。  
  
##  <a name="a-namegetbuddya--cspinbuttonctrlgetbuddy"></a><a name="getbuddy"></a>CSpinButtonCtrl::GetBuddy  
 擷取目前的協同視窗的指標。  
  
```  
CWnd* GetBuddy() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的協同視窗的指標。  
  
##  <a name="a-namegetposa--cspinbuttonctrlgetpos"></a><a name="getpos"></a>CSpinButtonCtrl::GetPos  
 擷取目前的微調按鈕控制項的位置。  
  
```  
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;  ```  
  
### Parameters  
 *lpbError*  
 A pointer to a boolean value that is set to zero if the value is successfully retrieved or non-zero if an error occurs. If this parameter is set to **NULL**, errors are not reported.  
  
### Return Value  
 The first version returns the 16-bit current position in the low-order word. The high-order word is nonzero if an error occurred.  
  
 The second version returns the 32-bit position.  
  
### Remarks  
 When it processes the value returned, the control updates its current position based on the caption of the buddy window. The control returns an error if there is no buddy window or if the caption specifies an invalid or out-of-range value.  
  
##  <a name="getrange"></a>  CSpinButtonCtrl::GetRange  
 Retrieves the upper and lower limits (range) for a spin button control.  
  
```  
DWORD GetRange() const;  
  
void GetRange (int i 較低，  
    int i 上方) const;  
  
void GetRange32 (int i 較低，  
    int i 上方) const;  
```  
  
### Parameters  
 *lower*  
 Reference to an integer that receives the lower limit for the control.  
  
 *upper*  
 Reference to an integer that receives the upper limit for the control.  
  
### Return Value  
 The first version returns a 32-bit value containing the upper and lower limits. The low-order word is the upper limit for the control, and the high-order word is the lower limit.  
  
### Remarks  
 The member function `GetRange32` retrieves the spin button control's range as a 32-bit integer.  
  
##  <a name="setaccel"></a>  CSpinButtonCtrl::SetAccel  
 Sets the acceleration for a spin button control.  
  
```  
BOOL SetAccel (int nAccel，  
    UDACCEL* pAccel);
```  
  
### Parameters  
 `nAccel`  
 Number of [UDACCEL](http://msdn.microsoft.com/library/windows/desktop/bb759897) structures specified by `pAccel`.  
  
 `pAccel`  
 Pointer to an array of `UDACCEL` structures, which contain acceleration information. Elements should be sorted in ascending order based on the **nSec** member.  
  
### Return Value  
 Nonzero if successful; otherwise 0.  
  
##  <a name="setbase"></a>  CSpinButtonCtrl::SetBase  
 Sets the base for a spin button control.  
  
```  
int SetBase (int nBase);
```  
  
### Parameters  
 `nBase`  
 New base value for the control. It can be 10 for decimal or 16 for hexadecimal.  
  
### Return Value  
 The previous base value if successful, or zero if an invalid base is given.  
  
### Remarks  
 The base value determines whether the buddy window displays numbers in decimal or hexadecimal digits. Hexadecimal numbers are always unsigned; decimal numbers are signed.  
  
##  <a name="setbuddy"></a>  CSpinButtonCtrl::SetBuddy  
 Sets the buddy window for a spin button control.  
  
```  
CWnd* SetBuddy (CWnd* pWndBuddy);
```  
  
### Parameters  
 `pWndBuddy`  
 Pointer to the new buddy window.  
  
### Return Value  
 A pointer to the previous buddy window.  
  
### Remarks  
 A spin control is almost always associated with another window, such as an edit control, that displays some content. This other window is called the "buddy" of the spin control.  
  
##  <a name="setpos"></a>  CSpinButtonCtrl::SetPos  
 Sets the current position for a spin button control.  
  
```  
int SetPos (int nPos);  
int SetPos32(int nPos);
```  
  
### Parameters  
 `nPos`  
 New position for the control. This value must be in the range specified by the upper and lower limits for the control.  
  
### Return Value  
 The previous position (16-bit precision for `SetPos`, 32-bit precision for `SetPos32`).  
  
### Remarks  
 `SetPos32` sets the 32-bit position.  
  
##  <a name="setrange"></a>  CSpinButtonCtrl::SetRange  
 Sets the upper and lower limits (range) for a spin button control.  
  
```  
void SetRange (簡短 nLower，  
    簡短的 nUpper);

 
void SetRange32 (int nLower，  
    int nUpper);
```  
  
### Parameters  
 `nLower`and `nUpper`  
 Upper and lower limits for the control. For `SetRange`, neither limit can be greater than **UD_MAXVAL** or less than **UD_MINVAL**; in addition, the difference between the two limits cannot exceed **UD_MAXVAL**. `SetRange32` places no restrictions on the limits; use any integers.  
  
### Remarks  
 The member function `SetRange32` sets the 32-bit range for the spin button control.  
  
> [!NOTE]
>  The default range for the spin button has the maximum set to zero (0) and the minimum set to 100. Because the maximum value is less than the minimum value, clicking the up arrow will decrease the position and clicking the down arrow will increase it. Use `CSpinButtonCtrl::SetRange` to adjust these values.  
  
## See Also  
 [MFC Sample CMNCTRL2](../../visual-cpp-samples.md)   
 [CWnd Class](../../mfc/reference/cwnd-class.md)   
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [CSliderCtrl Class](../../mfc/reference/csliderctrl-class.md)

