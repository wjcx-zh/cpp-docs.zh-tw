---
title: CObject 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- CObject [MFC], CObject
- CObject [MFC], AssertValid
- CObject [MFC], Dump
- CObject [MFC], GetRuntimeClass
- CObject [MFC], IsKindOf
- CObject [MFC], IsSerializable
- CObject [MFC], Serialize
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
ms.openlocfilehash: ce745e0717e36a3c9acb5323d04545c59750add7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222897"
---
# <a name="cobject-class"></a>CObject 類別

MFC 程式庫的主要基底類別。

## <a name="syntax"></a>語法

```
class AFX_NOVTABLE CObject
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|說明|
|----------|-----------------|
|[CObject：： CObject](#cobject)|預設建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CObject：： AssertValid](#assertvalid)|驗證這個物件的完整性。|
|[CObject：:D ump](#dump)|產生此物件的診斷傾印。|
|[CObject：： GetRuntimeClass](#getruntimeclass)|傳回 `CRuntimeClass` 對應至這個物件之類別的結構。|
|[CObject：： IsKindOf](#iskindof)|測試這個物件與指定類別的關聯性。|
|[CObject：： IsSerializable](#isserializable)|測試此物件是否可以序列化。|
|[CObject：：序列化](#serialize)|從封存載入或儲存物件。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CObject：： operator delete](#operator_delete)|特殊 **`delete`** 運算子。|
|[CObject：： operator new](#operator_new)|特殊 **`new`** 運算子。|

## <a name="remarks"></a>備註

它不只會作為程式庫類別（例如和）的根，也會做為 `CFile` `CObList` 您撰寫的類別。 `CObject`提供基本服務，包括

- 序列化支援

- 執行時間類別資訊

- 物件診斷輸出

- 與集合類別的相容性

請注意，不 `CObject` 支援多重繼承。 您的衍生類別只能有一個 `CObject` 基類，且該類別 `CObject` 必須在階層中最左邊。 不過，它可以 `CObject` 在右手邊的多重繼承分支中具有結構和非衍生的類別。

`CObject`如果您在類別的執行和宣告中使用一些選擇性宏，您將會發現衍生的主要優點。

第一層宏[DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)和[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)允許執行時間存取類別名稱及其在階層中的位置。 接著，這會允許有意義的診斷傾印。

第二層宏[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)包含第一層宏的所有功能，而且可讓物件「序列化」到「封存」。

如需有關在一般和使用中衍生 Microsoft Foundation 類別和 c + + 類別的詳細資訊 `CObject` ，請參閱[使用 CObject](../../mfc/using-cobject.md)和[序列化](../../mfc/serialization-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CObject`

## <a name="requirements"></a>需求

**標頭：** afx。h

## <a name="cobjectassertvalid"></a><a name="assertvalid"></a>CObject：： AssertValid

驗證這個物件的完整性。

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>備註

`AssertValid`藉由檢查此物件的內部狀態來執行有效性檢查。 在程式庫的偵錯工具版本中， `AssertValid` 可能會判斷提示，因此會以一則訊息來終止程式，其中會列出判斷提示失敗的行號和檔案名。

當您撰寫自己的類別時，您應該覆寫函式，為 `AssertValid` 您自己和類別的其他使用者提供診斷服務。 覆寫 `AssertValid` 通常會在 `AssertValid` 檢查衍生類別的唯一資料成員之前，呼叫其基類的函式。

因為 `AssertValid` 是函式 **`const`** ，所以不允許您在測試期間變更物件狀態。 您自己的衍生類別函式 `AssertValid` 不應該擲回例外狀況，而是應該判斷提示是否偵測到不正確物件資料。

"有效性" 的定義取決於物件的類別。 做為規則，函數應該執行「淺層檢查」。 也就是說，如果物件包含其他物件的指標，則應該檢查指標是否不是 null，但不應對指標所參考的物件執行有效性測試。

### <a name="example"></a>範例

如需所有範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

如需其他範例，請參閱[AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects)。

## <a name="cobjectcobject"></a><a name="cobject"></a>CObject：： CObject

這些函式是標準的 `CObject` 函數。

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>參數

