---
title: CMFCCaptionButton 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetHit
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetIconID
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetRect
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetSize
- AFXCAPTIONBUTTON/CMFCCaptionButton::IsMiniFrameButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::Move
- AFXCAPTIONBUTTON/CMFCCaptionButton::OnDraw
- AFXCAPTIONBUTTON/CMFCCaptionButton::SetMiniFrameButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCCaptionButton [MFC], CMFCCaptionButton
- CMFCCaptionButton [MFC], GetHit
- CMFCCaptionButton [MFC], GetIconID
- CMFCCaptionButton [MFC], GetRect
- CMFCCaptionButton [MFC], GetSize
- CMFCCaptionButton [MFC], IsMiniFrameButton
- CMFCCaptionButton [MFC], Move
- CMFCCaptionButton [MFC], OnDraw
- CMFCCaptionButton [MFC], SetMiniFrameButton
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec36bfc82064272e165ea274cd127cc626731643
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cmfccaptionbutton-class"></a>CMFCCaptionButton 類別
`CMFCCaptionButton`類別實作停駐窗格或迷你框架視窗的標題列顯示的按鈕。 Framework 通常會自動建立標題按鈕。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCCaptionButton : public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="constructors"></a>建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|建構 CMFCCaptionButton 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCCaptionButton::GetHit](#gethit)|傳回按鈕所代表的命令。|  
|[CMFCCaptionButton::GetIconID](#geticonid)|傳回與按鈕相關聯的映像識別碼。|  
|[CMFCCaptionButton::GetRect](#getrect)|傳回按鈕所佔據的矩形。|  
|[CMFCCaptionButton::GetSize](#getsize)|傳回按鈕的高度與寬度。|  
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|指出是否要將標題列的高度設定為小型的大小。|  
|[CMFCCaptionButton::Move](#move)|設定按鈕繪製位置和視窗顯示狀態。|  
|[CMFCCaptionButton::OnDraw](#ondraw)|繪製標題按鈕。|  
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|設定迷你標題列的大小。|  
  
## <a name="remarks"></a>備註  
 您也可以衍生自[CPaneFrameWnd 類別](../../mfc/reference/cpaneframewnd-class.md)和使用受保護的方法， `AddButton`、 加入迷你框架視窗標題按鈕。  
  
 CPaneFrameWnd.h 定義兩種類型的標題按鈕的命令識別碼：  
  
- `AFX_CAPTION_BTN_PIN`其中顯示固定按鈕停駐窗格支援自動隱藏模式時。  
  
- `AFX_CAPTION_BTN_CLOSE`用來顯示**關閉**按鈕時，可以關閉或隱藏窗格。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構`CMFCCaptionButton`物件，並設定迷你標題列的大小。  
  
 [!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcaptionbutton.h  
  
##  <a name="cmfccaptionbutton"></a>  CMFCCaptionButton::CMFCCaptionButton  
 建構 `CMFCCaptionButton` 物件。  
  
```  
CMFCCaptionButton();

 
CMFCCaptionButton(
    UINT nHit,  
    BOOL bLeftAlign = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nHit`  
 命令與按鈕相關聯。  
  
 [輸入] `bLeftAlign`  
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
|`HTNOWHERE`|預設值。表示沒有命令。|  
  
### <a name="remarks"></a>備註  
 根據預設，標題按鈕不會與命令相關聯。  
  
 在右或向左對齊標題按鈕。  
  
##  <a name="gethit"></a>  CMFCCaptionButton::GetHit  
 傳回按鈕所代表的命令。  
  
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
|`HTNOWHERE`|預設值。表示沒有命令。|  
  
##  <a name="geticonid"></a>  CMFCCaptionButton::GetIconID  
 傳回與按鈕相關聯的映像識別碼。  
  
```  
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,  
    BOOL bMaximized = FALSE) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bHorz`  
 `TRUE` 左或向右箭號映像識別碼;`FALSE`的向上或向下箭號影像 Id。  
  
 [輸入] `bMaximized`  
 `TRUE` 最大化映像識別碼;`FALSE`最小化映像識別碼。  
  
### <a name="return-value"></a>傳回值  
 映像識別碼。  
  
### <a name="remarks"></a>備註  
 參數會指定最小化的映像識別碼，或最大化標題按鈕。  
  
##  <a name="getrect"></a>  CMFCCaptionButton::GetRect  
 傳回按鈕所佔據的矩形。  
  
```  
virtual CRect GetRect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 表示按鈕的位置的矩形。  
  
### <a name="remarks"></a>備註  
 如果看不到按鈕，傳回的大小為 0。  
  
##  <a name="getsize"></a>  CMFCCaptionButton::GetSize  
 傳回按鈕的高度與寬度。  
  
```  
static CSize GetSize();
```  
  
### <a name="return-value"></a>傳回值  
 按鈕的外部的維度。  
  
### <a name="remarks"></a>備註  
 傳回的大小包含按鈕邊界和邊框。  
  
##  <a name="isminiframebutton"></a>  CMFCCaptionButton::IsMiniFrameButton  
 指出是否要將標題列的高度設定為小型的大小。  
  
```  
BOOL IsMiniFrameButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果標題設定為迷你大小;否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="move"></a>  CMFCCaptionButton::Move  
 設定按鈕繪製位置和視窗顯示狀態。  
  
```  
void Move(
    const CPoint& ptTo,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `ptTo`  
 新位置。  
  
 [輸入] `bHide`  
 是否要顯示的按鈕。  
  
##  <a name="ondraw"></a>  CMFCCaptionButton::OnDraw  
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
 [輸入] `pDC`  
 按鈕的裝置內容的指標。  
  
 [輸入] `bActive`  
 是否要繪製作用中的按鈕影像。  
  
 [輸入] `bHorz`  
 保留供衍生類別中使用。  
  
 [輸入] `bMaximized`  
 是否要繪製最大化的按鈕影像。  
  
 [輸入] `bDisabled`  
 是否要繪製啟用的按鈕影像。  
  
### <a name="remarks"></a>備註  
 `bMaximized`參數會使用最大化 按鈕時，或最小化按鈕。  
  
##  <a name="setminiframebutton"></a>  CMFCCaptionButton::SetMiniFrameButton  
 設定迷你標題列的大小。  
  
```  
void SetMiniFramebutton(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bSet`  
 `TRUE` 迷你標題列的高度;`FALSE`預設標題列的高度。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CPaneFrameWnd 類別](../../mfc/reference/cpaneframewnd-class.md)   
 [CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)
