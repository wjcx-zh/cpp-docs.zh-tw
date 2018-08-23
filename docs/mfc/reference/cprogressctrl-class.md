---
title: CProgressCtrl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CProgressCtrl
- AFXCMN/CProgressCtrl
- AFXCMN/CProgressCtrl::CProgressCtrl
- AFXCMN/CProgressCtrl::Create
- AFXCMN/CProgressCtrl::CreateEx
- AFXCMN/CProgressCtrl::GetBarColor
- AFXCMN/CProgressCtrl::GetBkColor
- AFXCMN/CProgressCtrl::GetPos
- AFXCMN/CProgressCtrl::GetRange
- AFXCMN/CProgressCtrl::GetState
- AFXCMN/CProgressCtrl::GetStep
- AFXCMN/CProgressCtrl::OffsetPos
- AFXCMN/CProgressCtrl::SetBarColor
- AFXCMN/CProgressCtrl::SetBkColor
- AFXCMN/CProgressCtrl::SetMarquee
- AFXCMN/CProgressCtrl::SetPos
- AFXCMN/CProgressCtrl::SetRange
- AFXCMN/CProgressCtrl::SetState
- AFXCMN/CProgressCtrl::SetStep
- AFXCMN/CProgressCtrl::StepIt
dev_langs:
- C++
helpviewer_keywords:
- CProgressCtrl [MFC], CProgressCtrl
- CProgressCtrl [MFC], Create
- CProgressCtrl [MFC], CreateEx
- CProgressCtrl [MFC], GetBarColor
- CProgressCtrl [MFC], GetBkColor
- CProgressCtrl [MFC], GetPos
- CProgressCtrl [MFC], GetRange
- CProgressCtrl [MFC], GetState
- CProgressCtrl [MFC], GetStep
- CProgressCtrl [MFC], OffsetPos
- CProgressCtrl [MFC], SetBarColor
- CProgressCtrl [MFC], SetBkColor
- CProgressCtrl [MFC], SetMarquee
- CProgressCtrl [MFC], SetPos
- CProgressCtrl [MFC], SetRange
- CProgressCtrl [MFC], SetState
- CProgressCtrl [MFC], SetStep
- CProgressCtrl [MFC], StepIt
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93a637c1374e77127a5bf71c6fa736d2857928f1
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2018
ms.locfileid: "42539405"
---
# <a name="cprogressctrl-class"></a>CProgressCtrl 類別
提供 Windows 通用進度列控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CProgressCtrl : public CWnd  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CProgressCtrl::CProgressCtrl](#cprogressctrl)|建構 `CProgressCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Cprogressctrl:: Create](#create)|建立進度列控制項，並將它附加至`CProgressCtrl`物件。|  
|[CProgressCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式中建立進度控制項，並將它附加至`CProgressCtrl`物件。|  
|[CProgressCtrl::GetBarColor](#getbarcolor)|取得目前的進度列控制項的進度指示器列的色彩。|  
|[CProgressCtrl::GetBkColor](#getbkcolor)|取得目前的進度列的背景色彩。|  
|[CProgressCtrl::GetPos](#getpos)|取得進度列目前位置。|  
|[CProgressCtrl::GetRange](#getrange)|取得進度列控制項的範圍的下限和上限限制。|  
|[Cprogressctrl:: Getstate](#getstate)|取得目前的進度列控制項的狀態。|  
|[CProgressCtrl::GetStep](#getstep)|擷取目前的進度列控制項的進度列的步驟遞增。|  
|[CProgressCtrl::OffsetPos](#offsetpos)|進度列控制項的目前位置往前移，藉由指定的遞增，並重新繪製的列，以反映新的位置。|  
|[CProgressCtrl::SetBarColor](#setbarcolor)|設定目前的進度列控制項中的進度指示器列的色彩。|  
|[CProgressCtrl::SetBkColor](#setbkcolor)|設定進度列的背景色彩。|  
|[CProgressCtrl::SetMarquee](#setmarquee)|關閉目前的進度列控制項的開啟或關閉的點線框模式。|  
|[CProgressCtrl::SetPos](#setpos)|設定進度列控制項的目前位置，並重新繪製的列，以反映新的位置。|  
|[CProgressCtrl::SetRange](#setrange)|設定進度列控制項的最小和最大範圍，並重新繪製的列，以反映新的範圍。|  
|[CProgressCtrl::SetState](#setstate)|設定目前進度列控制項的狀態。|  
|[CProgressCtrl::SetStep](#setstep)|指定進度列控制項的步驟遞增。|  
|[CProgressCtrl::StepIt](#stepit)|進度列控制項的目前位置前移步驟遞增值 (請參閱[SetStep](#setstep)) 並重新繪製的列，以反映新的位置。|  
  
## <a name="remarks"></a>備註  
 進度列控制項是一個應用程式可以使用來表示長時間作業進度的視窗。 它包含一個矩形，會逐漸填滿，從左到右，使用系統反白顯示色彩隨著作業的進度。  
  
 進度列控制項具有為範圍，而目前的位置。 範圍表示作業的總持續時間和目前的位置表示應用程式已完成此作業的進度。 視窗程序使用範圍，而且目前的位置來決定的進度列反白顯示色彩填滿百分比。 因為範圍和目前的位置值會表示為帶正負號的整數，目前的位置值的可能範圍是從-2,147,483,648 到 2,147,483,647 （含)。  
  
 如需有關使用`CProgressCtrl`，請參閱 <<c2> [ 控制項](../../mfc/controls-mfc.md)並[使用 CProgressCtrl](../../mfc/using-cprogressctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CProgressCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="cprogressctrl"></a>  CProgressCtrl::CProgressCtrl  
 建構 `CProgressCtrl` 物件。  
  
```  
CProgressCtrl();
```  
  
### <a name="remarks"></a>備註  
 在建構之後`CProgressCtrl`物件，請呼叫`CProgressCtrl::Create`建立進度列控制項。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]  
  
##  <a name="create"></a>  Cprogressctrl:: Create  
 建立進度列控制項，並將它附加至`CProgressCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 *cheaderctrl:: Create*  
 指定進度列控制項的樣式。 套用上列任何組合中的視窗 stylesdescribed [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)在 Windows SDK 中，除了下列進度列控制項的樣式，來控制：  
  
- PBS_VERTICAL 顯示垂直進度資訊，從上至底部。 沒有這個旗標，進度列控制項會顯示水平、 左到右。  
  
- PBS_SMOOTH 顯示逐步，smooth 填寫進度列控制項。 沒有這個旗標，控制項將會使用區塊填滿。  
  
 *rect*  
 指定進度列控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。 由於控制項必須是子視窗，指定的座標是相對於工作區*pParentWnd*。  
  
 *pParentWnd*  
 指定進度列控制項的父視窗，通常`CDialog`。 它必須不是 NULL。  
  
 *nID*  
 指定進度列控制項的識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果`CProgressCtrl`物件是否已成功建立，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 您建構`CProgressCtrl`兩個步驟中的物件。 首先，呼叫建構函式，這會建立`CProgressCtrl`物件，然後再呼叫`Create`，這會建立進度列控制項。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]  
  
##  <a name="createex"></a>  CProgressCtrl::CreateEx  
 建立控制項 （子視窗），並將它與關聯`CProgressCtrl`物件。  
  
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
 指定正在建立之控制項的延伸的樣式。 如需延伸的 Windows 樣式的清單，請參閱 < *dwExStyle*參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) Windows SDK 中。  
  
 *cheaderctrl:: Create*  
 指定進度列控制項的樣式。 套用上列任何組合中所述的視窗樣式[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) Windows SDK 中。  
  
 *rect*  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置，在中建立工作區座標中的視窗*pParentWnd*。  
  
 *pParentWnd*  
 是控制項的父視窗的指標。  
  
 *nID*  
 控制項的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而非[建立](#create)套用延伸的 Windows 樣式，由 Windows 延伸的樣式前置詞**WS_EX_**。  
  
##  <a name="getbarcolor"></a>  CProgressCtrl::GetBarColor  
 取得目前的進度列控制項的進度指示器列的色彩。  
  
```  
COLORREF GetBarColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的進度列的色彩以表示[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值或 CLR_DEFAULT 如果進度指示器的狀態列色彩的預設色彩。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PBM_GETBARCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760826)訊息，Windows SDK 中所述。  
  
##  <a name="getbkcolor"></a>  CProgressCtrl::GetBkColor  
 取得目前的進度列的背景色彩。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的進度列的背景色彩以表示[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PBM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760828)訊息，Windows SDK 中所述。  
  
##  <a name="getpos"></a>  CProgressCtrl::GetPos  
 擷取目前的進度列位置。  
  
```  
int GetPos();
```  
  
### <a name="return-value"></a>傳回值  
 進度列控制項的位置。  
  
### <a name="remarks"></a>備註  
 進度列控制項的位置不在畫面上的實體位置，但而不是介於上限和下限範圍中會指出[SetRange](#setrange)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]  
  
##  <a name="getrange"></a>  CProgressCtrl::GetRange  
 取得目前的下限和上限限制或範圍，進度列控制項。  
  
```  
void GetRange(
    int& nLower,  
    int& nUpper);
```  
  
### <a name="parameters"></a>參數  
 *nLower*  
 接收進度列控制項的下限的整數參考。  
  
 *nUpper*  
 接收進度列控制項的時間上限的整數參考。  
  
### <a name="remarks"></a>備註  
 此函式會將下限和上限限制的值複製到所參考的整數*nLower*並*nUpper*分別。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]  
  
##  <a name="getstate"></a>  Cprogressctrl:: Getstate  
 取得目前的進度列控制項的狀態。  
  
```  
int GetState() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的進度列控制項，也就是下列值之一的狀態：  
  
|值|狀況|  
|-----------|-----------|  
|PBST_NORMAL|進行中|  
|PBST_ERROR|錯誤|  
|PBST_PAUSED|已暫停|  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PBM_GETSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760834)訊息，Windows SDK 中所述。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數 `m_progressCtrl`，用來以程式設計方式存取進度列控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會擷取目前的進度列控制項的狀態。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]  
  
##  <a name="getstep"></a>  CProgressCtrl::GetStep  
 擷取目前的進度列控制項的進度列的步驟遞增。  
  
```  
int GetStep() const;  
```  
  
### <a name="return-value"></a>傳回值  
 進度列的步驟遞增值。  
  
### <a name="remarks"></a>備註  
 步驟增量是所用的數量來呼叫[CProgressCtrl::StepIt](#stepit)增加的進度列目前位置。  
  
 這個方法會傳送[PBM_GETSTEP](http://msdn.microsoft.com/library/windows/desktop/bb760836)訊息，Windows SDK 中所述。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數 `m_progressCtrl`，用來以程式設計方式存取進度列控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會擷取目前的進度列控制項的步驟增量。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]  
  
##  <a name="offsetpos"></a>  CProgressCtrl::OffsetPos  
 進度列控制項的目前位置前移所指定的增量*nPos*並重新繪製的列，以反映新的位置。  
  
```  
int OffsetPos(int nPos);
```  
  
### <a name="parameters"></a>參數  
 *nPos*  
 位置前移的數量。  
  
### <a name="return-value"></a>傳回值  
 進度列控制項先前的位置。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]  
  
##  <a name="setbarcolor"></a>  CProgressCtrl::SetBarColor  
 設定目前的進度列控制項中的進度指示器列的色彩。  
  
```  
COLORREF SetBarColor(COLORREF clrBar);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*clrBar*|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，指定新的進度指示器列的色彩。 指定 CLR_DEFAULT 造成進度列，使用其預設色彩。|  
  
### <a name="return-value"></a>傳回值  

前一個色彩的進度指示器列中，以表示[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值或 CLR_DEFAULT 進度指示器列的色彩是否預設色彩。  
  
### <a name="remarks"></a>備註  

`SetBarColor`方法會設定進度列色彩只有當 Windows Vista[佈景主題](/windows/desktop/Controls/visual-styles-overview)為非作用中。  
  
 這個方法會傳送[PBM_SETBARCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760838)訊息，Windows SDK 中所述。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數 `m_progressCtrl`，用來以程式設計方式存取進度列控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會變更進度列的色彩為紅色、 綠色、 藍色或預設值。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]  
  
##  <a name="setbkcolor"></a>  CProgressCtrl::SetBkColor  
 設定進度列的背景色彩。  
  
```  
COLORREF SetBkColor(COLORREF clrNew);
```  
  
### <a name="parameters"></a>參數  
 *clrNew*  
 COLORREF 值，指定新的背景色彩。 指定要用於進度列的預設背景色彩的 CLR_DEFAULT 值。  
  
### <a name="return-value"></a>傳回值  
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，指出上一個背景色彩或 CLR_DEFAULT 如果的背景色彩的預設色彩。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]  
  
##  <a name="setmarquee"></a>  CProgressCtrl::SetMarquee  
 關閉目前的進度列控制項的開啟或關閉的點線框模式。  
  
```  
BOOL SetMarquee(
    BOOL fMarqueeMode,   
    int nInterval);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*fMarqueeMode*|若為 true，則開啟跑馬燈模式，或若要關閉跑馬燈模式，則為 FALSE。|  
|[in]*n 間隔*|以毫秒為單位的跑馬燈動畫的更新之間的時間。|  
  
### <a name="return-value"></a>傳回值  
 此方法一律會傳回 TRUE。  
  
### <a name="remarks"></a>備註  
 點線框模式已開啟，進度列以動畫顯示和捲動例如當一個登入劇場點線框。  
  
 這個方法會傳送[PBM_SETMARQUEE](http://msdn.microsoft.com/library/windows/desktop/bb760842)訊息，Windows SDK 中所述。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數 `m_progressCtrl`，用來以程式設計方式存取進度列控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會啟動，並停止跑馬燈捲動動畫。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]  
  
##  <a name="setpos"></a>  CProgressCtrl::SetPos  
 設定進度列控制項的目前位置所指定*nPos*並重新繪製的列，以反映新的位置。  
  
```  
int SetPos(int nPos);
```  
  
### <a name="parameters"></a>參數  
 *nPos*  
 進度列控制項的新位置。  
  
### <a name="return-value"></a>傳回值  
 進度列控制項先前的位置。  
  
### <a name="remarks"></a>備註  
 進度列控制項的位置不在畫面上的實體位置，但而不是介於上限和下限範圍中會指出[SetRange](#setrange)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]  
  
##  <a name="setrange"></a>  CProgressCtrl::SetRange  
 設定進度列控制項的範圍的上限和下限，並重新繪製的列，以反映新的範圍。  
  
```  
void SetRange(
    short nLower,  
    short nUpper);

 
void SetRange32(
    int nLower,  
    int nUpper);
```  
  
### <a name="parameters"></a>參數  
 *nLower*  
 指定範圍的下限 （預設值為零）。  
  
 *nUpper*  
 指定範圍的上限 （預設值為 100）。  
  
### <a name="remarks"></a>備註  
 此成員函式`SetRange32`設定進度控制項的 32 位元範圍。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]  
  
##  <a name="setstate"></a>  CProgressCtrl::SetState  
 設定目前進度列控制項的狀態。  
  
```  
int SetState(int iState);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*iState*|要設定的進度列狀態。 使用下列其中一個值：<br /><br /> -PBST_NORMAL-進行中<br />-PBST_ERROR-錯誤<br />-PBST_PAUSED-暫停|  
  
### <a name="return-value"></a>傳回值  
 目前進度列控制項先前的狀態。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PBM_SETSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760850)訊息，Windows SDK 中所述。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數 `m_progressCtrl`，用來以程式設計方式存取進度列控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會將目前進度列控制項的狀態設定為已暫停或進行中。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]  
  
##  <a name="setstep"></a>  CProgressCtrl::SetStep  
 指定進度列控制項的步驟遞增。  
  
```  
int SetStep(int nStep);
```  
  
### <a name="parameters"></a>參數  
 *nStep*  
 新的步驟遞增值。  
  
### <a name="return-value"></a>傳回值  
 先前的步驟遞增值。  
  
### <a name="remarks"></a>備註  
 步驟增量是所用的數量的呼叫`CProgressCtrl::StepIt`增加進度列的目前位置。  
  
 預設步驟增量為 10。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]  
  
##  <a name="stepit"></a>  CProgressCtrl::StepIt  
 進度列控制項的目前位置前移步驟遞增，並重新繪製的列，以反映新的位置。  
  
```  
int StepIt();
```  
  
### <a name="return-value"></a>傳回值  
 進度列控制項先前的位置。  
  
### <a name="remarks"></a>備註  
 設定步驟遞增`CProgressCtrl::SetStep`成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CMNCTRL2](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)


