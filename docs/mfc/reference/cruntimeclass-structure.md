---
title: "CRuntimeClass 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- CRuntimeClass structure
- dynamic class information
- runtime, class information
- run-time class, CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 17994895aec5eee3fbe67bef5f80494988906df9
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cruntimeclass-structure"></a>CRuntimeClass 結構
每個類別衍生自`CObject`聯`CRuntimeClass`結構可讓您取得在執行階段物件或其基底類別的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
struct CRuntimeClass  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CRuntimeClass::CreateObject](#createobject)|在執行階段期間建立的物件。|  
|[CRuntimeClass::FromName](#fromname)|使用熟悉的類別名稱的執行階段期間建立的物件。|  
|[CRuntimeClass::IsDerivedFrom](#isderivedfrom)|決定是否類別衍生自指定的類別。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CRuntimeClass::m_lpszClassName](#m_lpszclassname)|類別的名稱。|  
|[CRuntimeClass::m_nObjectSize](#m_nobjectsize)|物件大小 (以位元組為單位)。|  
|[CRuntimeClass::m_pBaseClass](#m_pbaseclass)|指標`CRuntimeClass`結構的基底類別。|  
|[CRuntimeClass::m_pfnCreateObject](#m_pfncreateobject)|動態建立物件的函式指標。|  
|[CRuntimeClass::m_pfnGetBaseClass](#m_pfngetbaseclass)|傳回`CRuntimeClass`結構 （僅限可用時以動態方式連結）。|  
|[CRuntimeClass::m_wSchema](#m_wschema)|類別的結構描述編號。|  
  
## <a name="remarks"></a>備註  
 `CRuntimeClass`是一種結構，因此不需要基底類別。  
  
 當需要額外的型別檢查函式引數時，，或者當您必須撰寫特殊用途的程式碼的物件類別為基礎，能夠在執行階段決定物件的類別會很有用。 C++ 語言並不直接支援執行階段類別資訊。  
  
 `CRuntimeClass`提供相關的 c + + 物件，例如指標的相關資訊`CRuntimeClass`基底類別和相關類別的 ASCII 類別名稱。 此結構也會實作可用來動態建立物件，指定物件的型別使用熟悉的名稱，然後判斷是否相關聯的類別會衍生自特定類別的各種功能。  
  
 如需有關使用`CRuntimeClass`，請參閱文章[存取執行階段類別資訊](../../mfc/accessing-run-time-class-information.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CRuntimeClass`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="createobject"></a>CRuntimeClass::CreateObject  
 呼叫此函式動態建立指定的類別在執行階段。  
  
```  
CObject* CreateObject();  
  
static CObject* PASCAL CreateObject(LPCSTR lpszClassName);  
  
static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```  
  
### <a name="parameters"></a>參數  
 `lpszClassName`  
 若要建立類別熟悉的名稱。  
  
### <a name="return-value"></a>傳回值  
 新建立的物件的指標或**NULL**如果找不到類別名稱，或有記憶體不足，無法建立物件。  
  
### <a name="remarks"></a>備註  
 類別衍生自`CObject`可以支援動態建立，也就是在執行階段建立指定類別的物件。 文件、 檢視和框架類別，例如應該支援動態建立。 如需有關動態建立和`CreateObject`成員，請參閱[CObject 類別](../../mfc/using-cobject.md)和[CObject 類別︰ 指定功能層級](../../mfc/specifying-levels-of-functionality.md)。  
  
### <a name="example"></a>範例  
  請參閱範例[IsDerivedFrom](#isderivedfrom)。  
  
##  <a name="fromname"></a>CRuntimeClass::FromName  
 呼叫此函式可擷取`CRuntimeClass`與熟悉的名稱相關聯的結構。  
  
```  
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);  
  
static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```  
  
### <a name="parameters"></a>參數  
 `lpszClassName`  
 熟悉的類別名稱衍生自`CObject`。  
  
### <a name="return-value"></a>傳回值  
 指標`CRuntimeClass`物件，對應到名稱中傳遞`lpszClassName`。 此函數會傳回**NULL**如果找不到任何相符的類別名稱。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCObjectSample #&17;](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]  
  
##  <a name="isderivedfrom"></a>CRuntimeClass::IsDerivedFrom  
 呼叫此函式來判斷是否發出呼叫的類別會衍生自指定類別*pBaseClass*參數。  
  
```  
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;

 
```  
  
### <a name="parameters"></a>參數  
 *pBaseClass*  
 熟悉的類別名稱衍生自`CObject`。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果類別呼叫`IsDerivedFrom`衍生自基底類別的`CRuntimeClass`結構就會做為參數指定，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 關聯性取決於 「 查核 」 從鏈結衍生的類別成員的類別到頂端。 此函式只會傳回**FALSE**如果沒有找到符合的基底類別。  
  
> [!NOTE]
>  若要使用`CRuntimeClass`結構，您必須包含`IMPLEMENT_DYNAMIC`， `IMPLEMENT_DYNCREATE`，或`IMPLEMENT_SERIAL`巨集，在您要擷取執行階段物件資訊的類別實作。  
  
 如需有關使用`CRuntimeClass`，請參閱文章[CObject 類別︰ 存取執行階段類別資訊](../../mfc/accessing-run-time-class-information.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCObjectSample #&18;](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]  
  
##  <a name="m_lpszclassname"></a>CRuntimeClass::m_lpszClassName  
 以 null 結束的字串，包含 ASCII 類別名稱。  
  
### <a name="remarks"></a>備註  
 這個名稱可以用來建立使用類別的執行個體`FromName`成員函式。  
  
### <a name="example"></a>範例  
  請參閱範例[IsDerivedFrom](#isderivedfrom)。  
  
##  <a name="m_nobjectsize"></a>CRuntimeClass::m_nObjectSize  
 物件，以位元組為單位的大小。  
  
### <a name="remarks"></a>備註  
 如果物件具有資料成員指向已配置的記憶體，不包含該記憶體的大小。  
  
### <a name="example"></a>範例  
  請參閱範例[IsDerivedFrom](#isderivedfrom)。  
  
##  <a name="m_pbaseclass"></a>CRuntimeClass::m_pBaseClass  
 如果您的應用程式以靜態方式連結至 MFC，此資料成員都包含一個指向`CRuntimeClass`結構的基底類別。  
  
### <a name="remarks"></a>備註  
 如果您的應用程式動態連結至 MFC 程式庫，請參閱[m_pfnGetBaseClass](#m_pfngetbaseclass)。  
  
### <a name="example"></a>範例  
  請參閱範例[IsDerivedFrom](#isderivedfrom)。  
  
##  <a name="m_pfncreateobject"></a>CRuntimeClass::m_pfnCreateObject  
 建立您的類別物件的預設建構函式的函式指標。  
  
### <a name="remarks"></a>備註  
 這個指標才會有效的類別支援動態建立。否則，函數會傳回**NULL**。  
  
##  <a name="m_pfngetbaseclass"></a>CRuntimeClass::m_pfnGetBaseClass  
 如果您的應用程式會使用 MFC 程式庫當做共用 DLL，此資料成員指向函式傳回`CRuntimeClass`結構的基底類別。  
  
### <a name="remarks"></a>備註  
 如果您的應用程式以靜態方式連結至 MFC 程式庫，請參閱[m_pBaseClass](#m_pbaseclass)。  
  
### <a name="example"></a>範例  
  請參閱範例[IsDerivedFrom](#isderivedfrom)。  
  
##  <a name="m_wschema"></a>CRuntimeClass::m_wSchema  
 結構描述編號 (不可序列化的類別-1)。  
  
### <a name="remarks"></a>備註  
 如需有關結構描述的數字的詳細資訊，請參閱[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)巨集。  
  
### <a name="example"></a>範例  
  請參閱範例[IsDerivedFrom](#isderivedfrom)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CObject::GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)   
 [Cobject:: Iskindof](../../mfc/reference/cobject-class.md#iskindof)   
 [RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)   
 [您的類別](run-time-object-model-services.md#implement_dynamic)   
 [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)   
 [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)




