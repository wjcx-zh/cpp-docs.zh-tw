---
title: CObject 類別 |Microsoft Docs
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
ms.openlocfilehash: ccbfc00af51c3327b86386905fb7571f5cbf41fc
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757903"
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
|[CObject::Dump](#dump)|會產生此物件的診斷傾印。|  
|[CObject::GetRuntimeClass](#getruntimeclass)|傳回`CRuntimeClass`結構，其對應至這個物件的類別。|  
|[Cobject:: Iskindof](#iskindof)|測試指定類別的這個物件的關聯性。|  
|[CObject::IsSerializable](#isserializable)|若要查看是否可以序列化此物件的測試。|  
|[Cobject:: Serialize](#serialize)|載入或儲存的物件，或將封存檔。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CObject::operator delete](#operator_delete)|特殊**刪除**運算子。|  
|[新的 CObject::operator](#operator_new)|特殊**新**運算子。|  
  
## <a name="remarks"></a>備註  
 它可以做為不僅類別庫的根目錄這類`CFile`和`CObList`，但也為您撰寫的類別。 `CObject` 提供基本的服務，包括  
  
-   序列化支援  
  
-   執行階段類別資訊  
  
-   物件的診斷輸出  
  
-   集合類別與相容性  
  
 請注意，`CObject`不支援多重繼承。 在衍生的類別只能有一個`CObject`基底類別，而且`CObject`必須是階層中最左邊。 它是允許的不過，讓結構和非- `CObject`-右手邊的多重繼承分支中衍生類別。  
  
 您將了解主要的優點，從`CObject`衍生，如果您使用一些選擇性的巨集，在您的類別實作和宣告。  
  
 第一層巨集[DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)並[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)，允許執行階段存取的類別名稱及在階層中的位置。 如此一來，接著讓有意義的診斷傾印。  
  
 第二個層級巨集[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)並[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)、 包含的第一個層級巨集的所有功能，而且可以讓物件被 「 序列化 」 與 「 封存 」。  
  
 如需一般 Microsoft Foundation classes 和 c + + 類別衍生，並使用`CObject`，請參閱 <<c2> [ 使用 CObject](../../mfc/using-cobject.md)並[序列化](../../mfc/serialization-in-mfc.md)。  
  
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
 `AssertValid` 執行這個物件的驗證檢查，藉由檢查其內部狀態。 在 偵錯版本的程式庫，`AssertValid`可能會判斷提示，並因此結束程式的訊息會列出行號和檔名，判斷提示失敗的位置。  
  
 當您撰寫您自己的類別時，您應該覆寫`AssertValid`函式以提供診斷的服務，為自己和您類別的其他使用者。 覆寫`AssertValid`通常會呼叫`AssertValid`其基底類別，再檢查唯一衍生的類別資料成員的函式。  
  
 因為`AssertValid`已**const**函式，您不得在測試期間變更物件狀態。 衍生的類別`AssertValid`函式不應該擲回例外狀況，但而是應該判斷提示它們是否偵測到無效的物件資料。  
  
 「 有效 」 的定義取決於物件的類別。 因此，函式應該執行 「 淺層檢查 」。 也就是說，如果物件包含其他物件的指標，它應該檢查以查看是否指標不是 null，但它不應該執行的有效性測試指標所參考的物件。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`類別，用於所有`CObject`範例。  
  
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
 您的衍生類別的建構函式會自動呼叫的預設版本。  
  
 如果您的類別是可序列化 （它會合併 IMPLEMENT_SERIAL 巨集），則您必須將類別宣告中的預設建構函式 （不含引數的建構函式）。 如果您不需要預設建構函式，宣告私用或受保護的 「 空白 」 的建構函式。 如需詳細資訊，請參閱 <<c0> [ 使用 CObject](../../mfc/using-cobject.md)。  
  
 標準 c + + 預設類別複製建構函式會依成員複本。 私用的存在`CObject`複製建構函式可確保編譯器錯誤訊息，如果您的類別中的複製建構函式所需但無法使用。 因此，如果您的類別需要這項功能，您必須提供複製建構函式。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`類別，用於`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]  
  
##  <a name="dump"></a>  CObject::Dump  
 您的物件內容傾印[CDumpContext](../../mfc/reference/cdumpcontext-class.md)物件。  
  
```  
virtual void Dump(CDumpContext& dc) const;  
```  
  
### <a name="parameters"></a>參數  
 *dc*  
 傾印，通常的診斷傾印內容`afxDump`。  
  
### <a name="remarks"></a>備註  
 當您撰寫您自己的類別時，您應該覆寫`Dump`函式以提供診斷的服務，為自己和您類別的其他使用者。 覆寫`Dump`通常會呼叫`Dump`其基底類別，再列印唯一衍生的類別資料成員的函式。 `CObject::Dump` 列印類別名稱，如果您的類別使用`IMPLEMENT_DYNAMIC`或 IMPLEMENT_SERIAL 巨集。  
  
> [!NOTE]
>  您`Dump`函式應該不會列印其輸出的結尾新行字元。  
  
 `Dump` 呼叫的意義僅在 Microsoft Foundation 類別庫的偵錯版本。 呼叫、 函式宣告和使用的函式實作應該括住 **#ifdef _DEBUG** /  `#endif`條件式編譯的陳述式。  
  
 由於`Dump`已**const**函式，您不允許變更物件狀態期間傾印。  
  
 [CDumpContext 插入 (<<) 運算子](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt)呼叫`Dump`當`CObject`插入指標。  
  
 `Dump` 允許的物件只有 「 非循環 」 傾印。 您可以傾印物件的清單，比方說，但如果其中一個物件是清單本身，您將最終堆疊溢位。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`類別，用於所有`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]  
  
##  <a name="getruntimeclass"></a>  CObject::GetRuntimeClass  
 傳回`CRuntimeClass`結構，其對應至這個物件的類別。  
  
```  
virtual CRuntimeClass* GetRuntimeClass() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構，其對應至這個物件的類別; 從未**NULL**。  
  
### <a name="remarks"></a>備註  
 有一個`CRuntimeClass`針對每個結構`CObject`-衍生的類別。 結構成員如下所示：  
  
- **LPCSTR m_lpszClassName** null 結束的字串，包含 ASCII 的類別名稱。  
  
- **int m_nObjectSize**物件，以位元組為單位的大小。 如果物件具有資料成員指向已配置的記憶體，記憶體的大小就不會包含。  
  
- **UINT m_wSchema**結構描述編號 (-1 表示不可序列化的類別)。 請參閱[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)巨集的結構描述編號說明。  
  
- **CObject\* (依照 pascal 命名法\*m_pfnCreateObject) > （)** 建立您的類別物件的預設建構函式的函式指標 (有效前提類別支援動態建立; 否則會傳回**NULL**).  
  
- **CRuntimeClass\* (依照 pascal 命名法\*m_pfn_GetBaseClass) > （)** 如果您的應用程式動態連結至 MFC 的 AFXDLL 版本中，函式的指標，會傳回`CRuntimeClass`基底類別的結構。  
  
- **CRuntimeClass\* m_pBaseClass**如果您的應用程式以靜態方式連結至 MFC，指標`CRuntimeClass`基底類別的結構。  
  
 此函式需要使用[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)， [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)，或[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)類別實作中的巨集。 否則您會收到不正確的結果。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`類別，用於所有`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]  
  
##  <a name="iskindof"></a>  Cobject:: Iskindof  
 測試指定類別的這個物件的關聯性。  
  
```  
BOOL IsKindOf(const CRuntimeClass* pClass) const;  
```  
  
### <a name="parameters"></a>參數  
 *pClass*  
 指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)相關聯的結構您`CObject`-衍生的類別。  
  
### <a name="return-value"></a>傳回值  
 物件對應到類別; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式會測試*pClass*檢查 （1） 它是指定類別的物件或 （2） 它是衍生自指定的類別之類別的物件。 此函式僅適用於以宣告的類別[DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)， [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)，或[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)巨集。  
  
 因為它會失去 c + + 多型功能請勿廣泛使用此函式。 改為使用虛擬函式。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`類別，用於所有`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]  
  
##  <a name="isserializable"></a>  CObject::IsSerializable  
 測試是否此物件適合進行序列化。  
  
```  
BOOL IsSerializable() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果這個物件可以序列化;，非零值。否則為 0。  
  
### <a name="remarks"></a>備註  
 為可序列化的類別，其宣告必須包含[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)巨集，以及實作必須包含[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)巨集。  
  
> [!NOTE]
>  不會覆寫這個函式。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`類別，用於所有`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]  
  
##  <a name="operator_delete"></a>  CObject::operator delete  
 發行版本的程式庫，運算子**刪除**釋放運算子所配置的記憶體**新**。  
  
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
 在偵錯版本中，運算子**刪除**參與設計用來偵測記憶體流失的配置監視配置。  
  
 如果您使用的一行程式碼  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 在您實作的任何之前。CPP 檔案，然後第三個版本的**刪除**將會使用，供之後的報表配置的區塊中儲存的檔名和行號。 您不必擔心提供額外的參數;巨集會自動為您。  
  
 即使您不使用 DEBUG_NEW 偵錯模式中，您仍然可以取得流失偵測，但沒有來源檔案行號報告上面所述。  
  
 如果您覆寫運算子**新**並**刪除**，違反此診斷功能。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`類別，用於`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]  
  
##  <a name="operator_new"></a>  新的 CObject::operator  
 發行版本的程式庫，運算子**新**類似的方式執行最佳的記憶體配置`malloc`。  
  
```  
void* PASCAL operator new(size_t nSize);  
void* PASCAL operator new(size_t, void* p);

 
void* PASCAL operator new(
    size_t nSize,  
    LPCSTR lpszFileName,  
    int nLine);
```  
  
### <a name="remarks"></a>備註  
 在偵錯版本中，運算子**新**參與設計用來偵測記憶體流失的配置監視配置。  
  
 如果您使用的一行程式碼  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 在您實作的任何之前。CPP 檔案，然後第二版**新**將會使用，供之後的報表配置的區塊中儲存的檔名和行號。 您不必擔心提供額外的參數;巨集會自動為您。  
  
 即使您不使用 DEBUG_NEW 偵錯模式中，您仍然可以取得流失偵測，但沒有來源檔案行號報告上面所述。  
  
> [!NOTE]
>  如果您覆寫這位操作員，您也必須覆寫**刪除**。 不使用標準程式庫`_new_handler`函式。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`類別，用於`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]  
  
##  <a name="serialize"></a>  Cobject:: Serialize  
 從封存中讀取或寫入此物件。  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
 *ar*  
 A`CArchive`来序列化或從物件。  
  
### <a name="remarks"></a>備註  
 您必須覆寫`Serialize`針對每個您想要序列化的類別。 覆寫`Serialize`必須先呼叫`Serialize`函式，其基底類別。  
  
 您也必須使用[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)巨集，在類別宣告中，而且您必須使用[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)實作中的巨集。  
  
 使用[CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading)或是[CArchive::IsStoring](../../mfc/reference/carchive-class.md#isstoring)判斷封存是否載入或儲存。  
  
 `Serialize` 會呼叫[CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject)並[CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject)。 這些函式相關聯`CArchive`插入運算子 ( **< \<**) 和擷取運算子 ( **>>**)。  
  
 如需序列化的範例，請參閱文章[序列化： 序列化物件](../../mfc/serialization-serializing-an-object.md)。  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`類別，用於所有`CObject`範例。  
  
 [!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)



