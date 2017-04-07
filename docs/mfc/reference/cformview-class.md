---
title: "CFormView 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFormView
- AFXEXT/CFormView
- AFXEXT/CFormView::CFormView
- AFXEXT/CFormView::IsInitDlgCompleted
dev_langs:
- C++
helpviewer_keywords:
- views, containing controls
- CFormView class
- form views
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
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
ms.openlocfilehash: 82b38b04aa3cf2368d41ee20847c952c3082d4e4
ms.lasthandoff: 02/24/2017

---
# <a name="cformview-class"></a>CFormView 類別
用於表單檢視的基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CFormView : public CScrollView  
```  
  
## <a name="members"></a>Members  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CFormView::CFormView](#cformview)|建構 `CFormView` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|用於初始化期間同步處理。|  
  
## <a name="remarks"></a>備註  
 表單檢視基本上是包含控制項的檢視。 這些控制項根據對話方塊範本資源而佈置。 如果您想要應用程式中有表單，請使用 `CFormView`。 這些檢視支援捲動功能，如有需要使用[CScrollView](../../mfc/reference/cscrollview-class.md)功能。  
  
 當您準備[建立表單架構應用程式](../../mfc/reference/creating-a-forms-based-mfc-application.md)，您可以根據其檢視類別`CFormView`，讓表單架構應用程式。  
  
 您也可以新增插入[表單主題](../../mfc/form-views-mfc.md)到文件檢視為基礎的應用程式。 即使您的應用程式一開始不支援表單，Visual C++ 也會在您插入新表單時加入這項支援。  
  
 MFC 應用程式精靈和 [加入類別] 命令是建立表單架構應用程式的慣用方法。 如果您要建立表單架構應用程式，而不需使用這些方法，請參閱[建立表單架構應用程式](../../mfc/reference/creating-a-forms-based-mfc-application.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 `CFormView`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxext.h  
  
##  <a name="cformview"></a>CFormView::CFormView  
 建構 `CFormView` 物件。  
  
```  
CFormView(LPCTSTR lpszTemplateName);  
CFormView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>參數  
 `lpszTemplateName`  
 包含 null 結尾字串的對話方塊範本資源的名稱。  
  
 `nIDTemplate`  
 包含對話方塊範本資源的 ID 編號。  
  
### <a name="remarks"></a>備註  
 當您建立的物件型別衍生自`CFormView`，叫用的建構函式來建立檢視物件，並識別對話方塊資源檢視所依據的其中一個。 您可以識別資源名稱 (pass 字串做為引數的建構函式) 或其 ID （不帶正負號的整數做為引數傳遞）。  
  
 表單檢視 視窗和子控制項才會建立`CWnd::Create`呼叫。 `CWnd::Create`會呼叫文件和檢視建立程序的一部分，這由文件範本所驅動的架構。  
  
> [!NOTE]
>  您的衍生的類別*必須*提供它自己的建構函式。 在建構函式，會叫用建構函式， `CFormView::CFormView`、 資源名稱或識別碼做為引數，如上述的類別概觀中所示。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&90;](../../mfc/codesnippet/cpp/cformview-class_1.h)]  
  
 [!code-cpp[NVC_MFCDocView #&91;](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]  
  
##  <a name="isinitdlgcompleted"></a>CFormView::IsInitDlgCompleted  
 MFC 用來確保完成初始化後再執行其他作業。  
  
```  
BOOL IsInitDlgCompleted() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果這個對話方塊的初始化函式已完成，則為 true。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 SNAPVW](../../visual-cpp-samples.md)   
 [MFC 範例 VIEWEX](../../visual-cpp-samples.md)   
 [CScrollView 類別](../../mfc/reference/cscrollview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDialog 類別](../../mfc/reference/cdialog-class.md)   
 [CScrollView 類別](../../mfc/reference/cscrollview-class.md)

