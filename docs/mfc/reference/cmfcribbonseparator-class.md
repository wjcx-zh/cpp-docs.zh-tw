---
title: "CMFCRibbonSeparator 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::AddToListBox
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CopyFrom
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::GetRegularSize
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsTabStop
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDraw
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDrawOnList
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonSeparator class
- GetThisClass method
- CreateObject method
ms.assetid: bedb1a53-cb07-4c3c-be12-698c5409e7cf
caps.latest.revision: 21
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
ms.openlocfilehash: 98a58d43b5e6299f26521d873caec06d4581f7b3
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonseparator-class"></a>CMFCRibbonSeparator 類別
實作功能區分隔符號。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonSeparator : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCRibbonSeparator::CMFCRibbonSeparator](#cmfcribbonseparator)|建構 `CMFCRibbonSeparator` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|說明|  
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|加入分隔符號，**命令**清單中**自訂**對話方塊。 (覆寫[CMFCRibbonBaseElement::AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox)。)|  
|`CMFCRibbonSeparator::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CMFCRibbonSeparator::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
  
### <a name="protected-methods"></a>保護方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCRibbonSeparator::CopyFrom](#copyfrom)|設定分隔成員變數，從另一個物件複製方法。|  
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|傳回大小的分隔符號。|  
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|指出這是否為分隔符號。|  
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|指出這是否為定位停駐點。|  
|[CMFCRibbonSeparator::OnDraw](#ondraw)|若要快速存取工具列或功能區上繪製分隔符號系統呼叫。|  
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|在上繪製分隔符號系統呼叫**命令**清單。|  
  
## <a name="remarks"></a>備註  
 功能區分隔符號是垂直或水平的線條，以邏輯方式分隔功能區項目。 在功能區控制項、 主應用程式 功能表、 功能區狀態列，以及快速存取工具列，可以繪製分隔符號。  
  
 若要在應用程式中使用分隔符號，建構新的物件，並將它加入至主應用程式功能表，如下所示︰  
  
```  
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...  
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```  
呼叫[CMFCRibbonPanel::AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator)至功能區面板加入分隔符號。 分隔符號會配置，並在內部新增`AddSeparator`方法。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxbaseribbonelement.h  
  
##  <a name="addtolistbox"></a>CMFCRibbonSeparator::AddToListBox  
 加入分隔符號，**命令**清單中**自訂**對話方塊。  
  
```  
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,  
    BOOL bDeep);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndListBox`  
 指標**命令**其中加入分隔符號的清單。  
  
 [in] `bDeep`  
 忽略。  
  
### <a name="return-value"></a>傳回值  
 在清單方塊中所指定的字串以零起始的索引`pWndListBox`。  
  
##  <a name="cmfcribbonseparator"></a>CMFCRibbonSeparator::CMFCRibbonSeparator  
 建構 `CMFCRibbonSeparator` 物件。  
  
```  
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bIsHoriz`  
 如果`TRUE`，分隔符號是水平; 如果`FALSE`，分隔符號是垂直。  
  
### <a name="remarks"></a>備註  
 應用程式功能表中，會使用水平的分隔符號。 工具列中，會使用垂直的分隔符號。  
  
### <a name="example"></a>範例  
 下列範例示範如何建構的物件`CMFCRibbonSeparator`類別。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&19;](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]  
  
##  <a name="copyfrom"></a>CMFCRibbonSeparator::CopyFrom  
 設定分隔成員變數，從另一個物件複製方法。  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>參數  
 [in] `Src`  
 要複製的來源功能區項目。  
  
##  <a name="getregularsize"></a>CMFCRibbonSeparator::GetRegularSize  
 傳回大小的分隔符號。  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容指標。  
  
### <a name="return-value"></a>傳回值  
 在指定的裝置內容上分隔符號的大小。  
  
##  <a name="isseparator"></a>CMFCRibbonSeparator::IsSeparator  
 指出這是否為分隔符號。  
  
```  
virtual BOOL IsSeparator() const;  
```  
  
### <a name="return-value"></a>傳回值  
 一律`TRUE`這個類別。  
  
##  <a name="istabstop"></a>CMFCRibbonSeparator::IsTabStop  
 指出這是否為定位停駐點。  
  
```  
virtual BOOL IsTabStop() const;  
```  
  
### <a name="return-value"></a>傳回值  
 一律`FALSE`這個類別。  
  
### <a name="remarks"></a>備註  
 功能區分隔符號不是定位停駐點。  
  
##  <a name="ondraw"></a>CMFCRibbonSeparator::OnDraw  
 若要快速存取工具列或功能區上繪製分隔符號系統呼叫。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
##  <a name="ondrawonlist"></a>CMFCRibbonSeparator::OnDrawOnList  
 在上繪製分隔符號系統呼叫**命令**清單。  
  
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
  
|||  
|-|-|  
|參數|描述|  
|[in] `pDC`|裝置內容的指標。|  
|[in] `strText`|清單中顯示的文字。|  
|[in] `nTextOffset`|左邊算的起，這個周框與文字之間的間距。|  
|[in] `rect`|指定週框。|  
|[in] `bIsSelected`|忽略。|  
|[in] `bHighlighted`|忽略。|  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)

