---
title: "CSingleDocTemplate 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSingleDocTemplate
dev_langs:
- C++
helpviewer_keywords:
- templates, SDI
- document templates, single
- single document interface (SDI), applications
- CSingleDocTemplate class
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
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
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: 78e288dd958e73495a8d513d7fe3427ccc956a61
ms.lasthandoff: 02/24/2017

---
# <a name="csingledoctemplate-class"></a>CSingleDocTemplate 類別
定義實作單一文件介面 (SDI) 的文件範本。  
  
## <a name="syntax"></a>語法  
  
```  
class CSingleDocTemplate : public CDocTemplate  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CSingleDocTemplate::CSingleDocTemplate](#csingledoctemplate)|建構 `CSingleDocTemplate` 物件。|  
  
## <a name="remarks"></a>備註  
 SDI 應用程式使用的主框架視窗來顯示文件。一次只能有一個文件可以開啟。  
  
 文件範本會定義三種類型的類別之間的關聯性︰  
  
-   文件類別，衍生自**CDocument**。  
  
-   檢視類別，會顯示上面所列的文件類別中的資料。 您可以衍生此類別從`CView`， `CScrollView`， `CFormView`，或`CEditView`。 (您也可以使用`CEditView`直接。)  
  
-   框架視窗類別，其中包含檢視。 SDI 文件範本，您可以衍生此類別從`CFrameWnd`; 如果您不需要自訂行為的主框架視窗中，您可以使用`CFrameWnd`直接而不需衍生您自己的類別。  
  
 在 SDI 應用程式通常支援一種類型的文件，因此只有一個`CSingleDocTemplate`物件。 一次只能有一個文件可以開啟。  
  
 您不需要呼叫任何成員函式`CSingleDocTemplate`除非建構函式。 架構會處理`CSingleDocTemplate`內部物件。  
  
 如需有關使用`CSingleDocTemplate`，請參閱[文件範本和文件/檢視建立程序](../../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
 `CSingleDocTemplate`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="a-namecsingledoctemplatea--csingledoctemplatecsingledoctemplate"></a><a name="csingledoctemplate"></a>CSingleDocTemplate::CSingleDocTemplate  
 建構 `CSingleDocTemplate` 物件。  
  
```  
CSingleDocTemplate(
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### <a name="parameters"></a>參數  
 `nIDResource`  
 指定文件類型所使用的資源的識別碼。 這可能包括功能表、 圖示、 快速鍵對應表，以及字串資源。  
  
 最多七個以 '\n' 字元分隔的子字串所組成的字串資源 （不包含子字串時，需要 '\n' 字元做為預留位置; 不過，不需要尾端的 '\n' 字元）。這些子字串會描述文件類型。 子字串的相關資訊，請參閱[CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 應用程式的資源檔中找到此字串資源。 例如:   
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"`  
  
 `END`  
  
 您可以編輯這個字串使用字串編輯器。整個字串會顯示為單一項目在字串編輯器中，不是以七個個別的項目。  
  
 如需這些資源類型的詳細資訊，請參閱[字串編輯器](../../windows/string-editor.md)。  
  
 `pDocClass`  
 指向`CRuntimeClass`文件類別的物件。 這個類別是**CDocument**-衍生的類別定義以代表您的文件。  
  
 `pFrameClass`  
 指向`CRuntimeClass`框架視窗類別的物件。 這個類別可以是`CFrameWnd`-衍生的類別，或者它可以是`CFrameWnd`本身，如果您想要針對主框架視窗的預設行為。  
  
 `pViewClass`  
 指向`CRuntimeClass`檢視類別的物件。 這個類別是`CView`-衍生的類別定義顯示文件。  
  
### <a name="remarks"></a>備註  
 動態配置`CSingleDocTemplate`物件，並將它傳遞給`CWinApp::AddDocTemplate`從`InitInstance`應用程式類別的成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocViewSDI #&13;](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocViewSDI #&14;](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 DOCKTOOL](../../visual-cpp-samples.md)   
 [CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument 類別](../../mfc/reference/cdocument-class.md)   
 [CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)   
 [CMultiDocTemplate 類別](../../mfc/reference/cmultidoctemplate-class.md)   
 [CView 類別](../../mfc/reference/cview-class.md)   
 [CWinApp 類別](../../mfc/reference/cwinapp-class.md)

