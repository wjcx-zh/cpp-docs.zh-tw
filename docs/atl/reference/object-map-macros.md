---
title: "物件對應巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
caps.latest.revision: 16
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: f03ca61c6ab3c550c316b380d34eb5fa4f3b61de
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="object-map-macros"></a>物件對應巨集
這些巨集定義的對應物件和項目。  
  
|||  
|-|-|  
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|可讓您指定的類別物件的文字描述，將物件對應到輸入。|  
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|輸入物件對應中的 ATL 物件、 更新登錄，並建立物件的執行個體。|  
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|可讓您指定應該註冊並初始化物件，而不應該透過 `CoCreateInstance` 從外部建立。|  

## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
   
##  <a name="declare_object_description"></a>DECLARE_OBJECT_DESCRIPTION  
 可讓您指定的類別物件的文字描述。  
  
```
DECLARE_OBJECT_DESCRIPTION( x )
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]類別物件的描述。  
  
### <a name="remarks"></a>備註  
 ATL 物件對應到輸入這項描述[OBJECT_ENTRY](http://msdn.microsoft.com/en-us/abd10ee2-54f0-4f94-9ec2-ddf8f4c8c8cd)巨集。  
  
 `DECLARE_OBJECT_DESCRIPTION`實作`GetObjectDescription`函式，可用來覆寫[CComCoClass::GetObjectDescription](ccomcoclass-class.md#getobjectdescription)方法。  

  
 `GetObjectDescription`函式會呼叫**IComponentRegistrar::GetComponents**。 **IComponentRegistrar**是自動化的介面，可讓您註冊和取消註冊 DLL 中的個別元件。 當您使用 ATL 專案精靈 」 建立元件登錄物件時，此精靈會自動實作**IComponentRegistrar**介面。 **IComponentRegistrar**一般是由 Microsoft Transaction Server。  
  
 如需 ATL 專案精靈 的詳細資訊，請參閱文章[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&123;](../../atl/codesnippet/cpp/object-map-macros_1.h)]  
  
##  <a name="object_entry_auto"></a>OBJECT_ENTRY_AUTO  
 輸入物件對應中的 ATL 物件、 更新登錄，並建立物件的執行個體。  
  
```
OBJECT_ENTRY_AUTO( clsid, class )
```  
  
### <a name="parameters"></a>參數  
 `clsid`  
 [in] COM 類別的 CLSID，由名為 `class` 的 C++ 類別實作。  
  
 `class`  
 [in] C++ 類別的名稱，實作 `clsid` 所代表的 COM 類別。  
  
### <a name="remarks"></a>備註  
 物件進入巨集會放在專案的全域範圍，以支援註冊、初始化和建立類別。  
  
 `OBJECT_ENTRY_AUTO`輸入函式指標的建立者類別和類別 factory 建立者類別`CreateInstance`函式自動產生 ATL 物件對應到此物件。 當[CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver)是呼叫，更新系統登錄中的物件對應每個物件。  

  
 下表描述如何加入至物件對應的資訊取自指定第二個參數做為這個巨集的類別。  
  
|資訊|取自|  
|---------------------|-------------------|  
|COM 登錄|[登錄巨集](../../atl/reference/registry-macros.md)|  
|類別處理站的建立|[類別 Factory 巨集](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|建立執行個體|[彙總巨集](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|元件類別註冊|[類別巨集](../../atl/reference/category-macros.md)|  
|類別層級初始化和清除|[ObjectMain](ccomobjectrootex-class.md#objectmain)|  

  
##  <a name="object_entry_non_createable_ex_auto"></a>OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO  
 可讓您指定應該註冊並初始化物件，而不應該透過 `CoCreateInstance` 從外部建立。  
  
```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```  
  
### <a name="parameters"></a>參數  
 `clsid`  
 [in] COM 類別的 CLSID，由名為 `class` 的 C++ 類別實作。  
  
 `class`  
 [in] C++ 類別的名稱，實作 `clsid` 所代表的 COM 類別。  
  
### <a name="remarks"></a>備註  
 物件進入巨集會放在專案的全域範圍，以支援註冊、初始化和建立類別。  
  
 `OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO`可讓您指定的物件應該註冊，並初始化 (請參閱[OBJECT_ENTRY_AUTO](#object_entry_auto)如需詳細資訊)，但不是應該可以透過建立`CoCreateInstance`。  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)

