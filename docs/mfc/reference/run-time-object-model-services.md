---
title: "執行階段物件模型服務 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
caps.latest.revision: 15
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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 8739201489644b0f1695a70d0dc12d04ca47aa68
ms.lasthandoff: 02/24/2017

---
# <a name="run-time-object-model-services"></a>執行階段物件模型服務
類別[CObject](../../mfc/reference/cobject-class.md)和[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)封裝數個物件服務，包括存取執行階段類別資訊、 序列化和動態物件建立。 從 `CObject` 衍生的所有類別都會繼承此功能。  
  
 對執行階段類別資訊的存取可讓您決定在執行階段的物件類別相關資訊。 當您需要進行函式引數的額外類別檢查時，以及當您必須根據物件類別撰寫特殊用途的程式碼時，能夠在執行階段決定物件的類別就很有用。 C++ 語言並不直接支援執行階段類別資訊。  
  
 序列化是對於檔案來回寫入或讀取物件內容的程序。 即使應用程式結束之後，您還是可以使用序列化儲存物件的內容。 當應用程式重新啟動時，您可以從檔案讀取物件。 這類資料物件稱為「持續性」。  
  
 動態物件建立可讓您在執行階段建立指定類別的物件。 例如，因為架構需要動態建立文件、檢視和框架物件，所以必須支援動態建立。  
  
 下表列出支援的執行階段類別資訊、序列化和動態建立的 MFC 巨集。  
  
 如需有關這些執行階段物件服務和序列化的詳細資訊，請參閱文章[CObject 類別︰ 存取執行階段類別資訊](../../mfc/accessing-run-time-class-information.md)。  
  
### <a name="run-time-object-model-services-macros"></a>執行階段物件模型服務巨集  
  
