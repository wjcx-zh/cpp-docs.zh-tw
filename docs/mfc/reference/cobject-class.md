---
title: "CObject 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CObject
- AFX/CObject
- AFX/CObject::CObject
- AFX/CObject::AssertValid
- AFX/CObject::Dump
- AFX/CObject::GetRuntimeClass
- AFX/CObject::IsKindOf
- AFX/CObject::IsSerializable
- AFX/CObject::Serialize
dev_langs:
- C++
helpviewer_keywords:
- base classes, MFC objects
- objects [C++], base class for MFC
- object classes
- CObject class
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
caps.latest.revision: 22
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
ms.openlocfilehash: d411b9da8618eaac57045a1db05251517422976a
ms.lasthandoff: 02/24/2017

---
# <a name="cobject-class"></a>CObject 類別
MFC 程式庫的主要基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class AFX_NOVTABLE CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CObject::CObject](#cobject)|預設建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CObject::AssertValid](#assertvalid)|會驗證此物件的完整性。|  
|[CObject::Dump](#dump)|產生此物件的診斷傾印。|  
|[CObject::GetRuntimeClass](#getruntimeclass)|傳回`CRuntimeClass`對應到此物件的類別結構。|  
|[Cobject:: Iskindof](#iskindof)|測試指定類別的物件的關聯性。|  
|[CObject::IsSerializable](#isserializable)|若要查看是否可以序列化此物件的測試。|  
|[CObject::Serialize](#serialize)|載入或儲存的物件自/至封存檔。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CObject::operator 刪除](#operator_delete)|特殊**刪除**運算子。|  
|[新 CObject::operator](#operator_new)|特殊**新**運算子。|  
  
## <a name="remarks"></a>備註  
 它可以做為程式庫類別不只是為了根例如`CFile`和`CObList`，但也為您撰寫的類別。 `CObject`提供基本的服務，包括  
  
-   序列化支援  
  
-   執行階段類別資訊  
  
-   物件的診斷輸出  
  
-   相容性的集合類別  
  
 請注意，`CObject`不支援多重繼承。 在衍生的類別只能有一個`CObject`基底類別，而且`CObject`必須是階層中最左邊。 它是所允許的不過，將結構和非- `CObject`-右手邊的多重繼承分支中衍生類別。  
  
 您將了解最大的好處，從`CObject`衍生，如果您使用的某些選擇性巨集，在您的類別實作和宣告。  
  
 第一層級巨集、 [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)和[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)，允許執行階段存取的類別名稱以及其在階層中的位置。 這項目，接著讓有意義的診斷傾印。  
  
 第二層巨集、 [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)，包括第一層級巨集的所有功能，以及可讓序列化的物件是 「 」 與 「 封存 」。  
  
 如需一般 mfc 和 c + + 類別衍生，並使用`CObject`，請參閱[使用 CObject](../../mfc/using-cobject.md)和[序列化](../../mfc/serialization-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CObject`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="assertvalid"></a>CObject::AssertValid  
 會驗證此物件的完整性。  
  
```  
virtual void AssertValid() const;  
```  
  
### <a name="remarks"></a>備註  
 `AssertValid`藉由檢查其內部狀態執行有效性檢查，此物件上。 在程式庫的偵錯版本`AssertValid`可能會判斷提示，並因此終止程式使用訊息會列出行號和檔名，判斷提示失敗的位置。  
  
 當您撰寫您自己的類別時，您應該覆寫`AssertValid`函式以提供您自己和其他使用者類別的診斷服務。 覆寫`AssertValid`通常會呼叫`AssertValid`函式之前檢查唯一衍生的類別資料成員其基底類別。  
  
 因為`AssertValid`是**const**函式，允許您在測試期間變更物件狀態。 在衍生的類別`AssertValid`函式不應該擲回例外狀況，但而是應該判斷提示是否偵測到無效的物件資料。  
  
 「 有效 」 的定義取決於物件的類別。 因此，函式應該執行 「 淺層檢查 」。 也就是說，如果物件包含其他物件的指標，它應該檢查以查看是否指標不是 null，但它不應該在執行測試的指標所參考之物件的有效性。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)的清單`CAge`用在所有的類別`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&7;](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]  
  
 如需其他範例，請參閱[AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects)。  
  
##  <a name="cobject"></a>CObject::CObject  
 這些函式是標準`CObject`建構函式。  
  
```  
CObject();  
CObject(const CObject& objectSrc);
```  
  
### <a name="parameters"></a>參數  
 *objectSrc*  
 另一個參考`CObject`  
  
### <a name="remarks"></a>備註  
 預設版本會自動呼叫您的衍生類別的建構函式。  
  
 如果您的類別是可序列化 (其中包含`IMPLEMENT_SERIAL`巨集)，則您必須將類別宣告中的預設建構函式 （不含引數的建構函式）。 如果您不需要的預設建構函式，宣告私用或受保護的 「 空 」 的建構函式。 如需詳細資訊，請參閱[使用 CObject](../../mfc/using-cobject.md)。  
  
 標準 c + + 預設類別複製建構函式會依成員複本。 私用的存在`CObject`複製建構函式可以保證編譯器錯誤訊息，如果類別的複製建構函式所需但無法使用。 因此，如果您的類別需要這項功能，您必須提供複製建構函式。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)的清單`CAge`類別用於`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&8;](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]  
  
##  <a name="dump"></a>CObject::Dump  
 您的物件內容傾印[CDumpContext](../../mfc/reference/cdumpcontext-class.md)物件。  
  
```  
virtual void Dump(CDumpContext& dc) const;  
```  
  
### <a name="parameters"></a>參數  
 `dc`  
 診斷傾印內容來傾印，通常`afxDump`。  
  
### <a name="remarks"></a>備註  
 當您撰寫您自己的類別時，您應該覆寫`Dump`函式以提供您自己和其他使用者類別的診斷服務。 覆寫`Dump`通常會呼叫`Dump`函式前先列印唯一衍生的類別資料成員其基底類別。 `CObject::Dump`列印類別名稱，如果您的類別使用`IMPLEMENT_DYNAMIC`或`IMPLEMENT_SERIAL`巨集。  
  
> [!NOTE]
>  您`Dump`函式應該不會列印新行字元，其輸出的結尾。  
  
 `Dump`呼叫意義只有在偵錯版本的 Mfc 程式庫。 呼叫、 函式宣告和函式的實作應該括號**#ifdef _DEBUG** /  `#endif`條件式編譯陳述式。  
  
 由於`Dump`是**const**函式，允許您將物件狀態變更期間傾印。  
  
 [CDumpContext 插入 (<)> </)> ](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt)呼叫`Dump`時`CObject`插入指標。  
  
 `Dump`允許的物件只有 「 非循環 」 傾印。 您可以傾印物件的清單，比方說，但如果其中一個物件是清單本身，最後會超出堆疊。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)的清單`CAge`用在所有的類別`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&9;](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]  
  
##  <a name="getruntimeclass"></a>CObject::GetRuntimeClass  
 傳回`CRuntimeClass`對應到此物件的類別結構。  
  
```  
virtual CRuntimeClass* GetRuntimeClass() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構對應至物件的類別; 永遠不會**NULL**。  
  
### <a name="remarks"></a>備註  
 有一個`CRuntimeClass`每個結構`CObject`-衍生的類別。 結構成員如下所示︰  
  
- **LPCSTR m_lpszClassName** null 結束的字串，包含 ASCII 的類別名稱。  
  
- **int m_nObjectSize**物件，以位元組為單位的大小。 如果物件具有資料成員指向已配置的記憶體，不包含該記憶體的大小。  
  
- **UINT m_wSchema**結構描述編號 (– 1，不可序列化的類別)。 請參閱[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)巨集的結構描述編號說明。  
  
- **CObject\* (pascal 命名法\*m_pfnCreateObject) （)**建立您的類別物件的預設建構函式的函式指標 (有效前提是此類別支援動態建立; 否則會傳回**NULL**)。  
  
- **CRuntimeClass\* (pascal 命名法\*m_pfn_GetBaseClass) （)**如果您的應用程式動態連結至 MFC 的 AFXDLL 版本中，函式的指標，會傳回`CRuntimeClass`結構的基底類別。  
  
- **CRuntimeClass\* m_pBaseClass**如果您的應用程式以靜態方式連結至 MFC，指標`CRuntimeClass`結構的基底類別。  
  
 此函式需要使用[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)， [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)，或[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)類別實作中的巨集。 否則您會收到不正確的結果。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)的清單`CAge`用在所有的類別`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&10;](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]  
  
##  <a name="iskindof"></a>Cobject:: Iskindof  
 測試指定類別的物件的關聯性。  
  
```  
BOOL IsKindOf(const CRuntimeClass* pClass) const;  
```  
  
### <a name="parameters"></a>參數  
 `pClass`  
 指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構與相關聯程式`CObject`-衍生的類別。  
  
### <a name="return-value"></a>傳回值  
 非零，如果物件對應到類別;否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式會測試`pClass`（1） 它是指定類別的物件，或 （2） 它是衍生自指定類別的類別物件。 此函數僅適用於類別宣告為具有[DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)， [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)，或[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)巨集。  
  
 因為它會失去 c + + 多型功能請勿廣泛使用此函式。 改為使用虛擬函式。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)的清單`CAge`用在所有的類別`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&11;](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]  
  
