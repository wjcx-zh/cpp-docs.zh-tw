---
title: "CMultiDocTemplate 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
dev_langs:
- C++
helpviewer_keywords:
- MDI, template
- CMultiDocTemplate class
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
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
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: 6e58325cd4dcaec01bf8a76006bb397fccd9a171
ms.lasthandoff: 02/24/2017

---
# <a name="cmultidoctemplate-class"></a>CMultiDocTemplate 類別
定義實作多重文件介面 (MDI) 的文件範本。  
  
## <a name="syntax"></a>語法  
  
```  
class CMultiDocTemplate : public CDocTemplate  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMultiDocTemplate::CMultiDocTemplate](#cmultidoctemplate)|建構 `CMultiDocTemplate` 物件。|  
  
## <a name="remarks"></a>備註  
 MDI 應用程式使用中的使用者可以開啟零或多個文件框架視窗，其中每個文件顯示的工作區的主框架視窗。 如需 MDI 更詳細的說明，請參閱*軟體設計的 Windows 介面方針*。  
  
 文件範本會定義三種類型的類別之間的關聯性︰  
  
-   文件類別，衍生自[CDocument](../../mfc/reference/cdocument-class.md)。  
  
-   檢視類別，會顯示上面所列的文件類別中的資料。 您可以衍生此類別從[CView](../../mfc/reference/cview-class.md)， `CScrollView`， `CFormView`，或`CEditView`。 (您也可以使用`CEditView`直接。)  
  
-   框架視窗類別，其中包含檢視。 MDI 文件範本，您可以衍生此類別從`CMDIChildWnd`，或者，如果您不需要自訂文件框架視窗的行為，您可以使用[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)直接而不需衍生您自己的類別。  
  
 MDI 應用程式可以支援多個文件、 類型和不同類型的文件可以同時開啟。 您的應用程式具有每個文件類型所支援的文件範本。 例如，如果您的 MDI 應用程式支援試算表和文字文件，應用程式有兩個`CMultiDocTemplate`物件。  
  
 使用者建立新的文件時，應用程式會使用文件範本。 如果應用程式支援多個文件類型，架構文件範本從取得支援的文件類型的名稱，並顯示在 [開新檔案] 對話方塊中的清單。 一旦使用者選取文件類型，應用程式會建立文件類別物件、 框架視窗物件，以及檢視物件，並將其附加到彼此。  
  
 您不需要呼叫任何成員函式`CMultiDocTemplate`除非建構函式。 架構會處理`CMultiDocTemplate`內部物件。  
  
 如需有關`CMultiDocTemplate`，請參閱[文件範本和文件/檢視建立程序](../../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
 `CMultiDocTemplate`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cmultidoctemplate"></a>CMultiDocTemplate::CMultiDocTemplate  
 建構 `CMultiDocTemplate` 物件。  
  
```  
CMultiDocTemplate(
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### <a name="parameters"></a>參數  
 `nIDResource`  
 指定文件類型所使用的資源的識別碼。 這可能包括功能表、 圖示、 快速鍵對應表，以及字串資源。  
  
 最多七個以 '\n' 字元分隔的子字串所組成的字串資源 （不包含子字串時，需要 '\n' 字元做為預留位置; 不過，不需要尾端的 '\n' 字元）;這些子字串會描述文件類型。 如需子字串，請參閱[CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 應用程式的資源檔中找到此字串資源。 例如：  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"`  
  
 `END`  
  
 請注意，字串是以 '\n' 字元。這是因為第一個子字串不是 MDI 應用程式，因此並不包含。 您可以編輯這個字串使用字串編輯器。整個字串會顯示為單一項目在字串編輯器中，不是以七個個別的項目。  
  
 如需這些資源類型的詳細資訊，請參閱[資源編輯器](../../windows/resource-editors.md)。  
  
 `pDocClass`  
 指向`CRuntimeClass`文件類別的物件。 這個類別是**CDocument**-衍生的類別定義以代表您的文件。  
  
 `pFrameClass`  
 指向`CRuntimeClass`框架視窗類別的物件。 這個類別可以是`CMDIChildWnd`-衍生的類別，或者它可以是`CMDIChildWnd`本身如果想要對您的文件框架視窗的預設行為。  
  
 `pViewClass`  
 指向`CRuntimeClass`檢視類別的物件。 這個類別是`CView`-衍生的類別定義顯示文件。  
  
### <a name="remarks"></a>備註  
 以動態方式配置一個`CMultiDocTemplate`物件的每個文件類型支援您的應用程式，並傳遞至每個`CWinApp::AddDocTemplate`從`InitInstance`應用程式類別的成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&92;](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]  
  
 以下是第二個範例。  
  
 [!code-cpp[NVC_MFCDocView #&93;](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)   
 [CSingleDocTemplate 類別](../../mfc/reference/csingledoctemplate-class.md)   
 [CWinApp 類別](../../mfc/reference/cwinapp-class.md)