|||  
|-|-|  
|[DECLARE_DYNAMIC](#declare_dynamic)|啟用對於執行階段類別資訊的存取 (必須在類別宣告中使用)。|  
|[DECLARE_DYNCREATE](#declare_dyncreate)|啟用動態建立和存取執行階段類別資訊 (必須在類別宣告中使用)。|  
|[DECLARE_SERIAL](#declare_serial)|啟用序列化和存取執行階段類別資訊 (必須在類別宣告中使用)。|  
|[您的類別](#implement_dynamic)|啟用對執行階段類別資訊的存取 (必須在類別實作中使用)。|  
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|啟用動態建立和存取執行階段資訊 (必須在類別實作中使用)。|  
|[IMPLEMENT_SERIAL](#implement_serial)|允許序列化和存取執行階段類別資訊 (必須在類別實作中使用)。|  
|[RUNTIME_CLASS](#runtime_class)|傳回對應至已命名類別的 `CRuntimeClass` 結構。|  


 OLE 經常需要在執行階段動態建立物件。 例如，OLE 伺服器應用程式必須能夠動態建立 OLE 項目以回應來自用戶端的要求。 同樣地，Automation 伺服器必須能夠建立項目以回應從 Automation 用戶端的要求。  
  
 MFC 程式庫提供 OLE 兩個特定巨集。  
  
### <a name="dynamic-creation-of-ole-objects"></a>動態建立 OLE 物件  
  
|||  
|-|-|  
|[DECLARE_OLECREATE](#declare_olecreate)|讓物件透過 OLE Automation 建立。|  
|[IMPLEMENT_OLECREATE](#implement_olecreate)|讓物件經由 OLE 系統建立。|  
  
##  <a name="a-namedeclaredynamica--declaredynamic"></a><a name="declare_dynamic"></a>DECLARE_DYNAMIC  
 加入衍生的類別時，存取的物件類別的執行階段資訊的能力`CObject`。  
  
```
DECLARE_DYNAMIC(class_name) 
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 類別的實際名稱。  
  
### <a name="remarks"></a>備註  
 新增`DECLARE_DYNAMIC`巨集類別的標頭 (.h) 模組，然後將該模組包含在所有.cpp 模組需要存取此類別的物件。  
  
 如果您使用**DECLARE**_**動態**和`IMPLEMENT_DYNAMIC`巨集所述，您可以使用`RUNTIME_CLASS`巨集和`CObject::IsKindOf`函式可在執行階段決定物件的類別。  
  
 如果`DECLARE_DYNAMIC`包含在類別宣告，然後`IMPLEMENT_DYNAMIC`必須包含在類別實作。  
  
 如需有關`DECLARE_DYNAMIC`巨集，請參閱[CObject 類別主題](../../mfc/using-cobject.md)。  
  
### <a name="example"></a>範例  
 請參閱範例[IMPLEMENT_DYNAMIC](#implement_dynamic)。  

### <a name="requirements"></a>需求  
 **標頭：** afx.h 

##  <a name="a-namedeclaredyncreatea--declaredyncreate"></a><a name="declare_dyncreate"></a>DECLARE_DYNCREATE  
 可讓物件的`CObject`-衍生類別能夠在執行階段動態建立。  
  
```
DECLARE_DYNCREATE(class_name)   
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 類別的實際名稱。  
  
### <a name="remarks"></a>備註  
 架構會使用這項功能以動態方式建立新的物件。 例如，新建立的檢視當您開啟新文件。 文件、 檢視和框架類別應該支援動態建立，因為架構需要動態地建立。  
  
 新增`DECLARE_DYNCREATE`類別的.h 模組中的巨集則包含該模組中所有.cpp 模組需要存取此類別的物件。  
  
 如果`DECLARE_DYNCREATE`包含在類別宣告，然後`IMPLEMENT_DYNCREATE`必須包含在類別實作。  
  
 如需有關`DECLARE_DYNCREATE`巨集，請參閱[CObject 類別主題](../../mfc/using-cobject.md)。  
  
> [!NOTE]
>  `DECLARE_DYNCREATE`巨集包含的所有功能`DECLARE_DYNAMIC`。  
  
### <a name="example"></a>範例  
 請參閱範例[IMPLEMENT_DYNCREATE](#implement_dyncreate)。  

### <a name="requirements"></a>需求  
 **標頭：** afx.h 

##  <a name="a-namedeclareseriala--declareserial"></a><a name="declare_serial"></a>DECLARE_SERIAL  
 會產生所需的 c + + 標頭碼`CObject`-衍生可序列化的類別。  
  
```
DECLARE_SERIAL(class_name)   
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 類別的實際名稱。  
  
### <a name="remarks"></a>備註  
 序列化是檔案中寫入或讀取物件與內容的程序。  
  
 使用`DECLARE_SERIAL`巨集在.h 模組中，然後將該模組包含在所有.cpp 模組需要存取此類別的物件。  
  
 如果`DECLARE_SERIAL`包含在類別宣告，然後`IMPLEMENT_SERIAL`必須包含在類別實作。  
  
 `DECLARE_SERIAL`巨集包含的所有功能`DECLARE_DYNAMIC`和`DECLARE_DYNCREATE`。  
  
 您可以使用**AFX_API**巨集，以自動匯出`CArchive`引出運算子的類別使用`DECLARE_SERIAL`和`IMPLEMENT_SERIAL`巨集。 括號的類別宣告 （位於.h 檔） 為下列程式碼︰  
  
 [!code-cpp[NVC_MFCCObjectSample #&20;](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 如需有關`DECLARE_SERIAL`巨集，請參閱[CObject 類別主題](../../mfc/using-cobject.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCObjectSample #&21;](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]  
  
### <a name="requirements"></a>需求  
 **標頭：** afx.h 

##  <a name="a-nameimplementdynamica--implementdynamic"></a><a name="implement_dynamic"></a>您的類別  
 產生的 c + + 程式碼所需的動態`CObject`-衍生類別的執行階段存取的類別名稱和階層內的位置。  
  
```
IMPLEMENT_DYNAMIC(class_name, base_class_name)  
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 類別的實際名稱。  
  
 `base_class_name`  
 基底類別的名稱。  
  
### <a name="remarks"></a>備註  
 使用`IMPLEMENT_DYNAMIC`.cpp 模組，並連結產生的物件一次程式碼中的巨集。  
  
 如需詳細資訊，請參閱[CObject 類別主題](../../mfc/using-cobject.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCObjectSample #&2;](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]  
  
 [!code-cpp[NVC_MFCCObjectSample #&3;](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** afx.h 

##  <a name="a-nameimplementdyncreatea--implementdyncreate"></a><a name="implement_dyncreate"></a>IMPLEMENT_DYNCREATE  
 可讓物件的`CObject`-衍生類別能夠以動態方式建立在執行時使用的時間`DECLARE_DYNCREATE`巨集。  
  
```
IMPLEMENT_DYNCREATE(class_name, base_class_name)   
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 類別的實際名稱。  
  
 `base_class_name`  
 基底類別的實際名稱。  
  
### <a name="remarks"></a>備註  
 架構會建立新的物件，以動態方式，例如當它從磁碟讀取物件在序列化期間使用這項功能。 新增`IMPLEMENT_DYNCREATE`類別實作檔中的巨集。 如需詳細資訊，請參閱[CObject 類別主題](../../mfc/using-cobject.md)。  
  
 如果您使用`DECLARE_DYNCREATE`和`IMPLEMENT_DYNCREATE`巨集，然後您可以使用`RUNTIME_CLASS`巨集和`CObject::IsKindOf`在執行階段判斷物件的類別成員函式。  
  
 如果`DECLARE_DYNCREATE`包含在類別宣告，然後`IMPLEMENT_DYNCREATE`必須包含在類別實作。  
  
 請注意，此巨集定義會叫用類別的預設建構函式。 如果非一般建構函式會明確實作的類別，就必須明確地實作預設建構函式以及。 預設建構函式可以加入至類別的**私用**或**保護**成員區段，以防止從呼叫外部類別實作。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCObjectSample #&22;](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]  
  
 [!code-cpp[NVC_MFCCObjectSample #&23;](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** afx.h 

##  <a name="a-nameimplementseriala--implementserial"></a><a name="implement_serial"></a>IMPLEMENT_SERIAL  
 產生的 c + + 程式碼所需的動態`CObject`-衍生類別的執行階段存取的類別名稱和階層內的位置。  
  
```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)  
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 類別的實際名稱。  
  
 `base_class_name`  
 基底類別的名稱。  
  
 *wSchema*  
 A **UINT** 」 版本號碼"會讓還原序列化程式來識別及處理所建立的資料保存在編碼之前程式版本。 類別結構描述編號不能為 â €"1。  
  
### <a name="remarks"></a>備註  
 使用`IMPLEMENT_SERIAL`巨集在.cpp 模組，然後一次連結產生的物件程式碼。  
  
 您可以使用**AFX_API**巨集，以自動匯出`CArchive`引出運算子的類別使用`DECLARE_SERIAL`和`IMPLEMENT_SERIAL`巨集。 括號的類別宣告 （位於.h 檔） 為下列程式碼︰  
  
 [!code-cpp[NVC_MFCCObjectSample #&20;](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 如需詳細資訊，請參閱[CObject 類別主題](../../mfc/using-cobject.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCObjectSample #&24;](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** afx.h 

##  <a name="a-nameruntimeclassa--runtimeclass"></a><a name="runtime_class"></a>RUNTIME_CLASS  
 取得執行階段類別結構的 c + + 類別名稱。  
  
```
RUNTIME_CLASS(class_name)  
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 （不以引號括住） 類別的實際名稱。  
  
### <a name="remarks"></a>備註  
 `RUNTIME_CLASS`傳回的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)所指定的類別結構*class_name*。 只有`CObject`-衍生的類別宣告為具有`DECLARE_DYNAMIC`， `DECLARE_DYNCREATE`，或`DECLARE_SERIAL`會傳回指標`CRuntimeClass`結構。  
  
 如需詳細資訊，請參閱[CObject 類別主題](../../mfc/using-cobject.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCObjectSample #&25;](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** afx.h 
   
##  <a name="a-namedeclareolecreatea--declareolecreate"></a><a name="declare_olecreate"></a>DECLARE_OLECREATE  
 可讓物件的`CCmdTarget`-衍生類別能夠透過 OLE automation 建立。  
  
```
DECLARE_OLECREATE(class_name) 
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 類別的實際名稱。  
  
### <a name="remarks"></a>備註  
 這個巨集可讓其他 OLE 功能的應用程式建立此類型的物件。  
  
 新增`DECLARE_OLECREATE`類別的.h 模組中的巨集，然後包含該模組中所有.cpp 模組需要存取此類別的物件。  
  
 如果`DECLARE_OLECREATE`包含在類別宣告，然後`IMPLEMENT_OLECREATE`必須包含在類別實作。 使用類別宣告`DECLARE_OLECREATE`也必須使用`DECLARE_DYNCREATE`或`DECLARE_SERIAL`。  

### <a name="requirements"></a>需求  
 **標頭**: afxdisp.h  

##  <a name="a-nameimplementolecreatea--implementolecreate"></a><a name="implement_olecreate"></a>IMPLEMENT_OLECREATE  
 這個巨集或[IMPLEMENT_OLECREATE_FLAGS](http://msdn.microsoft.com/library/d1589f6a-5a69-4742-b07c-4c621cfd040d)必須出現在使用任何類別實作檔`DECLARE_OLECREATE`。  
  
```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)  
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 類別的實際名稱。  
  
 *external_name*  
 物件名稱公開給其他應用程式 （以引號括住）。  
  
 *l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8*  
 此類別的元件**CLSID**。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  如果您使用`IMPLEMENT_OLECREATE`，您可以根據預設，支援只有單一執行緒模型。 如果您使用`IMPLEMENT_OLECREATE_FLAGS`，您可以指定物件支援使用哪一個執行緒模型`nFlags`參數。  
  
 外部名稱是公開給其他應用程式的識別碼。 用戶端應用程式使用的外部名稱從自動化伺服器要求此類別的物件。  
  
 OLE 類別 ID 是唯一的 128 位元識別碼的物件。 它包括一個**長**、 兩個**WORD**s 和八**位元組**s 所表示的*l*， *w1*， *w2*，和*b1*透過*b8*語法描述中。 應用程式精靈和程式碼精靈視需要為您建立唯一的 OLE 類別 Id。  

### <a name="requirements"></a>需求  
 **標頭**: afxdisp.h 

## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

