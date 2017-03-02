---
title: "CWinFormsControl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinFormsControl
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- CWinFormsControl class
- Windows Forms [C++], MFC support
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
caps.latest.revision: 28
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
ms.openlocfilehash: 49e24c04deda3df5683908fa9ca485cf7802214b
ms.lasthandoff: 02/24/2017

---
# <a name="cwinformscontrol-class"></a>CWinFormsControl 類別
提供裝載 Windows Form 控制項的基本功能。  
  
## <a name="syntax"></a>語法  
  
```  
template<class TManagedControl>  
class CWinFormsControl : public CWnd  
```  
  
#### <a name="parameters"></a>參數  
 `TManagedControl`  
 .NET Framework Windows Form 控制項在 MFC 應用程式中顯示。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|建構的 MFC Windows Form 控制項的包裝函式物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|建立 Windows Form 控制項在 MFC 容器中。|  
|[CWinFormsControl::GetControl](#getcontrol)|擷取 Windows Form 控制項的指標。|  
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|擷取 Windows Form 控制項的控制代碼。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CWinFormsControl::operator-&gt;](#operator_-_gt)|取代[CWinFormsControl::GetControl](#getcontrol)運算式中。|  
|[CWinFormsControl::operator TManagedControl ^](#operator_tmanagedcontrol)|將型別轉換成 Windows Form 控制項的指標。|  
  
## <a name="remarks"></a>備註  
 `CWinFormsControl`類別會提供裝載 Windows Form 控制項的基本功能。  
  
 如需有關如何使用 Windows Form 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
 您的 MFC 程式碼不應快取視窗控制代碼 (通常會儲存在`m_hWnd`)。 某些 Windows Form 控制項屬性需要基礎 Win32`Window`終結並重新建立使用`DestroyWindow`和`CreateWindow`。 MFC Windows Form 實作控制代碼`Destroy`和`Create`更新控制項的事件`m_hWnd`成員。  
  
> [!NOTE]
>  MFC Windows Form 整合的工作只能在動態連結 （AFXDLL 定義的） 的 mfc 專案中。  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxwinforms.h  
  
##  <a name="a-namecreatemanagedcontrola--cwinformscontrolcreatemanagedcontrol"></a><a name="createmanagedcontrol"></a>CWinFormsControl::CreateManagedControl  
 建立 Windows Form 控制項在 MFC 容器中。  
  
```  
inline BOOL CreateManagedControl(
    System::Type^ pType,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID)  
inline BOOL CreateManagedControl(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID);

 
inline BOOL CreateManagedControl(
    DWORD dwStyle,  
    int nPlaceHolderID,  
    CWnd* pParentWnd);

 
inline BOOL CreateManagedControl(
    typename TManagedControl^ pControl,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID);
```  
  
### <a name="parameters"></a>參數  
 `pType`  
 若要建立控制項的資料型別。 必須是[類型](https://msdn.microsoft.com/en-us/library/system.type)資料型別。  
  
 `dwStyle`  
 要套用至控制項的視窗樣式。 指定組合[視窗樣式](../../mfc/reference/window-styles.md)。 目前支援下列的樣式︰ WS_TABSTOP、 WS_VISIBLE、 WS_DISABLED 和 WS_GROUP。  
  
 `rect`  
 A [RECT 結構](../../mfc/reference/rect-structure1.md)，定義控制項的左上角和右下角的座標 （第一個多載只）。  
  
 `nPlaceHolderID`  
 靜態位置持有者控制項控點放在資源編輯器。 新建立的 Windows Form 控制項取代靜態控制項，並假設其位置、 圖層順序和樣式 （第二個多載只）。  
  
 `pParentWnd`  
 父視窗的指標。  
  
 `nID`  
 要指派給新建立的控制項的資源識別碼編號。  
  
 `pControl`  
 Windows Form 控制項相關聯的執行個體[CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md)物件 （僅第四個多載）。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回非零值。 如果不成功，會傳回零。  
  
### <a name="remarks"></a>備註  
 這個方法會具現化.NET Framework Windows Form 控制項在 MFC 容器中。  
  
 方法的第一個多載接受.NET Framework 資料型別`pType`使 MFC 可以具現化這個型別的新物件。 `pType`必須是[類型](https://msdn.microsoft.com/en-us/library/system.type)資料型別。  
  
 方法的第二個多載會建立 Windows Form 控制項根據`TManagedControl`的範本參數`CWinFormsControl`類別。 大小和控制項的位置根據`RECT`結構傳遞給方法。 只有`dwStyle`關切的樣式。  
  
 方法的第三個多載會建立 Windows Form 控制項，以取代靜態控制項，其終結和假設其位置、 圖層順序和樣式。 靜態控制項只用來做為 Windows Form 控制項的預留位置。 建立控制項時，這個多載結合的樣式從`dwStyle`使用靜態控制項的資源的樣式。  
  
 方法的第四個多載可讓您傳遞已具現化的 Windows Form 控制項中`pControl`，MFC 會自動換行。 它必須是相同型別的`TManagedControl`的範本參數`CWinFormsControl`類別。  
  
 請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)範例使用 Windows Form 控制項。  
  
##  <a name="a-namecwinformscontrola--cwinformscontrolcwinformscontrol"></a><a name="cwinformscontrol"></a>CWinFormsControl::CWinFormsControl  
 建構的 MFC Windows Form 控制項的包裝函式物件。  
  
```  
CWinFormsControl();
```  
  
### <a name="remarks"></a>備註  
 當您呼叫具現化 Windows Form 控制項[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)。  
  
##  <a name="a-namegetcontrola--cwinformscontrolgetcontrol"></a><a name="getcontrol"></a>CWinFormsControl::GetControl  
 擷取 Windows Form 控制項的指標。  
  
```  
inline TManagedControl^ GetControl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 Windows Form 控制項中傳回的指標。  
  
### <a name="example"></a>範例  
  請參閱[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)。  
  
##  <a name="a-namegetcontrolhandlea--cwinformscontrolgetcontrolhandle"></a><a name="getcontrolhandle"></a>CWinFormsControl::GetControlHandle  
 擷取 Windows Form 控制項的控制代碼。  
  
```  
inline HWND GetControlHandle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回在 Windows Form 控制項的控制代碼。  
  
### <a name="remarks"></a>備註  
 `GetControlHandle`是 helper 方法會傳回儲存在.NET Framework 控制項屬性的視窗控制代碼。 視窗控制代碼值複製到[CWnd::m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd)的呼叫期間[CWnd::Attach](../../mfc/reference/cwnd-class.md#attach)。  
  
##  <a name="a-nameoperator-gta--cwinformscontroloperator--gt"></a><a name="operator_-_gt"></a>CWinFormsControl::operator-&gt;  
 取代[CWinFormsControl::GetControl](#getcontrol)運算式中。  
  
```  
inline TManagedControl^  operator->() const;  
```  
  
### <a name="remarks"></a>備註  
 此運算子會提供方便的語法，以取代`GetControl`運算式中。  
  
 如需有關 Windows Form 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
##  <a name="a-nameoperatortmanagedcontrola--cwinformscontroloperator-tmanagedcontrol"></a><a name="operator_tmanagedcontrol"></a>CWinFormsControl::operator TManagedControl ^  
 將型別轉換成 Windows Form 控制項的指標。  
  
```  
inline operator TManagedControl^() const;  
```  
  
### <a name="remarks"></a>備註  
 此運算子傳遞`CWinFormsControl<``TManagedControl``>`接受 Windows Form 控制項的指標的函式。  
  
## <a name="see-also"></a>另請參閱  
 [CWinFormsDialog 類別](../../mfc/reference/cwinformsdialog-class.md)   
 [CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)

