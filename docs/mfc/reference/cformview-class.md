---
title: CFormView 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFormView
- AFXEXT/CFormView
- AFXEXT/CFormView::CFormView
- AFXEXT/CFormView::IsInitDlgCompleted
dev_langs:
- C++
helpviewer_keywords:
- CFormView [MFC], CFormView
- CFormView [MFC], IsInitDlgCompleted
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3486285b7b6430e9cd6f0e4a936aa3341bd72e0f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366576"
---
# <a name="cformview-class"></a>CFormView 類別
用於表單檢視的基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CFormView : public CScrollView  
```  
  
## <a name="members"></a>成員  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CFormView::CFormView](#cformview)|建構 `CFormView` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|用於初始化期間同步處理。|  
  
## <a name="remarks"></a>備註  
 表單檢視基本上是包含控制項的檢視。 這些控制項根據對話方塊範本資源而佈置。 如果您想要應用程式中有表單，請使用 `CFormView`。 這些檢視支援捲動，視需要使用[CScrollView](../../mfc/reference/cscrollview-class.md)功能。  
  
 當您準備[建立表單架構應用程式](../../mfc/reference/creating-a-forms-based-mfc-application.md)，您可以根據其檢視類別`CFormView`，因此表單架構應用程式。  
  
 您也可以新增插入[表單主題](../../mfc/form-views-mfc.md)到文件檢視架構的應用程式。 即使您的應用程式一開始不支援表單，Visual C++ 也會在您插入新表單時加入這項支援。  
  
 MFC 應用程式精靈和 [加入類別] 命令是建立表單架構應用程式的慣用方法。 如果您要建立表單架構應用程式，而不使用這些方法，請參閱[建立表單架構應用程式](../../mfc/reference/creating-a-forms-based-mfc-application.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 `CFormView`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxext.h  
  
##  <a name="cformview"></a>  CFormView::CFormView  
 建構 `CFormView` 物件。  
  
```  
CFormView(LPCTSTR lpszTemplateName);  
CFormView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>參數  
 `lpszTemplateName`  
 包含的對話方塊範本資源名稱的以 null 結尾字串。  
  
 `nIDTemplate`  
 包含對話方塊範本資源的識別碼。  
  
### <a name="remarks"></a>備註  
 當您建立的物件類型的衍生自`CFormView`，叫用的建構函式來建立檢視物件，並識別基礎檢視的對話方塊資源的其中一個。 您可以識別資源名稱 （傳遞字串做為引數的建構函式） 或它的 ID （傳遞的不帶正負號的整數，做為引數）。  
  
 表單檢視 視窗和子控制項才會建立`CWnd::Create`呼叫。 `CWnd::Create` 會呼叫文件和檢視建立程序的一部分，這由文件範本所驅動的架構。  
  
> [!NOTE]
>  您的衍生的類別*必須*提供它自己的建構函式。 在建構函式，來叫用建構函式， `CFormView::CFormView`、 資源名稱或識別碼做為引數，如上述類別概觀中所示。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]  
  
 [!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]  
  
##  <a name="isinitdlgcompleted"></a>  CFormView::IsInitDlgCompleted  
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
