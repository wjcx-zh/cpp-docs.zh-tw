---
title: CRuntimeClass 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 365247dc41ea75e67f63b2bb76b5bfe0c14a7ead
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cruntimeclass-structure"></a>CRuntimeClass 結構
每個類別衍生自`CObject`聯`CRuntimeClass`可用來取得在執行階段物件或其基底類別的相關資訊的結構。  
  
## <a name="syntax"></a>語法  
  
```  
struct CRuntimeClass  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CRuntimeClass::CreateObject](#createobject)|在執行階段期間建立的物件。|  
|[CRuntimeClass::FromName](#fromname)|使用熟悉的類別名稱的執行階段期間建立的物件。|  
|[CRuntimeClass::IsDerivedFrom](#isderivedfrom)|決定是否類別衍生自指定的類別。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CRuntimeClass::m_lpszClassName](#m_lpszclassname)|類別的名稱。|  
|[CRuntimeClass::m_nObjectSize](#m_nobjectsize)|物件大小 (以位元組為單位)。|  
|[CRuntimeClass::m_pBaseClass](#m_pbaseclass)|指標`CRuntimeClass`結構的基底類別。|  
|[CRuntimeClass::m_pfnCreateObject](#m_pfncreateobject)|以動態方式建立物件的函式的指標。|  
|[CRuntimeClass::m_pfnGetBaseClass](#m_pfngetbaseclass)|傳回`CRuntimeClass`結構 （僅限可用時以動態方式連結）。|  
|[CRuntimeClass::m_wSchema](#m_wschema)|類別的結構描述編號。|  
  
## <a name="remarks"></a>備註  
 `CRuntimeClass` 是一種結構，因此不需要基底類別。  
  
 當需要檢查函式引數的實際類型時，或當您必須撰寫特殊用途的物件類別為基礎的程式碼，則在執行階段判斷物件類別的功能會非常有用。 C++ 語言並不直接支援執行階段類別資訊。  
  
 `CRuntimeClass` 提供相關的 c + + 物件，例如指標的相關資訊`CRuntimeClass`基底類別和相關類別的 ASCII 類別名稱。 此結構也會實作可用來動態建立物件，指定的物件類型，使用熟悉的名稱，並判斷是否相關聯的類別會衍生自特定類別的各種功能。  
  
 如需有關使用`CRuntimeClass`，請參閱文章[存取執行階段類別資訊](../../mfc/accessing-run-time-class-information.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CRuntimeClass`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="createobject"></a>  CRuntimeClass::CreateObject  
 呼叫此函式可動態執行階段期間建立指定的類別。  
  
```  
CObject* CreateObject();  
  
static CObject* PASCAL CreateObject(LPCSTR lpszClassName);  
  
static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```  
  
### <a name="parameters"></a>參數  
 `lpszClassName`  
 要建立之類別的熟悉名稱。  
  
### <a name="return-value"></a>傳回值  
 新建立的物件的指標或**NULL**如果找不到類別名稱，或沒有記憶體不足，無法建立物件。  
  
### <a name="remarks"></a>備註  
 類別衍生自`CObject`可支援動態建立，也就是在執行階段建立指定之類別的物件。 文件、 檢視和框架類別，例如，應該支援動態建立。 如需有關動態建立和`CreateObject`成員，請參閱[CObject 類別](../../mfc/using-cobject.md)和[CObject 類別： 指定功能層級](../../mfc/specifying-levels-of-functionality.md)。  
  
### <a name="example"></a>範例  
  請參閱範例的[IsDerivedFrom](#isderivedfrom)。  
  
##  <a name="fromname"></a>  CRuntimeClass::FromName  
 呼叫此函式可擷取`CRuntimeClass`熟悉的名稱相關聯的結構。  
  
```  
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);  
  
static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```  
  
### <a name="parameters"></a>參數  
 `lpszClassName`  
 類別的熟悉名稱衍生自`CObject`。  
  
### <a name="return-value"></a>傳回值  
 指標`CRuntimeClass`，對應到物件名稱傳入`lpszClassName`。 此函數會傳回**NULL**如果找不到任何相符的類別名稱。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]  
  