##  <a name="isserializable"></a>CObject::IsSerializable  
 測試是否此物件會進行序列化。  
  
```  
BOOL IsSerializable() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果這個物件可以序列化。否則為 0。  
  
### <a name="remarks"></a>備註  
 要序列化的類別，它的宣告必須包含[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)巨集，以及實作必須包含[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)巨集。  
  
> [!NOTE]
>  不會覆寫這個函式。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)的清單`CAge`用在所有的類別`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&12;](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]  
  
##  <a name="operator_delete"></a>CObject::operator 刪除  
 發行版本的程式庫中，運算子**刪除**釋放運算子所配置的記憶體**新**。  
  
```  
void PASCAL operator delete(void* p);

 
void PASCAL operator delete(
    void* p,
    void* pPlace);

 
void PASCAL operator delete(
    void* p,  
    LPCSTR lpszFileName,  
    int nLine);
```  
  
### <a name="remarks"></a>備註  
 在偵錯版本中，運算子**刪除**參與設計來偵測記憶體流失配置監視配置。  
  
 如果您使用這行程式碼  
  
 [!code-cpp[NVC_MFCCObjectSample #&14;](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 將您的實作中的任何之前。CPP 檔案，然後第三個版本的**刪除**將會使用，供之後的報表配置的區塊中儲存的檔名和行號。 您不需要擔心提供額外的參數。巨集會為您處理。  
  
 即使您不使用`DEBUG_NEW`在偵錯模式中，您仍會收到流失偵測，但沒有來源檔案行號報告上面所述。  
  
 如果您覆寫運算子**新**和**刪除**，違反此診斷功能。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)的清單`CAge`類別用於`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&15;](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]  
  
##  <a name="operator_new"></a>新 CObject::operator  
 發行版本的程式庫中，運算子**新**執行最佳的記憶體配置方式類似`malloc`。  
  
```  
void* PASCAL operator new(size_t nSize);  
void* PASCAL operator new(size_t, void* p);

 
void* PASCAL operator new(
    size_t nSize,  
    LPCSTR lpszFileName,  
    int nLine);
```  
  
### <a name="remarks"></a>備註  
 在偵錯版本中，運算子**新**參與設計來偵測記憶體流失配置監視配置。  
  
 如果您使用這行程式碼  
  
 [!code-cpp[NVC_MFCCObjectSample #&14;](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 將您的實作中的任何之前。CPP 檔案，然後第二版**新**將會使用，供之後的報表配置的區塊中儲存的檔名和行號。 您不需要擔心提供額外的參數。巨集會為您處理。  
  
 即使您不使用`DEBUG_NEW`在偵錯模式中，您仍會收到流失偵測，但沒有來源檔案行號報告上面所述。  
  
> [!NOTE]
>  如果您覆寫這個運算子，您也必須覆寫**刪除**。 不使用標準程式庫**_new_handler**函式。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)的清單`CAge`類別用於`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&16;](../../mfc/codesnippet/cpp/cobject-class_9.h)]  
  
##  <a name="serialize"></a>CObject::Serialize  
 從封存中讀取或寫入此物件。  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
 `ar`  
 A`CArchive`来序列化或從物件。  
  
### <a name="remarks"></a>備註  
 您必須覆寫`Serialize`針對每個您想要序列化的類別。 覆寫`Serialize`必須先呼叫`Serialize`函式，其基底類別。  
  
 您也必須使用[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)巨集，在類別宣告中，而且您必須使用[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)實作中的巨集。  
  
 使用[CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading)或[CArchive::IsStoring](../../mfc/reference/carchive-class.md#isstoring)來判斷是否載入或儲存封存。  
  
 `Serialize`會呼叫[CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject)和[CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject)。 這些函式相關聯`CArchive`插入運算子 ( ** < \< **) 和擷取運算子 ( ** >> **)。  
  
 如需序列化的範例，請參閱文章[序列化︰ 序列化物件](../../mfc/serialization-serializing-an-object.md)。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)的清單`CAge`用在所有的類別`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&13;](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)




