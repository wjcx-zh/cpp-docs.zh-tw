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
ms.openlocfilehash: 92979a10c18d9759e0ecc9f0785e56a97c0f0642
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874021"
---
# <a name="cruntimeclass-structure"></a>CRuntimeClass 結構

衍生自 `CObject` 的每個類別都會與 `CRuntimeClass` 結構相關聯，您可以在執行時間用來取得物件或其基類的相關資訊。

## <a name="syntax"></a>語法

```
struct CRuntimeClass
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRuntimeClass：： CreateObject](#createobject)|在執行時間建立物件。|
|[CRuntimeClass：： FromName](#fromname)|使用熟悉的類別名稱，在執行時間建立物件。|
|[CRuntimeClass：： IsDerivedFrom](#isderivedfrom)|判斷類別是否衍生自指定的類別。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CRuntimeClass：： m_lpszClassName](#m_lpszclassname)|類別的名稱。|
|[CRuntimeClass：： m_nObjectSize](#m_nobjectsize)|物件大小 (以位元組為單位)。|
|[CRuntimeClass：： m_pBaseClass](#m_pbaseclass)|基類之 `CRuntimeClass` 結構的指標。|
|[CRuntimeClass：： m_pfnCreateObject](#m_pfncreateobject)|動態建立物件之函式的指標。|
|[CRuntimeClass：： m_pfnGetBaseClass](#m_pfngetbaseclass)|傳回 `CRuntimeClass` 結構（僅適用于動態連結時）。|
|[CRuntimeClass：： m_wSchema](#m_wschema)|類別的架構編號。|

## <a name="remarks"></a>備註

`CRuntimeClass` 是結構，因此沒有基類。

當需要額外的函式引數類型檢查，或您必須根據物件的類別撰寫特殊用途的程式碼時，能夠在執行時間判斷物件的類別會很有用。 C++ 語言並不直接支援執行階段類別資訊。

`CRuntimeClass` 提供相關C++物件的資訊，例如基類的 `CRuntimeClass` 指標，以及相關類別的 ASCII 類別名稱。 這個結構也會執行各種函式，這些函式可用來動態建立物件、使用熟悉的名稱來指定物件的類型，以及判斷相關類別是否衍生自特定類別。

如需使用 `CRuntimeClass`的詳細資訊，請參閱[存取執行時間類別資訊](../../mfc/accessing-run-time-class-information.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

`CRuntimeClass`

## <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="createobject"></a>CRuntimeClass：： CreateObject

呼叫此函式可在執行時間以動態方式建立指定的類別。

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>參數

*lpszClassName*<br/>
要建立之類別的熟悉名稱。

### <a name="return-value"></a>傳回值

新建立之物件的指標，如果找不到類別名稱或記憶體不足，無法建立物件，則為 Null。

### <a name="remarks"></a>備註

衍生自 `CObject` 的類別可以支援動態建立，這是在執行時間建立指定類別之物件的能力。 例如，檔、視圖和框架類別都應該支援動態建立。 如需動態建立和 `CreateObject` 成員的詳細資訊，請參閱[Cobject 類別](../../mfc/using-cobject.md)和[Cobject 類別：指定功能層級](../../mfc/specifying-levels-of-functionality.md)。

### <a name="example"></a>範例

  請參閱[IsDerivedFrom](#isderivedfrom)的範例。

##  <a name="fromname"></a>CRuntimeClass：： FromName

呼叫此函式可取出與熟悉名稱相關聯的 `CRuntimeClass` 結構。

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>參數

*lpszClassName*<br/>
衍生自 `CObject`之類別的熟悉名稱。

### <a name="return-value"></a>傳回值

`CRuntimeClass` 物件的指標，與*lpszClassName*中傳遞的名稱相對應。 如果找不到相符的類別名稱，此函數會傳回 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

##  <a name="isderivedfrom"></a>CRuntimeClass：： IsDerivedFrom

呼叫此函式可判斷呼叫的類別是否衍生自*pBaseClass*參數中指定的類別。

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;
```

### <a name="parameters"></a>參數

*pBaseClass*<br/>
衍生自 `CObject`之類別的熟悉名稱。

### <a name="return-value"></a>傳回值

如果呼叫 `IsDerivedFrom` 的類別衍生自基底類別，而該基類的 `CRuntimeClass` 結構是指定為參數，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

關聯性是由成員類別中的「行走」決定，從衍生類別的鏈到最上層都是如此。 如果找不到基類的相符項，則此函式只會傳回 FALSE。

> [!NOTE]
>  若要使用 `CRuntimeClass` 結構，您必須在要取得其執行時間物件資訊的類別的執行中，包含 IMPLEMENT_DYNAMIC、IMPLEMENT_DYNCREATE 或 IMPLEMENT_SERIAL 宏。

如需使用 `CRuntimeClass`的詳細資訊，請參閱[CObject 類別：存取執行時間類別資訊](../../mfc/accessing-run-time-class-information.md)一文。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

##  <a name="m_lpszclassname"></a>CRuntimeClass：： m_lpszClassName

包含 ASCII 類別名稱的以 null 終止的字串。

### <a name="remarks"></a>備註

這個名稱可用於使用 `FromName` 成員函式建立類別的實例。

### <a name="example"></a>範例

  請參閱[IsDerivedFrom](#isderivedfrom)的範例。

##  <a name="m_nobjectsize"></a>CRuntimeClass：： m_nObjectSize

物件的大小（以位元組為單位）。

### <a name="remarks"></a>備註

如果物件的資料成員指向已配置的記憶體，則不會包含該記憶體的大小。

### <a name="example"></a>範例

  請參閱[IsDerivedFrom](#isderivedfrom)的範例。

##  <a name="m_pbaseclass"></a>CRuntimeClass：： m_pBaseClass

如果您的應用程式以靜態方式連結至 MFC，此資料成員會包含基類之 `CRuntimeClass` 結構的指標。

### <a name="remarks"></a>備註

如果您的應用程式會動態連結至 MFC 程式庫，請參閱[m_pfnGetBaseClass](#m_pfngetbaseclass)。

### <a name="example"></a>範例

  請參閱[IsDerivedFrom](#isderivedfrom)的範例。

##  <a name="m_pfncreateobject"></a>CRuntimeClass：： m_pfnCreateObject

預設的函式指標，可建立類別的物件。

### <a name="remarks"></a>備註

只有在類別支援動態建立時，這個指標才有效;否則，函數會傳回 Null。

##  <a name="m_pfngetbaseclass"></a>CRuntimeClass：： m_pfnGetBaseClass

如果您的應用程式使用 MFC 程式庫做為共用 DLL，這個資料成員會指向函式，該函式會傳回基類的 `CRuntimeClass` 結構。

### <a name="remarks"></a>備註

如果您的應用程式會以靜態方式連結至 MFC 程式庫，請參閱[m_pBaseClass](#m_pbaseclass)。

### <a name="example"></a>範例

  請參閱[IsDerivedFrom](#isderivedfrom)的範例。

##  <a name="m_wschema"></a>CRuntimeClass：： m_wSchema

架構編號（不可序列化類別的-1）。

### <a name="remarks"></a>備註

如需架構編號的詳細資訊，請參閱[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

### <a name="example"></a>範例

  請參閱[IsDerivedFrom](#isderivedfrom)的範例。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CObject：： GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[CObject：： IsKindOf](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)<br/>
[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)<br/>
[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)
