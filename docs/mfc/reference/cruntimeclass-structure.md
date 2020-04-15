---
title: CRuntimeClass 結構
ms.date: 11/04/2016
f1_keywords:
- CRuntimeClass
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
ms.openlocfilehash: a58b9c97d5683423a0f81f6b5424f19f987943bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318556"
---
# <a name="cruntimeclass-structure"></a>CRuntimeClass 結構

派生自的每個`CObject`類都與一`CRuntimeClass`個 結構相關聯,可用於在運行時獲取有關物件或其基類的資訊。

## <a name="syntax"></a>語法

```
struct CRuntimeClass
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRuntime 類別:建立物件](#createobject)|在運行時創建物件。|
|[CRuntime 類別::從名稱](#fromname)|使用熟悉的類名稱在運行時創建物件。|
|[CRuntime 類::派生自](#isderivedfrom)|確定類是否派生自指定的類。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CRuntime 類::m_lpszClassName](#m_lpszclassname)|類別的名稱。|
|[CRuntime 類::m_nObjectSize](#m_nobjectsize)|物件大小 (以位元組為單位)。|
|[CRuntime 類::m_pBaseClass](#m_pbaseclass)|指向基類`CRuntimeClass`結構的指標。|
|[CRuntime 類::m_pfnCreateObject](#m_pfncreateobject)|指向動態創建物件的函數的指標。|
|[CRuntime 類::m_pfnGetBaseClass](#m_pfngetbaseclass)|返回`CRuntimeClass`結構(僅在動態連結時可用)。|
|[CRuntime 類::m_wSchema](#m_wschema)|類的架構編號。|

## <a name="remarks"></a>備註

`CRuntimeClass`是一個結構,因此沒有基類。

當需要對函數參數進行額外的類型檢查時,或者在必須基於物件的類編寫特殊用途代碼時,在運行時確定物件類的能力非常有用。 C++ 語言並不直接支援執行階段類別資訊。

`CRuntimeClass`提供有關相關C++物件的資訊,例如指向基`CRuntimeClass`類的指標和相關類的 ASCII 類名稱。 此結構還實現各種函數,這些函數可用於動態創建物件、使用熟悉的名稱指定物件類型,並確定相關類是否派生自特定類。

有關`CRuntimeClass`使用的詳細資訊,請參閱[訪問運行時類資訊](../../mfc/accessing-run-time-class-information.md)的文章。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CRuntimeClass`

## <a name="requirements"></a>需求

**標題:** afx.h

## <a name="cruntimeclasscreateobject"></a><a name="createobject"></a>CRuntime 類別:建立物件

呼叫此函數以在運行時動態創建指定的類。

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>參數

*lpszClass 名稱*<br/>
要創建的類的熟悉名稱。

### <a name="return-value"></a>傳回值

指向新創建的物件的指標,或者 NULL(如果未找到類名稱或記憶體不足以創建物件)。

### <a name="remarks"></a>備註

派生自的`CObject`類可以支援動態創建,即在運行時創建指定類的物件的能力。 例如,文檔、視圖和框架類應支援動態創建。 有關動態建立與`CreateObject`成員的詳細資訊,請參閱[CObject 類別](../../mfc/using-cobject.md)與[CObject 類別:指定功能等級](../../mfc/specifying-levels-of-functionality.md)。

### <a name="example"></a>範例

  請參閱[「從派生」](#isderivedfrom)的範例。

## <a name="cruntimeclassfromname"></a><a name="fromname"></a>CRuntime 類別::從名稱

調用此函數以檢索與`CRuntimeClass`熟悉名稱關聯的結構。

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>參數

*lpszClass 名稱*<br/>
派生自`CObject`的類的熟悉名稱。

### <a name="return-value"></a>傳回值

指向`CRuntimeClass`物件的指標,對應於*在 lpszClassName*中傳遞的名稱。 如果未找到匹配的類名稱,則函數返回 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

## <a name="cruntimeclassisderivedfrom"></a><a name="isderivedfrom"></a>CRuntime 類::派生自

調用此函數以確定調用類是否派生自*pBaseClass 參數*中指定的類。

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;
```

### <a name="parameters"></a>參數

*pBase 類別*<br/>
派生自`CObject`的類的熟悉名稱。

### <a name="return-value"></a>傳回值

如果類調用`IsDerivedFrom`派生自`CRuntimeClass`其 結構為參數的基類,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

關係由成員的類「行走」到派生類鏈一直「走」到頂部來確定。 僅當找不到基類的匹配項時,此功能才會返回 FALSE。

> [!NOTE]
> 若要使用結構`CRuntimeClass`,必須在要檢索運行時物件的類的實現中包括IMPLEMENT_DYNAMIC、IMPLEMENT_DYNCREATE或IMPLEMENT_SERIAL宏。

有關使用`CRuntimeClass`的詳細資訊,請參閱文章[CObject 類別:存取執行時類別資訊](../../mfc/accessing-run-time-class-information.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

## <a name="cruntimeclassm_lpszclassname"></a><a name="m_lpszclassname"></a>CRuntime 類::m_lpszClassName

包含 ASCII 類別名稱的 null 連接端的字串。

### <a name="remarks"></a>備註

此名稱可用於使用成員函數創建類的`FromName`實例。

### <a name="example"></a>範例

  請參閱[「從派生」](#isderivedfrom)的範例。

## <a name="cruntimeclassm_nobjectsize"></a><a name="m_nobjectsize"></a>CRuntime 類::m_nObjectSize

物件的大小(以位元組為單位)。

### <a name="remarks"></a>備註

如果物件具有指向已分配記憶體的數據成員,則不包括該記憶體的大小。

### <a name="example"></a>範例

  請參閱[「從派生」](#isderivedfrom)的範例。

## <a name="cruntimeclassm_pbaseclass"></a><a name="m_pbaseclass"></a>CRuntime 類::m_pBaseClass

如果應用程式以靜態方式連結到 MFC,則此數據成員包含指向基`CRuntimeClass`類 結構的指標。

### <a name="remarks"></a>備註

如果應用程式動態連結到 MFC 函式庫,請參閱[m_pfnGetBaseClass](#m_pfngetbaseclass)。

### <a name="example"></a>範例

  請參閱[「從派生」](#isderivedfrom)的範例。

## <a name="cruntimeclassm_pfncreateobject"></a><a name="m_pfncreateobject"></a>CRuntime 類::m_pfnCreateObject

指向創建類物件的預設構造函數的函數指標。

### <a name="remarks"></a>備註

僅當類支持動態創建時,此指標才有效;否則,函數將返回 NULL。

## <a name="cruntimeclassm_pfngetbaseclass"></a><a name="m_pfngetbaseclass"></a>CRuntime 類::m_pfnGetBaseClass

如果應用程式使用 MFC 庫作為共用 DLL,則此數據成員指向`CRuntimeClass`返回基類 結構的函數。

### <a name="remarks"></a>備註

如果應用程式靜態連結到 MFC 庫,請參閱[m_pBaseClass](#m_pbaseclass)。

### <a name="example"></a>範例

  請參閱[「從派生」](#isderivedfrom)的範例。

## <a name="cruntimeclassm_wschema"></a><a name="m_wschema"></a>CRuntime 類::m_wSchema

架構編號 (-1 表示不可序列化類)。

### <a name="remarks"></a>備註

有關架構編號的詳細資訊,請參閱[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

### <a name="example"></a>範例

  請參閱[「從派生」](#isderivedfrom)的範例。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CObject:取得執行時類別](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[物件::是](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)<br/>
[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)<br/>
[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)
