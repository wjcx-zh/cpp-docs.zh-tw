---
title: "CMFCRibbonCheckBox 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonCheckBox
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCheckBox class
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
caps.latest.revision: 30
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
ms.openlocfilehash: 9efe04a8e79835b8e51b7045cb86ab2dba68b675
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribboncheckbox-class"></a>CMFCRibbonCheckBox 類別
`CMFCRibbonCheckBox` 類別實作可以加入至功能區面板、快速存取工具列或快顯功能表的核取方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonCheckBox : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(覆寫[CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)。)|  
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(覆寫[CMFCRibbonButton::GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize)。)|  
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(覆寫[CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)。)|  
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(覆寫 `CMFCRibbonButton::IsDrawTooltipImage`。)|  
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(覆寫[CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)。)|  
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(覆寫[CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)。)|  
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(覆寫 `CMFCRibbonButton::OnDrawOnList`。)|  
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(覆寫[CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata)。)|  
  
## <a name="remarks"></a>備註  
 若要在應用程式中使用 `CMFCRibbonCheckBox`，請將下列建構函式加入至您的程式碼：  
  
```  
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)  
```  
其中，`nID` 是核取方塊的命令識別碼，`lpszText` 則是核取方塊的文字標籤。  
  
 您也可以使用功能區面板加入核取方塊[CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxribboncheckbox.h  
  
##  <a name="a-namecmfcribboncheckboxa--cmfcribboncheckboxcmfcribboncheckbox"></a><a name="cmfcribboncheckbox"></a>CMFCRibbonCheckBox::CMFCRibbonCheckBox  
 功能區核取方塊物件的建構函式  
  
```  
CMFCRibbonCheckBox(
    UINT nID,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 指定命令識別碼。  
  
 [in] `lpszText`  
 指定文字標籤。  
  
### <a name="return-value"></a>傳回值  
 建構物件功能區核取方塊。  
  
### <a name="example"></a>範例  
 下列範例示範如何建構的物件`CMFCRibbonCheckBox`類別。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&17;](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]  
  
##  <a name="a-namegetcompactsizea--cmfcribboncheckboxgetcompactsize"></a><a name="getcompactsize"></a>CMFCRibbonCheckBox::GetCompactSize  
 覆寫時，取得核取方塊的壓縮大小。  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 指標`CDC`核取方塊相關聯。  
  
### <a name="return-value"></a>傳回值  
 傳回`CSize`物件，其中包含核取方塊的壓縮大小。  
  
### <a name="remarks"></a>備註  
 如果未覆寫，會傳回中繼核取方塊的大小。  
  
##  <a name="a-namegetintermediatesizea--cmfcribboncheckboxgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonCheckBox::GetIntermediateSize  
 取得中繼核取方塊的大小。  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 指標`CDC`這個核取方塊相關聯。  
  
### <a name="return-value"></a>傳回值  
 A`CSize`物件，其中包含中繼核取方塊的大小。  
  
### <a name="remarks"></a>備註  
 如果未覆寫，會計算中繼大小做為預設值 核取方塊大小 ( `AFX_CHECK_BOX_DEFAULT_SIZE`) 再加上文字的大小，再加上邊界。  
  
##  <a name="a-namegetregularsizea--cmfcribboncheckboxgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonCheckBox::GetRegularSize  
 取得規則的核取方塊大小。  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 指標`CDC`這個核取方塊相關聯的物件。  
  
### <a name="return-value"></a>傳回值  
 傳回`CSize`物件，其中包含規則的核取方塊大小。  
  
### <a name="remarks"></a>備註  
 如果未覆寫，會傳回中繼核取方塊的大小。  
  
##  <a name="a-nameisdrawtooltipimagea--cmfcribboncheckboxisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a>CMFCRibbonCheckBox::IsDrawTooltipImage  
 指出是否有核取方塊相關聯的工具提示映像。  
  
```  
virtual BOOL IsDrawTooltipImage() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果沒有核取方塊，與相關聯的工具提示映像或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondrawa--cmfcribboncheckboxondraw"></a><a name="ondraw"></a>CMFCRibbonCheckBox::OnDraw  
 繪製使用指定的裝置內容的核取方塊架構所呼叫。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 指標`CDC`要在其中繪製核取方塊。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondrawmenuimagea--cmfcribboncheckboxondrawmenuimage"></a><a name="ondrawmenuimage"></a>CMFCRibbonCheckBox::OnDrawMenuImage  
 繪製功能表 核取方塊的影像架構呼叫。  
  
```  
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```  
  
### <a name="parameters"></a>參數  
 [in] `CDC*`  
 指標`CDC`核取方塊相關聯。  
  
 [in] `CRect`  
 A`CRect`物件，指定要在其中繪製的功能表影像的矩形。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`所繪製影像，如果或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
 如果未覆寫，就會傳回`FALSE`。  
  
##  <a name="a-nameondrawonlista--cmfcribboncheckboxondrawonlist"></a><a name="ondrawonlist"></a>CMFCRibbonCheckBox::OnDrawOnList  
 若要命令的清單方塊中繪製核取方塊，架構呼叫。  
  
```  
virtual void OnDrawOnList(
    CDC* pDC,  
    CString strText,  
    int nTextOffset,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 要在其中繪製核取方塊的裝置內容的指標。  
  
 [in] `strText`  
 顯示文字。  
  
 [in] `nTextOffset`  
 距離，單位為像素，從左側的清單方塊的顯示文字。  
  
 [in] `rect`  
 核取方塊，顯示矩形。  
  
 [in] `bIsSelected`  
 `TRUE`如果選取此核取方塊，或`FALSE`如果不是。  
  
 [in] `bHighlighted`  
 `TRUE`如果核取方塊，會反白顯示，或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetaccdataa--cmfcribboncheckboxsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonCheckBox::SetACCData  
 設定協助工具的資料 核取方塊。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>參數  
 `pParent`  
 核取方塊的父視窗。  
  
 `data`  
 核取方塊，協助工具的資料。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 `TRUE`。  
  
### <a name="remarks"></a>備註  
 依預設此方法會設定協助工具資料的核取方塊，而且一定傳回`TRUE`。 覆寫此方法以設定協助工具資料並傳回值，以指出成功或失敗。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonPanel 類別](../../mfc/reference/cmfcribbonpanel-class.md)

