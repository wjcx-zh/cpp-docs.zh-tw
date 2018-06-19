---
title: CObject 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CObject [MFC], CObject
- CObject [MFC], AssertValid
- CObject [MFC], Dump
- CObject [MFC], GetRuntimeClass
- CObject [MFC], IsKindOf
- CObject [MFC], IsSerializable
- CObject [MFC], Serialize
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38c27d2fa0e04770bae69901e1164da84c2186ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377236"
---
# <a name="cobject-class"></a>CObject 類別
MFC 程式庫的主要基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class AFX_NOVTABLE CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CObject::CObject](#cobject)|預設建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CObject::AssertValid](#assertvalid)|會驗證此物件的完整性。|  
|[CObject::Dump](#dump)|產生此物件的診斷傾印。|  
|[CObject::GetRuntimeClass](#getruntimeclass)|傳回`CRuntimeClass`結構對應至這個物件的類別。|  
|[Cobject:: Iskindof](#iskindof)|測試指定類別的這個物件的關聯性。|  
|[CObject::IsSerializable](#isserializable)|若要查看是否可以序列化此物件的測試。|  
|[Cobject:: Serialize](#serialize)|載入或儲存物件自/至封存。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CObject::operator 刪除](#operator_delete)|特殊**刪除**運算子。|  
|[新的 CObject::operator](#operator_new)|特殊**新**運算子。|  
  
## <a name="remarks"></a>備註  
 它可以做不僅可針對程式庫類別根例如`CFile`和`CObList`，而且還可讓您撰寫的類別。 `CObject` 提供基本的服務，包括  
  
-   序列化支援  
  
-   執行階段類別資訊  
  
-   物件的診斷輸出  
  
-   相容性的集合類別  
  
 請注意，`CObject`不支援多重繼承。 在衍生的類別只能有一個`CObject`基底類別，而且`CObject`必須是階層中最左邊。 它是所允許的不過，讓結構和非- `CObject`-衍生的右手邊的多重繼承分支中的類別。  
  
 您會發現從主要的優點`CObject`衍生，如果您使用一些在您的類別實作和宣告中的選擇性巨集。  
  
 第一層巨集[DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)和[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)，允許執行階段存取的類別名稱和其在階層中的位置。 這項目，接著，可讓有意義的診斷傾印。  
  
 第二個層級巨集[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)，包含第一層巨集的所有功能，以及它們可讓物件 「 序列化 」 與 「 封存 」。  
  
 如需一般 Microsoft Foundation 類別和 c + + 類別衍生，並使用`CObject`，請參閱[使用 CObject](../../mfc/using-cobject.md)和[序列化](../../mfc/serialization-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CObject`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="assertvalid"></a>  CObject::AssertValid  
 會驗證此物件的完整性。  
  
```  
virtual void AssertValid() const;  
```  
  
### <a name="remarks"></a>備註  
 `AssertValid` 正在檢查其內部狀態，以執行有效性檢查，此物件上。 在 程式庫的偵錯版本`AssertValid`可能會判斷提示，並因此終止程式使用訊息會列出行號和檔名，判斷提示失敗的位置。  
  
 當您撰寫您自己的類別時，您應該覆寫`AssertValid`函式，以提供診斷服務為自己和您類別的其他使用者。 覆寫`AssertValid`通常會呼叫`AssertValid`之前檢查資料成員的唯一衍生的類別及其基底類別的函式。  
  
 因為`AssertValid`是**const**函式，您不允許測試期間變更物件狀態。 在衍生的類別`AssertValid`函式應該不會擲回例外狀況，但而是應該判斷提示是否偵測到無效的物件資料。  
  
 「 有效 」 的定義取決於物件的類別。 因此，函式應該執行 「 淺層檢查 」。 也就是說，如果物件包含其他物件的指標，它應該檢查是否指標不是 null，但它不應該執行的有效性測試指標所參考的物件。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如的清單`CAge`用在所有的類別`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]  
  
 如需其他範例，請參閱[AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects)。  
  
##  <a name="cobject"></a>  CObject::CObject  
 這些函式是標準`CObject`建構函式。  
  
```  
CObject();  
CObject(const CObject& objectSrc);
```  
  
### <a name="parameters"></a>參數  
 *objectSrc*  
 另一個參考 `CObject`  
  
### <a name="remarks"></a>備註  
 預設版本會自動呼叫您的衍生類別的建構函式。  
  
 如果您的類別是可序列化 (它會合併`IMPLEMENT_SERIAL`巨集)，則必須在類別宣告中有預設建構函式 （不含引數的建構函式）。 如果您不需要預設建構函式，宣告私用或受保護的"empty"的建構函式。 如需詳細資訊，請參閱[使用 CObject](../../mfc/using-cobject.md)。  
  
 標準 c + + 預設類別複製建構函式會依成員複本。 私用與否`CObject`複製建構函式可以保證編譯器錯誤訊息，如果類別的複製建構函式所需但無法使用。 因此，如果您的類別需要這項功能，您必須提供的複製建構函式。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如的清單`CAge`類別用於`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]  
  
##  <a name="dump"></a>  CObject::Dump  
 傾印物件的內容[CDumpContext](../../mfc/reference/cdumpcontext-class.md)物件。  
  
```  
virtual void Dump(CDumpContext& dc) const;  
```  
  
### <a name="parameters"></a>參數  
 `dc`  
 傾印，通常的診斷傾印內容`afxDump`。  
  
### <a name="remarks"></a>備註  
 當您撰寫您自己的類別時，您應該覆寫`Dump`函式，以提供診斷服務為自己和您類別的其他使用者。 覆寫`Dump`通常會呼叫`Dump`其基底類別，然後再列印唯一衍生的類別資料成員的函式。 `CObject::Dump` 列印類別名稱，如果您的類別使用`IMPLEMENT_DYNAMIC`或`IMPLEMENT_SERIAL`巨集。  
  
> [!NOTE]
>  您`Dump`函式應該不會列印新行字元，其輸出的結尾。  
  
 `Dump` 呼叫只會在合理 Mfc 程式庫的偵錯版本。 您應該呼叫、 函式宣告和函式實作與括號 **#ifdef _DEBUG** /  `#endif`條件式編譯陳述式。  
  
 因為`Dump`是**const**函式，您不允許變更物件狀態在傾印。  
  
 [CDumpContext 插入 (<<) 運算子](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt)呼叫`Dump`時`CObject`插入指標。  
  
 `Dump` 允許的物件只有 「 非循環 」 傾印。 您可以傾印物件的清單，例如，但如果其中一個物件本身的清單，您將最終產生堆疊溢位。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如的清單`CAge`用在所有的類別`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]  
  
##  <a name="getruntimeclass"></a>  CObject::GetRuntimeClass  
 傳回`CRuntimeClass`結構對應至這個物件的類別。  
  
```  
virtual CRuntimeClass* GetRuntimeClass() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構對應到此物件的類別; 永遠不會**NULL**。  
  
### <a name="remarks"></a>備註  
 有一個`CRuntimeClass`每個結構`CObject`-衍生的類別。 結構成員如下所示：  
  
- **LPCSTR m_lpszClassName** null 結束的字串，包含 ASCII 的類別名稱。  
  
- **int m_nObjectSize**物件，以位元組為單位的大小。 如果物件具有資料成員會指向配置的記憶體，不包含該記憶體的大小。  
  
- **UINT m_wSchema**結構描述編號 (-1，不可序列化的類別)。 請參閱[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)巨集的結構描述編號說明。  
  
- **CObject\* (依照 pascal 命名法\*m_pfnCreateObject) > （)** 建立您的類別物件的預設建構函式的函式指標 (有效前提是此類別支援動態建立; 否則會傳回**NULL**).  
  
- **CRuntimeClass\* (依照 pascal 命名法\*m_pfn_GetBaseClass) > （)** 如果您的應用程式動態連結至 MFC 的 AFXDLL 版本中，函式的指標，會傳回`CRuntimeClass`結構的基底類別。  
  
- **CRuntimeClass\* m_pBaseClass**如果您的應用程式以靜態方式連結至 MFC，指標`CRuntimeClass`結構的基底類別。  
  
 此函式需要使用[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)， [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)，或[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)類別實作中的巨集。 否則您會收到不正確的結果。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如的清單`CAge`用在所有的類別`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]  
  
##  <a name="iskindof"></a>  Cobject:: Iskindof  
 測試指定類別的這個物件的關聯性。  
  
```  
BOOL IsKindOf(const CRuntimeClass* pClass) const;  
```  
  
### <a name="parameters"></a>參數  
 `pClass`  
 指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構與相關聯您`CObject`-衍生的類別。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果物件會對應至類別。否則便是 0。  
  
### <a name="remarks"></a>備註  
 此函式會測試`pClass`檢查 （1） 它已指定類別的物件或 （2） 它已從指定的類別衍生的類別物件。 此函式僅適用於以宣告的類別[DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)， [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)，或[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)巨集。  
  
 因為它會失去 c + + 多型功能請勿廣泛使用此函式。 請改用虛擬函式。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如的清單`CAge`用在所有的類別`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]  
  
##  <a name="isserializable"></a>  CObject::IsSerializable  
 測試是否適合序列化此物件。  
  
```  
BOOL IsSerializable() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果這個物件可以序列化; 非零，否則便是 0。  
  
### <a name="remarks"></a>備註  
 是可序列化的類別，其宣告必須包含[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)巨集，以及實作必須包含[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)巨集。  
  
> [!NOTE]
>  不會覆寫這個函式。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如的清單`CAge`用在所有的類別`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]  
  
##  <a name="operator_delete"></a>  CObject::operator 刪除  
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
 在偵錯版本中，運算子**刪除**參與設計用來偵測記憶體流失配置監視配置。  
  
 如果您使用的一行程式碼  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 將您的實作中的任何之前。CPP 檔案，然後第三個版本的**刪除**將會使用，供之後的報表配置的區塊中儲存的檔名和行號。 您不必擔心提供額外的參數。巨集會自動為您。  
  
 即使您未使用`DEBUG_NEW`在偵錯模式中，您仍可以獲得流失偵測，但沒有來源檔案行號報告上面所述。  
  
 如果您覆寫運算子**新**和**刪除**，審查此診斷功能。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如的清單`CAge`類別用於`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]  
  
##  <a name="operator_new"></a>  新的 CObject::operator  
 發行版本的程式庫中，運算子**新**類似的方式執行最佳的記憶體配置`malloc`。  
  
```  
void* PASCAL operator new(size_t nSize);  
void* PASCAL operator new(size_t, void* p);

 
void* PASCAL operator new(
    size_t nSize,  
    LPCSTR lpszFileName,  
    int nLine);
```  
  
### <a name="remarks"></a>備註  
 在偵錯版本中，運算子**新**參與設計用來偵測記憶體流失配置監視配置。  
  
 如果您使用的一行程式碼  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 將您的實作中的任何之前。CPP 檔案，然後第二個版本的**新**將會使用，供之後的報表配置的區塊中儲存的檔名和行號。 您不必擔心提供額外的參數。巨集會自動為您。  
  
 即使您未使用`DEBUG_NEW`在偵錯模式中，您仍可以獲得流失偵測，但沒有來源檔案行號報告上面所述。  
  
> [!NOTE]
>  如果您覆寫此運算子，您也必須覆寫**刪除**。 不使用標準程式庫 **_new_handler**函式。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如的清單`CAge`類別用於`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]  
  
##  <a name="serialize"></a>  Cobject:: Serialize  
 從封存中讀取或寫入此物件。  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
 `ar`  
 A`CArchive`往或來自序列化的物件。  
  
### <a name="remarks"></a>備註  
 您必須覆寫`Serialize`針對每個您想要序列化的類別。 覆寫`Serialize`必須先呼叫`Serialize`函式，其基底類別。  
  
 您也必須使用[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)巨集，在類別宣告中，而且您必須使用[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)實作中的巨集。  
  
 使用[CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading)或[CArchive::IsStoring](../../mfc/reference/carchive-class.md#isstoring)判斷封存是否載入或儲存。  
  
 `Serialize` 會呼叫[CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject)和[CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject)。 這些函式相關聯`CArchive`插入運算子 ( **< \<**) 和擷取運算子 ( **>>**)。  
  
 如需序列化的範例，請參閱文章[序列化： 序列化物件](../../mfc/serialization-serializing-an-object.md)。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如的清單`CAge`用在所有的類別`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)



