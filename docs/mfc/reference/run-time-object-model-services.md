---
title: 執行階段物件模型服務
ms.date: 03/27/2019
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
ms.openlocfilehash: f8b891467d91d0c945b6c59c90dbc49fd7cbcb30
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491593"
---
# <a name="run-time-object-model-services"></a>執行階段物件模型服務

類別[CObject](../../mfc/reference/cobject-class.md)和[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)會封裝數個物件服務, 包括存取執行時間類別資訊、序列化和動態物件建立。 從 `CObject` 衍生的所有類別都會繼承此功能。

對執行階段類別資訊的存取可讓您決定在執行階段的物件類別相關資訊。 當您需要進行函式引數的額外類別檢查時，以及當您必須根據物件類別撰寫特殊用途的程式碼時，能夠在執行階段決定物件的類別就很有用。 C++ 語言並不直接支援執行階段類別資訊。

序列化是對於檔案來回寫入或讀取物件內容的程序。 即使應用程式結束之後，您還是可以使用序列化儲存物件的內容。 當應用程式重新啟動時，您可以從檔案讀取物件。 這類資料物件稱為「持續性」。

動態物件建立可讓您在執行階段建立指定類別的物件。 例如，因為架構需要動態建立文件、檢視和框架物件，所以必須支援動態建立。

下表列出支援的執行階段類別資訊、序列化和動態建立的 MFC 巨集。

如需這些執行時間物件服務和序列化的詳細資訊, 請參閱[CObject 類別:存取執行時間類別資訊](../../mfc/accessing-run-time-class-information.md)。

### <a name="run-time-object-model-services-macros"></a>執行階段物件模型服務巨集

