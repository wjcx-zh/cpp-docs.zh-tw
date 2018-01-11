---
title: "CMFCRibbonCheckBox 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetCompactSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetIntermediateSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetRegularSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::IsDrawTooltipImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDraw
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawMenuImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawOnList
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::SetACCData
dev_langs: C++
helpviewer_keywords:
- CMFCRibbonCheckBox [MFC], CMFCRibbonCheckBox
- CMFCRibbonCheckBox [MFC], GetCompactSize
- CMFCRibbonCheckBox [MFC], GetIntermediateSize
- CMFCRibbonCheckBox [MFC], GetRegularSize
- CMFCRibbonCheckBox [MFC], IsDrawTooltipImage
- CMFCRibbonCheckBox [MFC], OnDraw
- CMFCRibbonCheckBox [MFC], OnDrawMenuImage
- CMFCRibbonCheckBox [MFC], OnDrawOnList
- CMFCRibbonCheckBox [MFC], SetACCData
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bc46d934c99e24b63ef314ef1f63402893c6bb18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribboncheckbox-class"></a>CMFCRibbonCheckBox 類別
`CMFCRibbonCheckBox` 類別實作可以加入至功能區面板、快速存取工具列或快顯功能表的核取方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonCheckBox : public CMFCRibbonButton  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(覆寫[cmfcribbonbutton:: Getcompactsize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)。)|  
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(覆寫[cmfcribbonbutton:: Getintermediatesize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize)。)|  
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(覆寫[cmfcribbonbutton:: Getregularsize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)。)|  
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(覆寫 `CMFCRibbonButton::IsDrawTooltipImage`。)|  
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(覆寫[cmfcribbonbutton:: Ondraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)。)|  
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(覆寫[cmfcribbonbaseelement:: Ondrawmenuimage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)。)|  
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(覆寫 `CMFCRibbonButton::OnDrawOnList`。)|  
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(覆寫[cmfcribbonbutton:: Setaccdata](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata)。)|  
  
## <a name="remarks"></a>備註  
 若要在應用程式中使用 `CMFCRibbonCheckBox`，請將下列建構函式加入至您的程式碼：  
  
```  
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)  
```  
其中，`nID` 是核取方塊的命令識別碼，`lpszText` 則是核取方塊的文字標籤。  
  
 您可以將核取方塊加入 功能區面板使用[cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxribboncheckbox.h  
  
##  <a name="cmfcribboncheckbox"></a>CMFCRibbonCheckBox::CMFCRibbonCheckBox  
 功能區核取方塊，物件建構函式  
  
```  
CMFCRibbonCheckBox(
    UINT nID,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nID`  
 指定命令識別碼。  
  
 [輸入] `lpszText`  
 指定文字標籤。  
  
### <a name="return-value"></a>傳回值  
 建構功能區核取方塊物件。  
  
### <a name="example"></a>範例  
 下列範例示範如何建構的物件`CMFCRibbonCheckBox`類別。  
  
 [!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]  
  
##  <a name="getcompactsize"></a>CMFCRibbonCheckBox::GetCompactSize  
 覆寫時，取得核取方塊的壓縮大小。  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 指標`CDC`相關聯的核取方塊。  
  
### <a name="return-value"></a>傳回值  
 傳回`CSize`物件，其中包含核取方塊的壓縮大小。  
  
### <a name="remarks"></a>備註  
 如果未覆寫，會傳回中繼核取方塊的大小。  
  
##  <a name="getintermediatesize"></a>CMFCRibbonCheckBox::GetIntermediateSize  
 取得中繼核取方塊的大小。  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 指標`CDC`此核取方塊相關聯。  
  
### <a name="return-value"></a>傳回值  
 A`CSize`物件，其中包含中繼核取方塊的大小。  
  
### <a name="remarks"></a>備註  
 如果未覆寫，會計算為預設核取方塊大小的中繼大小 ( `AFX_CHECK_BOX_DEFAULT_SIZE`) 再加上文字的大小，再加上邊界。  
  
##  <a name="getregularsize"></a>CMFCRibbonCheckBox::GetRegularSize  
 取得規則的核取方塊大小。  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 指標`CDC`此核取方塊相關聯的物件。  
  
### <a name="return-value"></a>傳回值  
 傳回`CSize`物件，其中包含一般大小的核取方塊。  
  
### <a name="remarks"></a>備註  
 如果未覆寫，會傳回中繼核取方塊的大小。  
  
##  <a name="isdrawtooltipimage"></a>CMFCRibbonCheckBox::IsDrawTooltipImage  
 指出是否核取方塊相關聯的工具提示映像。  
  
```  
virtual BOOL IsDrawTooltipImage() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果沒有核取方塊，與相關聯的工具提示映像或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondraw"></a>CMFCRibbonCheckBox::OnDraw  
 由架構呼叫以繪製使用指定的裝置內容的核取方塊。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 指標`CDC`要在其中繪製此核取方塊。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondrawmenuimage"></a>CMFCRibbonCheckBox::OnDrawMenuImage  
 由架構呼叫以繪製功能表影像核取方塊。  
  
```  
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `CDC*`  
 指標`CDC`相關聯的核取方塊。  
  
 [輸入] `CRect`  
 A`CRect`物件，指定要在其中繪製的功能表影像的矩形。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果繪製影像或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
 如果未覆寫，就會傳回`FALSE`。  
  
##  <a name="ondrawonlist"></a>CMFCRibbonCheckBox::OnDrawOnList  
 由架構呼叫以繪製命令清單方塊中的核取方塊。  
  
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
 [輸入] `pDC`  
 在其中繪製此核取方塊的裝置內容的指標。  
  
 [輸入] `strText`  
 顯示文字。  
  
 [輸入] `nTextOffset`  
 距離，單位為像素，從清單方塊來顯示文字的左邊。  
  
 [輸入] `rect`  
 核取方塊的顯示矩形。  
  
 [輸入] `bIsSelected`  
 `TRUE`如果選取此核取方塊，或`FALSE`如果不是。  
  
 [輸入] `bHighlighted`  
 `TRUE`如果核取方塊會反白顯示，或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setaccdata"></a>CMFCRibbonCheckBox::SetACCData  
 設定核取方塊的協助工具資料。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>參數  
 `pParent`  
 核取方塊的父視窗。  
  
 `data`  
 核取方塊的協助工具資料。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 `TRUE`。  
  
### <a name="remarks"></a>備註  
 依預設這個方法會設定協助工具資料的核取方塊，一律會傳回`TRUE`。 覆寫此方法以設定協助工具資料並傳回值，以指出成功或失敗。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonPanel 類別](../../mfc/reference/cmfcribbonpanel-class.md)