*objectSrc*<br/>
另一個的參考`CObject`

### <a name="remarks"></a>備註

預設版本會由衍生類別的「函式」自動呼叫。

如果您的類別是可序列化的（它會併入 IMPLEMENT_SERIAL 宏），則您的類別宣告中必須有預設的處理常式（不含引數的函式）。 如果您不需要預設的處理函式，請宣告私用或受保護的「空白」的函式。 如需詳細資訊，請參閱[使用 CObject](../../mfc/using-cobject.md)。

Standard c + + 預設類別複製的函式會進行成員複製。 `CObject`如果需要類別的複製構造函式，但無法使用，則私用複製函式的存在可保證編譯器錯誤訊息。 因此，如果您的類別需要這項功能，則必須提供複製的函式。

### <a name="example"></a>範例

如需範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

## <a name="cobjectdump"></a><a name="dump"></a>CObject：:D ump

將物件的內容傾印到[CDumpCoNtext](../../mfc/reference/cdumpcontext-class.md)物件。

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>參數

*dc*<br/>
用於傾印的診斷轉儲內容，通常為 `afxDump` 。

### <a name="remarks"></a>備註

當您撰寫自己的類別時，您應該覆寫函式，為 `Dump` 您自己和類別的其他使用者提供診斷服務。 覆寫的 `Dump` 通常會先呼叫其基類的函式， `Dump` 再列印衍生類別唯一的資料成員。 `CObject::Dump`如果您的類別使用或 IMPLEMENT_SERIAL 宏，則列印類別名稱 `IMPLEMENT_DYNAMIC` 。

> [!NOTE]
> 您的函式 `Dump` 不應在其輸出結尾列印分行符號。

`Dump`只有在 MFC 程式庫的 Debug 版本中，呼叫才有意義。 您應該使用條件式編譯的 **#ifdef _DEBUG** /  語句來括住呼叫、函式宣告和函數執行 `#endif` 。

因為 `Dump` 是函式 **`const`** ，所以不允許您在傾印期間變更物件狀態。

插入指標時， [CDumpCoNtext 插入（<<）運算子](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) `Dump` 會呼叫 `CObject` 。

`Dump`只允許「非迴圈」的物件傾印。 例如，您可以傾印物件清單，但如果其中一個物件是清單本身，您最後就會溢位堆疊。

### <a name="example"></a>範例

如需所有範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

## <a name="cobjectgetruntimeclass"></a><a name="getruntimeclass"></a>CObject：： GetRuntimeClass

傳回 `CRuntimeClass` 對應至這個物件之類別的結構。

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>傳回值

對應至這個物件之類別的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構指標。永不**為 Null**。

### <a name="remarks"></a>備註

`CRuntimeClass`每個衍生類別都有一個結構 `CObject` 。 結構成員如下所示：

- **LPCSTR m_lpszClassName**包含 ASCII 類別名稱的以 null 終止的字串。

- **int m_nObjectSize**物件的大小（以位元組為單位）。 如果物件的資料成員指向已配置的記憶體，則不會包含該記憶體的大小。