##  <a name="isderivedfrom"></a>  CRuntimeClass::IsDerivedFrom  
 呼叫此函式來判斷是否發出呼叫的類別會衍生自指定的類別*pBaseClass*參數。  
  
```  
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;

 
```  
  
### <a name="parameters"></a>參數  
 *pBaseClass*  
 類別的熟悉名稱衍生自`CObject`。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果類別呼叫`IsDerivedFrom`衍生自基底類別的`CRuntimeClass`結構已指定做為參數，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 關聯性取決於 「 查核 」 從鏈結中向上衍生的類別成員的類別到頂端。 此函式只會傳回**FALSE**如果沒有找到符合的基底類別。  
  
> [!NOTE]
>  若要使用`CRuntimeClass`結構，您必須包含`IMPLEMENT_DYNAMIC`， `IMPLEMENT_DYNCREATE`，或`IMPLEMENT_SERIAL`巨集，在您要擷取的執行階段物件資訊類別的實作。  
  
 如需有關使用`CRuntimeClass`，請參閱文章[CObject 類別： 存取執行階段類別資訊](../../mfc/accessing-run-time-class-information.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]  
  
##  <a name="m_lpszclassname"></a>  CRuntimeClass::m_lpszClassName  
 以 null 結束的字串，包含 ASCII 的類別名稱。  
  
### <a name="remarks"></a>備註  
 這個名稱可以用來建立執行個體的類別使用`FromName`成員函式。  
  
### <a name="example"></a>範例  
  請參閱範例的[IsDerivedFrom](#isderivedfrom)。  
  
##  <a name="m_nobjectsize"></a>  CRuntimeClass::m_nObjectSize  
 物件，以位元組為單位的大小。  
  
### <a name="remarks"></a>備註  
 如果物件具有資料成員會指向配置的記憶體，不包含該記憶體的大小。  
  
### <a name="example"></a>範例  
  請參閱範例的[IsDerivedFrom](#isderivedfrom)。  
  
##  <a name="m_pbaseclass"></a>  CRuntimeClass::m_pBaseClass  
 如果您的應用程式以靜態方式連結至 MFC，此資料成員包含的指標`CRuntimeClass`結構的基底類別。  
  
### <a name="remarks"></a>備註  
 如果您的應用程式動態連結至 MFC 程式庫，請參閱[m_pfnGetBaseClass](#m_pfngetbaseclass)。  
  
### <a name="example"></a>範例  
  請參閱範例的[IsDerivedFrom](#isderivedfrom)。  
  
##  <a name="m_pfncreateobject"></a>  CRuntimeClass::m_pfnCreateObject  
 預設建構函式來建立您的類別物件的函式指標。  
  
### <a name="remarks"></a>備註  
 此指標才會有效類別支援動態建立。否則，函數會傳回**NULL**。  
  
##  <a name="m_pfngetbaseclass"></a>  CRuntimeClass::m_pfnGetBaseClass  
 如果您的應用程式使用 MFC 程式庫共用的 dll，此資料成員指向函式傳回`CRuntimeClass`結構的基底類別。  
  
### <a name="remarks"></a>備註  
 如果您的應用程式以靜態方式連結 MFC 程式庫，請參閱[m_pBaseClass](#m_pbaseclass)。  
  
### <a name="example"></a>範例  
  請參閱範例的[IsDerivedFrom](#isderivedfrom)。  
  
##  <a name="m_wschema"></a>  CRuntimeClass::m_wSchema  
 結構描述編號 (不可序列化的類別-1)。  
  
### <a name="remarks"></a>備註  
 如需有關結構描述的數字的詳細資訊，請參閱[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)巨集。  
  
### <a name="example"></a>範例  
  請參閱範例的[IsDerivedFrom](#isderivedfrom)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CObject::GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)   
 [Cobject:: Iskindof](../../mfc/reference/cobject-class.md#iskindof)   
 [RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)   
 [您的類別](run-time-object-model-services.md#implement_dynamic)   
 [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)   
 [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)



