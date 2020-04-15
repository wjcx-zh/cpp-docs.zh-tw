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
ms.openlocfilehash: cea4d09a1c1a4680b095a40fa0619287959ff4ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360417"
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
|[CObject:CObject](#cobject)|預設建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CObject::斷言有效](#assertvalid)|驗證此物件的完整性。|
|[CObject::Dump](#dump)|生成此物件的診斷轉儲。|
|[CObject:取得執行時類別](#getruntimeclass)|返回與此`CRuntimeClass`物件的類對應的結構。|
|[物件::是](#iskindof)|測試此物件與給定類的關係。|
|[CObject:可序列化](#isserializable)|測試此物件是否可以序列化。|
|[CObject:序列化](#serialize)|從/存儲從存檔的物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CObject::運算子刪除](#operator_delete)|特殊**刪除**運算子。|
|[CObject::運算元新](#operator_new)|特殊**新**操作員。|

## <a name="remarks"></a>備註

它不僅用作庫類(如`CFile``CObList`和 )的根,還充當您編寫的類的根。 `CObject`提供基本服務,包括

- 序列化支援

- 執行時類別資訊

- 物件診斷輸出

- 與集合類的相容性

請注意,`CObject`不支援多重繼承。 派生類只能有一個`CObject`基類`CObject`, 並且必須在層次結構中保留最起。 但是,在右側多繼承分支中具有結構和非`CObject`派生類是允許的。

如果在類實現和聲明中使用`CObject`一些可選宏,您將從派生中獲得主要好處。

第一級宏[(DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)和[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic))允許運行時訪問類名稱及其在層次結構中的位置。 這反過來又允許有意義的診斷轉儲。

第二級宏[(DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial))包括第一級宏的所有功能,它們使物件能夠"序列化"到"存檔"和"存檔"。

有關派生 Microsoft 基礎類別和 C++`CObject`類別以及使用的資訊,請參閱使用[CObject](../../mfc/using-cobject.md)與[序列化](../../mfc/serialization-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CObject`

## <a name="requirements"></a>需求

**標題:** afx.h

## <a name="cobjectassertvalid"></a><a name="assertvalid"></a>CObject::斷言有效

驗證此物件的完整性。

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>備註

`AssertValid`通過檢查此物件的內部狀態,對此物件執行有效性檢查。 在庫的調試版本中,`AssertValid`可能會斷言並因此終止程式,該消息列出了斷言失敗的行號和檔名。

編寫自己的類時,應重寫該`AssertValid`函數,以便為自己和類的其他使用者提供診斷服務。 重寫`AssertValid`通常調用其基`AssertValid`類 的函數,然後再檢查派生類獨有的數據成員。

由於`AssertValid`是**const**函數,因此不允許在測試期間更改物件狀態。 您自己的派生類`AssertValid`函數不應引發異常,而應斷言它們是否檢測到無效的物件數據。

"有效性"的定義取決於物件的類。 通常,該函數應執行"淺檢查"。 也就是說,如果物件包含指向其他對象的指標,則應檢查指標是否為空,但不應對指標引用的物件執行有效性測試。

### <a name="example"></a>範例

有關所有`CAge``CObject`範例中使用的類的清單,請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

有關另一個範例,請參閱[AfxDoForall 物件](diagnostic-services.md#afxdoforallobjects)。

## <a name="cobjectcobject"></a><a name="cobject"></a>CObject:CObject

這些函數是標準`CObject`構造函數。

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>參數

*物件Src*<br/>
對另一個引用`CObject`

### <a name="remarks"></a>備註

派生類的構造函數會自動調用預設版本。

如果類是可序列化的(它包含IMPLEMENT_SERIAL宏),則類聲明中必須有一個預設構造函數(沒有參數的構造函數)。 如果不需要預設構造函數,則聲明私有或受保護的"空"構造函數。 有關詳細資訊,請參閱使用[CObject](../../mfc/using-cobject.md)。

標準C++預設類複製構造函數執行逐個成員複製。 如果需要類的副本構造函數`CObject`但不可用,則私有複製構造函數的存在可確保編譯器錯誤消息。 因此,如果類需要此功能,則必須提供複製構造函數。

### <a name="example"></a>範例

`CAge`有關`CObject`範例使用的類的清單,請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

## <a name="cobjectdump"></a><a name="dump"></a>CObject::Dump

將對象的內容轉印到[CDumpContext](../../mfc/reference/cdumpcontext-class.md)物件。

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>參數

*直流*<br/>
用於轉印的診斷轉印上下文,通常`afxDump`為 。

### <a name="remarks"></a>備註

編寫自己的類時,應重寫該`Dump`函數,以便為自己和類的其他使用者提供診斷服務。 重寫`Dump`通常調用其基`Dump`類 的函數,然後再列印派生類獨有的數據成員。 `CObject::Dump`如果類使用 或 IMPLEMENT_SERIAL`IMPLEMENT_DYNAMIC`宏, 請列印類別名稱。

> [!NOTE]
> 函數`Dump`不應在其輸出結束時列印新線字元。

`Dump`僅在 Microsoft 基礎類庫的調試版本中才有意義。 應用 **#ifdef_DEBUG**/ `#endif`語句來括弧調用、函數聲明和函數實現,以便進行條件編譯。

由於`Dump`是**const**函數,因此不允許在轉儲期間更改物件狀態。

插入`CObject`指標時[,CDumpContext 插入(<<)運算子](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt)呼叫`Dump`。

`Dump`只允許"迴圈"傾倒物體。 例如,您可以轉儲物件清單,但如果其中一個對像是清單本身,則最終將溢出堆疊。

### <a name="example"></a>範例

有關所有`CAge``CObject`範例中使用的類的清單,請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

## <a name="cobjectgetruntimeclass"></a><a name="getruntimeclass"></a>CObject:取得執行時類別

返回與此`CRuntimeClass`物件的類對應的結構。

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>傳回值

指向與此物件的類對應的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構的指標;從不**NULL**。

### <a name="remarks"></a>備註

每個`CObject`派生`CRuntimeClass`類 有一個結構。 結構成員如下:

- **LPCSTR m_lpszClassName**包含 ASCII 類別名稱的 null 連接端的字串。

- **int m_nObjectSize**物件的大小(以位元組為單位)。 如果物件具有指向已分配記憶體的數據成員,則不包括該記憶體的大小。

- **UINT m_wSchema**架構編號 (- 1 表示不可序列化類別)。 有關架構編號的說明,請參閱[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

- **CObject\* \* ( PASCAL m_pfnCreateObject ))** 指向建立類物件的預設建構函數的函數指標(僅在類支援動態創建時有效;否則,返回**NULL**)。

- **CRuntimeClass\* \* ( PASCAL m_pfn_GetBaseClass )( )** 如果應用程式動態連結到 MFC 的`CRuntimeClass`AFXDLL 版本,則指向返回 基質結構的函數的指標。

- **CRuntimeClass\* m_pBaseClass**如果應用程式靜態連結到 MFC,則`CRuntimeClass`指向基類 結構的指標。

此函數要求在類實現中使用[IMPLEMENT_DYNAMIC、IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dynamic)或[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。 否則,您將獲得不正確的結果。

### <a name="example"></a>範例

有關所有`CAge``CObject`範例中使用的類的清單,請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

## <a name="cobjectiskindof"></a><a name="iskindof"></a>物件::是

測試此物件與給定類的關係。

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>參數

*pClass*<br/>
指向與派生類關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構`CObject`的指標。

### <a name="return-value"></a>傳回值

如果對象對應於類,則非零;否則 0。

### <a name="remarks"></a>備註

此函數測試*pClass*以查看它是指定類的物件,還是 (2) 它是派生自指定類的類的物件。 此函數僅適用於使用[DECLARE_DYNAMIC、DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dynamic)或[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏[DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)聲明的類。

不要廣泛使用此函數,因為它會破壞C++多態性特徵。 改用虛擬函數。

### <a name="example"></a>範例

有關所有`CAge``CObject`範例中使用的類的清單,請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

## <a name="cobjectisserializable"></a><a name="isserializable"></a>CObject:可序列化

測試此物件是否有資格序列化。

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>傳回值

如果可以序列化此物件,則非零;否則 0。

### <a name="remarks"></a>備註

要對類進行序列化,其聲明必須包含[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏,並且實現必須包含[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

> [!NOTE]
> 不要重寫此函數。

### <a name="example"></a>範例

有關所有`CAge``CObject`範例中使用的類的清單,請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

## <a name="cobjectoperator-delete"></a><a name="operator_delete"></a>CObject::運算子刪除

對於庫的發佈版本,運算符**刪除**釋放運算符**new**分配的記憶體。

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

在調試版本中,操作員**刪除**參與旨在檢測記憶體洩漏的分配監視方案。

如果使用代碼行

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

在中的任何實現之前。CPP 檔案,然後將使用**刪除**的第三個版本,將檔名和行號存儲在分配的塊中以供以後報告。 您不必擔心提供額外的參數;宏為您處理。

即使您在除錯模式下不使用DEBUG_NEW,您仍然會檢測到洩漏檢測,但沒有上述源檔行號報告。

如果重寫運算符**新****並刪除**,將喪失此診斷功能。

### <a name="example"></a>範例

`CAge`有關`CObject`範例使用的類的清單,請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

## <a name="cobjectoperator-new"></a><a name="operator_new"></a>CObject::運算元新

對於函式庫的發行版本,運算子**new**以類似於的方式執行最佳`malloc`記憶體分配 。

```
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>備註

在調試版本中 **,新操作員**參與旨在檢測記憶體洩漏的分配監視方案。

如果使用代碼行

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

在中的任何實現之前。CPP 檔案,然後將使用**new**的第二個版本,將檔名和行號存儲在分配的塊中以供以後報告。 您不必擔心提供額外的參數;宏為您處理。

即使您在除錯模式下不使用DEBUG_NEW,您仍然會檢測到洩漏檢測,但沒有上述源檔行號報告。

> [!NOTE]
> 如果重寫此運算子,則必須重寫**刪除**。 不要使用標準庫`_new_handler`函數。

### <a name="example"></a>範例

`CAge`有關`CObject`範例使用的類的清單,請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

## <a name="cobjectserialize"></a><a name="serialize"></a>CObject:序列化

從封存中讀取或寫入此物件。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
要`CArchive`序列化到或從中序列化的物件。

### <a name="remarks"></a>備註

您必須重寫`Serialize`要序列化的每個類。 重寫`Serialize`必須首先調用其基`Serialize`類 的函數。

還必須在類聲明中使用[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏,並且必須在實現中使用[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

使用[CArchive::正在載入](../../mfc/reference/carchive-class.md#isloading)或[CArchive:正在儲存](../../mfc/reference/carchive-class.md#isstoring)以確定存檔是載入還是儲存。

`Serialize`由[CArchive 呼叫:讀取物件](../../mfc/reference/carchive-class.md#readobject)與[CArchive::寫入物件](../../mfc/reference/carchive-class.md#writeobject)。 這些函數與`CArchive`插入運算子**<**( ) 和提取運算子**>>**( ) 相關聯。

有關序列化範例,請參閱文章[序列化:序列化物件](../../mfc/serialization-serializing-an-object.md)。

### <a name="example"></a>範例

有關所有`CAge``CObject`範例中使用的類的清單,請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)
