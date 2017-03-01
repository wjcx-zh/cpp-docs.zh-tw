---
title: "CMFCCaptionButton 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCCaptionButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCCaptionButton class
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
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
ms.openlocfilehash: 9d6342f87622c34b671ad5ea443eb78ffd8c3838
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccaptionbutton-class"></a>CMFCCaptionButton 類別
`CMFCCaptionButton`類別實作停駐窗格或迷你框架視窗的標題列顯示的按鈕。 Framework 通常會自動建立標題按鈕。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCCaptionButton : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="constructors"></a>建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|建構 CMFCCaptionButton 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCCaptionButton::GetHit](#gethit)|傳回代表按鈕的命令。|  
|[CMFCCaptionButton::GetIconID](#geticonid)|傳回與按鈕關聯的影像 ID。|  
|[CMFCCaptionButton::GetRect](#getrect)|傳回按鈕所佔據的矩形。|  
|[CMFCCaptionButton::GetSize](#getsize)|傳回按鈕的高度與寬度。|  
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|指出是否要將標題列的高度設定為迷你大小。|  
|[CMFCCaptionButton::Move](#move)|設定按鈕繪製位置和視窗中顯示狀態。|  
|[CMFCCaptionButton::OnDraw](#ondraw)|繪製標題按鈕。|  
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|設定迷你標題列的大小。|  
  
## <a name="remarks"></a>備註  
 您可以衍生自[CPaneFrameWnd 類別](../../mfc/reference/cpaneframewnd-class.md)，並使用受保護的方法，`AddButton`要加入的迷你框架視窗標題按鈕。  
  
 CPaneFrameWnd.h 會定義兩種類型的標題按鈕的命令識別碼︰  
  
- `AFX_CAPTION_BTN_PIN`其中顯示釘選按鈕停駐窗格支援自動隱藏模式時。  
  
- `AFX_CAPTION_BTN_CLOSE`用來顯示**關閉**按鈕時，可以關閉或隱藏窗格。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構`CMFCCaptionButton`物件，並設定迷你標題列的大小。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&43;](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxcaptionbutton.h  
  
##  <a name="a-namecmfccaptionbuttona--cmfccaptionbuttoncmfccaptionbutton"></a><a name="cmfccaptionbutton"></a>CMFCCaptionButton::CMFCCaptionButton  
 建構 `CMFCCaptionButton` 物件。  
  
```  
CMFCCaptionButton();

 
CMFCCaptionButton(
    UINT nHit,  
    BOOL bLeftAlign = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `nHit`  
 關聯按鈕的命令。  
  
 [in] `bLeftAlign`  
 指定按鈕是否靠左對齊。  
  
 下表列出可能的值為`nHit`參數。  
  
|值|命令|  
|-----------|-------------|  
|`AFX_HTCLOSE`|[關閉] 按鈕。|  
|`HTMINBUTTON`|最小化按鈕。|  
|`HTMAXBUTTON`|最大化 按鈕。|  
|`AFX_HTLEFTBUTTON`|向左箭號按鈕。|  
|`AFX_HTRIGHTBUTTON`|向右箭號按鈕。|  
|`AFX_HTMENU`|向下箭號 功能表按鈕。|  
|`HTNOWHERE`|預設值。不代表任何命令。|  
  
### <a name="remarks"></a>備註  
 根據預設，標題按鈕不會與命令相關聯。  
  
 標題按鈕右邊或左邊對齊。  
  
##  <a name="a-namegethita--cmfccaptionbuttongethit"></a><a name="gethit"></a>CMFCCaptionButton::GetHit  
 傳回代表按鈕的命令。  
  
```  
UINT GetHit() const;  
```  
  
### <a name="return-value"></a>傳回值  
 命令按鈕所表示。  
  
 下表列出可能的傳回值。  
  
|值|命令|  
|-----------|-------------|  
|`AFX_HTCLOSE`|[關閉] 按鈕。|  
|`HTMINBUTTON`|最小化按鈕。|  
|`HTMAXBUTTON`|最大化 按鈕。|  
|`AFX_HTLEFTBUTTON`|向左箭號按鈕。|  
|`AFX_HTRIGHTBUTTON`|向右箭號按鈕。|  
|`AFX_HTMENU`|向下箭號 功能表按鈕。|  
|`HTNOWHERE`|預設值。不代表任何命令。|  
  
##  <a name="a-namegeticonida--cmfccaptionbuttongeticonid"></a><a name="geticonid"></a>CMFCCaptionButton::GetIconID  
 傳回與按鈕關聯的影像 ID。  
  
```  
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,  
    BOOL bMaximized = FALSE) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `bHorz`  
 `TRUE`向左或向右箭號影像 Id。`FALSE`的向上或向下箭號影像 Id。  
  
 [in] `bMaximized`  
 `TRUE`最大化影像 ID。`FALSE`最小化映像識別碼。  
  
### <a name="return-value"></a>傳回值  
 映像的識別碼。  
  
### <a name="remarks"></a>備註  
 參數會指定最小化的映像識別碼，或最大化標題按鈕。  
  
##  <a name="a-namegetrecta--cmfccaptionbuttongetrect"></a><a name="getrect"></a>CMFCCaptionButton::GetRect  
 傳回按鈕所佔據的矩形。  
  
```  
virtual CRect GetRect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 表示按鈕的位置矩形。  
  
### <a name="remarks"></a>備註  
 如果您無法看到此按鈕，傳回的大小為 0。  
  
##  <a name="a-namegetsizea--cmfccaptionbuttongetsize"></a><a name="getsize"></a>CMFCCaptionButton::GetSize  
 傳回按鈕的高度與寬度。  
  
```  
static CSize GetSize();
```  
  
### <a name="return-value"></a>傳回值  
 按鈕的外部的維度。  
  
### <a name="remarks"></a>備註  
 傳回的大小包含按鈕邊界和邊框。  
  
##  <a name="a-nameisminiframebuttona--cmfccaptionbuttonisminiframebutton"></a><a name="isminiframebutton"></a>CMFCCaptionButton::IsMiniFrameButton  
 指出是否要將標題列的高度設定為迷你大小。  
  
```  
BOOL IsMiniFrameButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果標題設為迷你大小;否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namemovea--cmfccaptionbuttonmove"></a><a name="move"></a>CMFCCaptionButton::Move  
 設定按鈕繪製位置和視窗中顯示狀態。  
  
```  
void Move(
    const CPoint& ptTo,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `ptTo`  
 新位置。  
  
 [in] `bHide`  
 是否要顯示的按鈕。  
  
##  <a name="a-nameondrawa--cmfccaptionbuttonondraw"></a><a name="ondraw"></a>CMFCCaptionButton::OnDraw  
 繪製標題按鈕。  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    BOOL bActive,  
    BOOL bHorz = TRUE,  
    BOOL bMaximized = TRUE,  
    BOOL bDisabled = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 按鈕的裝置內容的指標。  
  
 [in] `bActive`  
 是否要畫作用中 按鈕。  
  
 [in] `bHorz`  
 保留供衍生類別中使用。  
  
 [in] `bMaximized`  
 是否要繪製最大化 按鈕的影像。  
  
 [in] `bDisabled`  
 是否要繪製已啟用 按鈕影像。  
  
### <a name="remarks"></a>備註  
 `bMaximized`參數會使用最大化 按鈕時，或最小化按鈕。  
  
##  <a name="a-namesetminiframebuttona--cmfccaptionbuttonsetminiframebutton"></a><a name="setminiframebutton"></a>CMFCCaptionButton::SetMiniFrameButton  
 設定迷你標題列的大小。  
  
```  
void SetMiniFramebutton(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bSet`  
 `TRUE`迷你標題列的高度;`FALSE`的預設標題列的高度。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CPaneFrameWnd 類別](../../mfc/reference/cpaneframewnd-class.md)   
 [CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)