|||
|-|-|
|[DECLARE_DYNAMIC](#declare_dynamic)|啟用對於執行階段類別資訊的存取 (必須在類別宣告中使用)。|
|[DECLARE_DYNCREATE](#declare_dyncreate)|啟用動態建立和存取執行階段類別資訊 (必須在類別宣告中使用)。|
|[DECLARE_SERIAL](#declare_serial)|啟用序列化和存取執行階段類別資訊 (必須在類別宣告中使用)。|
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|啟用對執行階段類別資訊的存取 (必須在類別實作中使用)。|
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|啟用動態建立和存取執行階段資訊 (必須在類別實作中使用)。|
|[IMPLEMENT_SERIAL](#implement_serial)|允許序列化和存取執行階段類別資訊 (必須在類別實作中使用)。|
|[RUNTIME_CLASS](#runtime_class)|傳回對應至已命名類別的 `CRuntimeClass` 結構。|

OLE 經常需要在執行階段動態建立物件。 例如，OLE 伺服器應用程式必須能夠動態建立 OLE 項目以回應來自用戶端的要求。 同樣地，Automation 伺服器必須能夠建立項目以回應從 Automation 用戶端的要求。

MFC 程式庫提供 OLE 兩個特定巨集。

### <a name="dynamic-creation-of-ole-objects"></a>動態建立 OLE 物件

|||
|-|-|
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|判斷通用控制項程式庫是否實作指定的 API。|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|判斷通用控制項程式庫是否實作指定的 API。|
|[DECLARE_OLECREATE](#declare_olecreate)|讓物件透過 OLE Automation 建立。|
|[DECLARE_OLECTLTYPE](#declare_olectltype)|宣告控制項`GetUserTypeNameID`類別`GetMiscStatus`的和成員函式。|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|宣告 OLE 控制項提供屬性頁清單, 以顯示其屬性。|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|讓物件經由 OLE 系統建立。|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|實作用`GetUserTypeNameID`控制項`GetMiscStatus`類別的和成員函式。|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|這個宏或[IMPLEMENT_OLECREATE](#implement_olecreate)必須出現在任何使用`DECLARE_OLECREATE`之類別的執行檔中。 |

## <a name="afx_comctl32_if_exists"></a> AFX_COMCTL32_IF_EXISTS

判斷通用控制項程式庫是否實作指定的 API。

### <a name="syntax"></a>語法

```
AFX_COMCTL32_IF_EXISTS(  proc );
```

### <a name="parameters"></a>參數

*proc*<br/>
包含函式名稱以 Null 結束之字串的指標或指定函式的序數值。 如果這個參數是序數值，它必須是低序位文字；高序位文字必須為零。 這個參數必須是 Unicode 值。

### <a name="remarks"></a>備註

您可以使用這個宏來決定通用控制項程式庫函式所指定的函數 (而不是呼叫[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress))。

### <a name="requirements"></a>需求

afxcomctl32.h、afxcomctl32.inl

## <a name="afx_comctl32_if_exists2"></a>  AFX_COMCTL32_IF_EXISTS2

判斷通用控制項程式庫是否會執行指定的 API (這是 Unicode 版本的[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists))。

### <a name="syntax"></a>語法

```
AFX_COMCTL32_IF_EXISTS2( proc );
```

### <a name="parameters"></a>參數

*proc*<br/>
包含函式名稱以 Null 結束之字串的指標或指定函式的序數值。 如果這個參數是序數值，它必須是低序位文字；高序位文字必須為零。 這個參數必須是 Unicode 值。

### <a name="remarks"></a>備註

您可以使用這個宏來決定通用控制項程式庫函式所指定的函數 (而不是呼叫[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress))。 這個宏是 Unicode 版本的 AFX_COMCTL32_IF_EXISTS。

### <a name="requirements"></a>需求

afxcomctl32.h、afxcomctl32.inl

##  <a name="declare_dynamic"></a>  DECLARE_DYNAMIC

加入從`CObject`衍生類別時, 存取物件類別之執行時間資訊的功能。

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

### <a name="remarks"></a>備註

將 DECLARE_DYNAMIC 宏新增至類別的標頭 (.h) 模組, 然後在需要存取此類別之物件的所有 .cpp 模組中包含該模組。

如果您依照所述使用 DECLARE_ 動態和 IMPLEMENT_DYNAMIC 宏, 則可以使用 RUNTIME_CLASS 宏和`CObject::IsKindOf`函式, 在執行時間判斷物件的類別。

如果 DECLARE_DYNAMIC 包含在類別宣告中, 則 IMPLEMENT_DYNAMIC 必須包含在類別實中。

如需 DECLARE_DYNAMIC 宏的詳細資訊, 請參閱[CObject 類別主題](../../mfc/using-cobject.md)。

### <a name="example"></a>範例

請參閱[IMPLEMENT_DYNAMIC](#implement_dynamic)的範例。

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="declare_dyncreate"></a>  DECLARE_DYNCREATE

可在運行`CObject`時間動態建立衍生類別的物件。

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

### <a name="remarks"></a>備註

此架構會使用此功能, 以動態方式建立新的物件。 例如, 當您開啟新檔時, 會建立新的 view。 檔、視圖和框架類別應該支援動態建立, 因為架構必須以動態方式建立它們。

在類別的 .h 模組中新增 DECLARE_DYNCREATE 宏, 然後在需要存取此類別之物件的所有 .cpp 模組中包含該模組。

如果 DECLARE_DYNCREATE 包含在類別宣告中, 則 IMPLEMENT_DYNCREATE 必須包含在類別實中。

如需 DECLARE_DYNCREATE 宏的詳細資訊, 請參閱[CObject 類別主題](../../mfc/using-cobject.md)。

> [!NOTE]
>  DECLARE_DYNCREATE 宏包含 DECLARE_DYNAMIC 的所有功能。

### <a name="example"></a>範例

請參閱[IMPLEMENT_DYNCREATE](#implement_dyncreate)的範例。

### <a name="requirements"></a>需求

**標頭：** afx.h

## <a name="declare_olectltype"></a>DECLARE_OLECTLTYPE

宣告控制項`GetUserTypeNameID`類別`GetMiscStatus`的和成員函式。

### <a name="syntax"></a>語法

```
DECLARE_OLECTLTYPE( class_name )
```

### <a name="parameters"></a>參數

*class_name*<br/>
控制項類別的名稱。

### <a name="remarks"></a>備註

`GetUserTypeNameID`和`GetMiscStatus`是純虛擬函式, 宣告`COleControl`于中。 因為這些函式是純虛擬的, 所以必須在控制項類別中覆寫這些函式。 除了 DECLARE_OLECTLTYPE 之外, 您還必須將 IMPLEMENT_OLECTLTYPE 宏加入至控制項類別宣告。

### <a name="requirements"></a>需求

**標頭:** afxctl.h。h

## <a name="declare_proppageids"></a>DECLARE_PROPPAGEIDS

宣告 OLE 控制項提供屬性頁清單, 以顯示其屬性。

### <a name="syntax"></a>語法

```
DECLARE_PROPPAGEIDS( class_name )
```

### <a name="parameters"></a>參數

*class_name*<br/>
擁有屬性頁的控制項類別名稱。

### <a name="remarks"></a>備註

在類別宣告的結尾使用宏。`DECLARE_PROPPAGEIDS` 然後, 在定義類別之成員函式的 .cpp 檔案中, 使用`BEGIN_PROPPAGEIDS`宏、每個控制項屬性頁的宏專案, `END_PROPPAGEIDS`以及用來宣告屬性頁清單結尾的宏。

如需屬性頁的詳細資訊, 請參閱[ActiveX 控制項:屬性頁](../mfc-activex-controls-property-pages.md)。

### <a name="requirements"></a>需求

**標頭:** afxctl.h。h

##  <a name="declare_serial"></a>DECLARE_SERIAL

產生可C++序列化的衍生類別所`CObject`需的標頭程式碼。

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

### <a name="remarks"></a>備註

序列化是在檔案中寫入或讀取物件內容的處理常式。

在 .h 模組中使用 DECLARE_SERIAL 宏, 然後在需要存取此類別之物件的所有 .cpp 模組中包含該模組。

如果 DECLARE_SERIAL 包含在類別宣告中, 則 IMPLEMENT_SERIAL 必須包含在類別實中。

DECLARE_SERIAL 宏包含 DECLARE_DYNAMIC 和 DECLARE_DYNCREATE 的所有功能。

您可以使用 AFX_API 宏, 自動匯出`CArchive`使用 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 宏之類別的提取運算子。 使用下列程式碼括住類別宣告 (位於 .h 檔案中):

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

如需 DECLARE_SERIAL 宏的詳細資訊, 請參閱[CObject 類別主題](../../mfc/using-cobject.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="implement_dynamic"></a>  IMPLEMENT_DYNAMIC

產生動態C++ `CObject`衍生類別所需的程式碼, 其具有在階層中的類別名稱和位置的執行時間存取權。

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

*base_class_name*<br/>
基類的名稱。

### <a name="remarks"></a>備註

在 .cpp 模組中使用 IMPLEMENT_DYNAMIC 宏, 然後只將產生的物件程式碼連結一次。

如需詳細資訊, 請參閱[CObject 類別主題](../../mfc/using-cobject.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="implement_dyncreate"></a>  IMPLEMENT_DYNCREATE

當搭配 DECLARE_DYNCREATE `CObject`宏使用時, 可讓衍生類別的物件在執行時間以動態方式建立。

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

*base_class_name*<br/>
基類的實際名稱。

### <a name="remarks"></a>備註

此架構會使用此功能, 以動態方式建立新的物件, 例如, 當它在序列化期間從磁片讀取物件時。 在類別執行檔案中新增 IMPLEMENT_DYNCREATE 宏。 如需詳細資訊, 請參閱[CObject 類別主題](../../mfc/using-cobject.md)。

如果您使用 DECLARE_DYNCREATE 和 IMPLEMENT_DYNCREATE 宏, 則可以使用 RUNTIME_CLASS 宏和`CObject::IsKindOf`成員函式, 在執行時間判斷物件的類別。

如果 DECLARE_DYNCREATE 包含在類別宣告中, 則 IMPLEMENT_DYNCREATE 必須包含在類別實中。

請注意, 這個巨集定義會叫用類別的預設函式。 如果類別明確地執行非一般的函式, 它也必須明確地執行預設的函式。 預設的函式可以新增至類別的**私**用或**protected**成員區段, 以防止從類別實作為外部呼叫它。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

## <a name="implement_olecreate_flags"></a>IMPLEMENT_OLECREATE_FLAGS

這個宏或[IMPLEMENT_OLECREATE](#implement_olecreate)必須在任何使用 DECLARE_OLECREATE 的類別的執行檔中出現。

### <a name="syntax"></a>語法

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

*external_name*<br/>
公開給其他應用程式的物件名稱 (括在引號中)。

*nFlags*<br/>
包含下列一個或多個旗標:

   - `afxRegInsertable`允許控制項出現在 OLE 物件的 [插入物件] 對話方塊中。
   - `afxRegApartmentThreading`將登錄中的執行緒模型設定為 ThreadingModel = 公寓。
   - `afxRegFreeThreading`將登錄中的執行緒模型設定為 ThreadingModel = Free。

         You can combine the two flags `afxRegApartmentThreading` and `afxRegFreeThreading` to set ThreadingModel=Both. See [InprocServer32](/windows/win32/com/inprocserver32) in the Windows SDK for more information on threading model registration.

*l*， *w1*， *w2*， *b1*， *b2*， *b3*， *b4* *b5*， *b6*， *b7*， *b8*元件之類別的 CLSID。

### <a name="remarks"></a>備註

> [!NOTE]
>  如果您使用 IMPLEMENT_OLECREATE_FLAGS, 您可以使用*nFlags*參數指定物件所支援的執行緒模型。 如果您只想要支援單一 treading 模型, 請使用 IMPLEMENT_OLECREATE。

外部名稱是公開給其他應用程式的識別碼。 用戶端應用程式會使用外部名稱, 向 automation 伺服器要求這個類別的物件。

OLE 類別 ID 是物件的唯一128位識別碼。 其中包含一個**長**、兩個**單字**和8個**位元組**的, 這是由*l*、 *w1*、 *w2*和*b1*以語法描述中的*b8*來表示。 [應用程式精靈] 和 [程式碼] 嚮導會視需要為您建立唯一的 OLE 類別 Id。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="implement_olectltype"></a>IMPLEMENT_OLECTLTYPE

實作用`GetUserTypeNameID`控制項`GetMiscStatus`類別的和成員函式。

### <a name="syntax"></a>語法

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```

### <a name="parameters"></a>參數

*class_name*<br/>
控制項類別的名稱。

*idsUserTypeName*<br/>
字串的資源識別碼, 包含控制項的外部名稱。

*dwOleMisc*<br/>
包含一個或多個旗標的列舉。 如需此列舉的詳細資訊, 請參閱 Windows SDK 中的[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) 。

### <a name="remarks"></a>備註

除了 IMPLEMENT_OLECTLTYPE 之外, 您還必須將 DECLARE_OLECTLTYPE 宏加入至控制項類別宣告。

此`GetUserTypeNameID`成員函式會傳回識別控制項類別的資源字串。 `GetMiscStatus`傳回控制項的 OLEMISC 位。 此列舉會指定描述控制項之其他特性的設定集合。 如需 OLEMISC 設定的完整描述, 請參閱 Windows SDK 中的[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) 。

> [!NOTE]
>  ActiveX ControlWizard 所使用的預設設定為:OLEMISC_ACTI加值稅EWHENVISIBLE、OLEMISC_SETCLIENTSITEFIRST、OLEMISC_INSIDEOUT、OLEMISC_CANTLINKINSIDE 和 OLEMISC_RECOMPOSEONRESIZE。

### <a name="requirements"></a>需求

**標頭:** afxctl.h。h

##  <a name="implement_serial"></a>IMPLEMENT_SERIAL

產生動態C++ `CObject`衍生類別所需的程式碼, 其具有在階層中的類別名稱和位置的執行時間存取權。

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

*base_class_name*<br/>
基類的名稱。

*wSchema*<br/>
將在封存中編碼的 UINT 「版本號碼」, 可讓還原序列化程式能夠識別及處理先前程式版本所建立的資料。 類別架構編號不得為-1。

### <a name="remarks"></a>備註

在 .cpp 模組中使用 IMPLEMENT_SERIAL 宏;然後只將產生的物件程式碼連結一次。

您可以使用 AFX_API 宏, 自動匯出`CArchive`使用 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 宏之類別的提取運算子。 使用下列程式碼括住類別宣告 (位於 .h 檔案中):

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

如需詳細資訊, 請參閱[CObject 類別主題](../../mfc/using-cobject.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="runtime_class"></a>RUNTIME_CLASS

從C++類別的名稱取得執行時間類別結構。

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱 (不包含在引號中)。

### <a name="remarks"></a>備註

RUNTIME_CLASS 會針對*class_name*所指定的類別, 傳回[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構的指標。 只有`CObject`使用 DECLARE_DYNAMIC、DECLARE_DYNCREATE 或 DECLARE_SERIAL 宣告的衍生類別, 才會傳回結構的`CRuntimeClass`指標。

如需詳細資訊, 請參閱[CObject 類別主題](../../mfc/using-cobject.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="declare_olecreate"></a>  DECLARE_OLECREATE

可讓衍生`CCmdTarget`類別的物件透過 OLE automation 建立。

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

### <a name="remarks"></a>備註

此宏可讓其他啟用 OLE 的應用程式建立此類型的物件。

在類別的 .h 模組中新增 DECLARE_OLECREATE 宏, 然後在需要存取此類別之物件的所有 .cpp 模組中包含該模組。

如果 DECLARE_OLECREATE 包含在類別宣告中, 則 IMPLEMENT_OLECREATE 必須包含在類別實中。 使用 DECLARE_OLECREATE 的類別宣告也必須使用 DECLARE_DYNCREATE 或 DECLARE_SERIAL。

### <a name="requirements"></a>需求

**標頭**: afxdisp.h。h

##  <a name="implement_olecreate"></a>IMPLEMENT_OLECREATE

這個宏或[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)必須出現在任何使用`DECLARE_OLECREATE`之類別的執行檔中。

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

*external_name*<br/>
公開給其他應用程式的物件名稱 (括在引號中)。

*l*， *w1*， *w2*， *b1*， *b2*， *b3*， *b4* *b5*， *b6*， *b7*， *b8*元件之類別的 CLSID。

### <a name="remarks"></a>備註

> [!NOTE]
>  如果您使用 IMPLEMENT_OLECREATE, 則根據預設, 您只支援單一線程模型。 如果您使用 IMPLEMENT_OLECREATE_FLAGS, 您可以使用*nFlags*參數指定物件所支援的執行緒模型。

外部名稱是公開給其他應用程式的識別碼。 用戶端應用程式會使用外部名稱, 向 automation 伺服器要求這個類別的物件。

OLE 類別 ID 是物件的唯一128位識別碼。 其中包含一個**長**、兩個**單字**和8個**位元組**的, 這是由*l*、 *w1*、 *w2*和*b1*以語法描述中的*b8*來表示。 [應用程式精靈] 和 [程式碼] 嚮導會視需要為您建立唯一的 OLE 類別 Id。

### <a name="requirements"></a>需求

**標頭**: afxdisp.h。h

## <a name="see-also"></a>另請參閱

[宏和全域](mfc-macros-and-globals.md)<br/>
[MFC 通用控制項程式庫的隔離](../isolation-of-the-mfc-common-controls-library.md)<br/>
[CLSID 金鑰](/windows/win32/com/clsid-key-hklm)