- **UINT m_wSchema**架構編號（不可序列化類別的-1）。 如需架構編號的描述，請參閱[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

- **CObject \* （PASCAL \* m_pfnCreateObject）（）** 函式指標，適用于建立類別物件的預設函式（只有在類別支援動態建立時才有效，否則會傳回**Null**）。

- **CRuntimeClass \* （PASCAL \* m_pfn_GetBaseClass）（）** 如果您的應用程式是以動態方式連結至 MFC 的 AFXDLL 版本，則為函式的指標，該函式會傳回 `CRuntimeClass` 基類的結構。

- **CRuntimeClass \* m_pBaseClass** ，如果您的應用程式以靜態方式連結至 MFC，則為 `CRuntimeClass` 基類結構的指標。

此函式需要在類別實作用中使用[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)、 [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)或[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。 否則，您會得到不正確的結果。

### <a name="example"></a>範例

如需所有範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

## <a name="cobjectiskindof"></a><a name="iskindof"></a>CObject：： IsKindOf

測試這個物件與指定類別的關聯性。

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>參數

*pClass*<br/>
與衍生類別相關聯之[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構的指標 `CObject` 。

### <a name="return-value"></a>傳回值

如果物件對應至類別，則為非零。否則為0。

### <a name="remarks"></a>備註

此函式會測試*pClass* ，以查看（1）它是否為指定類別的物件，或（2）它是否為衍生自指定類別的類別物件。 此函式僅適用于使用[DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)、 [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)或[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏所宣告的類別。

請勿廣泛使用此函式，因為它會破壞 c + + 多型的功能。 請改用虛擬函式。

### <a name="example"></a>範例

如需所有範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

## <a name="cobjectisserializable"></a><a name="isserializable"></a>CObject：： IsSerializable

測試這個物件是否符合序列化的資格。

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>傳回值

如果這個物件可以序列化，則為非零。否則為0。

### <a name="remarks"></a>備註

若要讓類別成為可序列化的，其宣告必須包含[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏，而且該實作為必須包含[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

> [!NOTE]
> 不要覆寫此函數。

### <a name="example"></a>範例

如需所有範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

## <a name="cobjectoperator-delete"></a><a name="operator_delete"></a>CObject：： operator delete

針對程式庫的發行版本，運算子會 **`delete`** 釋出由運算子所配置的記憶體 **`new`** 。

```cpp
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

在 Debug 版本中，運算子會 **`delete`** 參與專為偵測記憶體流失而設計的配置監視配置。

如果您使用程式程式碼

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

在中的任何實作為之前。然後，將會使用的第三個版本 **`delete`** ，將檔案名和行號儲存在配置的區塊中，以供日後報告之用。 您不需要擔心提供額外的參數;宏會替您負責。

即使您未在 [偵錯工具] 模式中使用 DEBUG_NEW，仍然會取得流失偵測，但不會有上述的來源檔案行號報告。

如果您覆寫運算子 **`new`** 和 **`delete`** ，則會要略過此診斷功能。

### <a name="example"></a>範例

如需範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

## <a name="cobjectoperator-new"></a><a name="operator_new"></a>CObject：： operator new

針對程式庫的發行版本，運算子會 **`new`** 以類似的方式執行最佳的記憶體配置 `malloc` 。

```cpp
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>備註

在 Debug 版本中，運算子會 **`new`** 參與專為偵測記憶體流失而設計的配置監視配置。

如果您使用程式程式碼

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

在中的任何實作為之前。然後，將會使用的第二個版本 **`new`** ，將檔案名和行號儲存在配置的區塊中，以供日後報告之用。 您不需要擔心提供額外的參數;宏會替您負責。

即使您未在 [偵錯工具] 模式中使用 DEBUG_NEW，仍然會取得流失偵測，但不會有上述的來源檔案行號報告。

> [!NOTE]
> 如果您覆寫這個運算子，您也必須覆寫 **`delete`** 。 請勿使用標準程式庫 `_new_handler` 函數。

### <a name="example"></a>範例

如需範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

## <a name="cobjectserialize"></a><a name="serialize"></a>CObject：：序列化

從封存中讀取或寫入此物件。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
要在其中 `CArchive` 序列化的物件。

### <a name="remarks"></a>備註

您必須覆寫 `Serialize` 您想要序列化的每個類別。 覆寫的 `Serialize` 必須先呼叫 `Serialize` 其基類的函式。

您也必須在類別宣告中使用[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏，而且您必須在執行中使用[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

使用[CArchive：： IsLoading](../../mfc/reference/carchive-class.md#isloading)或[CArchive：： IsStoring](../../mfc/reference/carchive-class.md#isstoring)來判斷封存是否正在載入或儲存。

`Serialize`由[CArchive：： ReadObject](../../mfc/reference/carchive-class.md#readobject)和[Carchive：： WriteObject](../../mfc/reference/carchive-class.md#writeobject)呼叫。 這些函數與 `CArchive` 插入運算子（）相關聯 **<\<**) and extraction operator ( **>>** 。

如需序列化範例，請參閱[序列化：序列化物件一](../../mfc/serialization-serializing-an-object.md)文。

### <a name="example"></a>範例

如需所有範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)
