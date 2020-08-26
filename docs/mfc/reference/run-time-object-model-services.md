---
title: 執行階段物件模型服務
ms.date: 03/27/2019
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
ms.openlocfilehash: 63a82e3b05100f273be04a8718f2ecbb1510f06f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844505"
---
# <a name="run-time-object-model-services"></a>執行階段物件模型服務

[CObject](../../mfc/reference/cobject-class.md)和[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)類別會封裝數個物件服務，包括對執行時間類別資訊、序列化和動態物件建立的存取。 從 `CObject` 衍生的所有類別都會繼承此功能。

對執行階段類別資訊的存取可讓您決定在執行階段的物件類別相關資訊。 當您需要進行函式引數的額外類別檢查時，以及當您必須根據物件類別撰寫特殊用途的程式碼時，能夠在執行階段決定物件的類別就很有用。 C++ 語言並不直接支援執行階段類別資訊。

序列化是對於檔案來回寫入或讀取物件內容的程序。 即使應用程式結束之後，您還是可以使用序列化儲存物件的內容。 當應用程式重新啟動時，您可以從檔案讀取物件。 這類資料物件稱為「持續性」。

動態物件建立可讓您在執行階段建立指定類別的物件。 例如，因為架構需要動態建立文件、檢視和框架物件，所以必須支援動態建立。

下表列出支援的執行階段類別資訊、序列化和動態建立的 MFC 巨集。

如需這些執行時間物件服務和序列化的詳細資訊，請參閱 [CObject 類別：存取執行時間類別資訊](../../mfc/accessing-run-time-class-information.md)一文。

### <a name="run-time-object-model-services-macros"></a>執行階段物件模型服務巨集

|名稱|描述|
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

|名稱|描述|
|-|-|
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|判斷通用控制項程式庫是否實作指定的 API。|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|判斷通用控制項程式庫是否實作指定的 API。|
|[DECLARE_OLECREATE](#declare_olecreate)|讓物件透過 OLE Automation 建立。|
|[DECLARE_OLECTLTYPE](#declare_olectltype)|宣告 `GetUserTypeNameID` 控制項類別的和成員函式 `GetMiscStatus` 。|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|宣告 OLE 控制項提供屬性頁清單來顯示其屬性。|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|讓物件經由 OLE 系統建立。|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|實作為 `GetUserTypeNameID` 控制項類別的和成員函式 `GetMiscStatus` 。|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|這個宏或 [IMPLEMENT_OLECREATE](#implement_olecreate) 必須出現在使用之任何類別的執行檔中 `DECLARE_OLECREATE` 。 |

## <a name="afx_comctl32_if_exists"></a><a name="afx_comctl32_if_exists"></a> AFX_COMCTL32_IF_EXISTS

判斷通用控制項程式庫是否實作指定的 API。

### <a name="syntax"></a>語法

```
AFX_COMCTL32_IF_EXISTS(  proc );
```

### <a name="parameters"></a>參數

*進程*<br/>
包含函式名稱以 Null 結束之字串的指標或指定函式的序數值。 如果這個參數是序數值，它必須是低序位文字；高序位文字必須為零。 這個參數必須是 Unicode 值。

### <a name="remarks"></a>備註

您可以使用這個宏來判斷是否有由 *proc* (指定的函式，而不是呼叫 [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)的通用控制項程式庫。

### <a name="requirements"></a>規格需求

afxcomctl32.h、afxcomctl32.inl

## <a name="afx_comctl32_if_exists2"></a><a name="afx_comctl32_if_exists2"></a> AFX_COMCTL32_IF_EXISTS2

判斷通用控制項程式庫是否會執行指定的 API (這是 [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)) 的 Unicode 版本。

### <a name="syntax"></a>語法

```
AFX_COMCTL32_IF_EXISTS2( proc );
```

### <a name="parameters"></a>參數

*進程*<br/>
包含函式名稱以 Null 結束之字串的指標或指定函式的序數值。 如果這個參數是序數值，它必須是低序位文字；高序位文字必須為零。 這個參數必須是 Unicode 值。

### <a name="remarks"></a>備註

您可以使用這個宏來判斷是否有由 *proc* (指定的函式，而不是呼叫 [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)的通用控制項程式庫。 這個宏是 AFX_COMCTL32_IF_EXISTS 的 Unicode 版本。

### <a name="requirements"></a>規格需求

afxcomctl32.h、afxcomctl32.inl

## <a name="declare_dynamic"></a><a name="declare_dynamic"></a> DECLARE_DYNAMIC

加入從衍生類別時，存取物件類別之執行時間資訊的功能 `CObject` 。

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

### <a name="remarks"></a>備註

將 DECLARE_DYNAMIC 宏加入至類別的標頭 ( .h) 模組，然後將該模組包含在所有需要存取此類別物件的 .cpp 模組中。

如果您使用 DECLARE_ 動態和 IMPLEMENT_DYNAMIC 宏（如所述），您可以在執行時間使用 RUNTIME_CLASS 宏和函式 `CObject::IsKindOf` 來判斷物件的類別。

如果類別宣告中包含 DECLARE_DYNAMIC，則 IMPLEMENT_DYNAMIC 必須包含在類別實中。

如需 DECLARE_DYNAMIC 宏的詳細資訊，請參閱 [CObject 類別主題](../../mfc/using-cobject.md)。

### <a name="example"></a>範例

請參閱 [IMPLEMENT_DYNAMIC](#implement_dynamic)的範例。

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="declare_dyncreate"></a><a name="declare_dyncreate"></a> DECLARE_DYNCREATE

可 `CObject` 在執行時間動態建立衍生類別的物件。

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

### <a name="remarks"></a>備註

此架構會使用這種功能，以動態方式建立新的物件。 例如，當您開啟新的檔時，就會建立新的視圖。 Document、view 和 frame 類別應該支援動態建立，因為架構需要動態建立它們。

將 DECLARE_DYNCREATE 宏加入至類別的 .h 模組中，然後將該模組包含在所有需要存取此類別物件的 .cpp 模組中。

如果類別宣告中包含 DECLARE_DYNCREATE，則 IMPLEMENT_DYNCREATE 必須包含在類別實中。

如需 DECLARE_DYNCREATE 宏的詳細資訊，請參閱 [CObject 類別主題](../../mfc/using-cobject.md)。

> [!NOTE]
> DECLARE_DYNCREATE 宏包含 DECLARE_DYNAMIC 的所有功能。

### <a name="example"></a>範例

請參閱 [IMPLEMENT_DYNCREATE](#implement_dyncreate)的範例。

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="declare_olectltype"></a><a name="declare_olectltype"></a> DECLARE_OLECTLTYPE

宣告 `GetUserTypeNameID` 控制項類別的和成員函式 `GetMiscStatus` 。

### <a name="syntax"></a>語法

```
DECLARE_OLECTLTYPE( class_name )
```

### <a name="parameters"></a>參數

*class_name*<br/>
控制項類別的名稱。

### <a name="remarks"></a>備註

`GetUserTypeNameID` 和 `GetMiscStatus` 是在中宣告的純虛擬函式 `COleControl` 。 因為這些函式是純虛擬的，所以必須在控制項類別中覆寫這些函式。 除了 DECLARE_OLECTLTYPE 之外，您還必須將 IMPLEMENT_OLECTLTYPE 宏加入至控制項類別宣告。

### <a name="requirements"></a>規格需求

**標頭：** afxctl.h。h

## <a name="declare_proppageids"></a><a name="declare_proppageids"></a> DECLARE_PROPPAGEIDS

宣告 OLE 控制項提供屬性頁清單來顯示其屬性。

### <a name="syntax"></a>語法

```
DECLARE_PROPPAGEIDS( class_name )
```

### <a name="parameters"></a>參數

*class_name*<br/>
擁有屬性頁的控制項類別名稱。

### <a name="remarks"></a>備註

在 `DECLARE_PROPPAGEIDS` 類別宣告的結尾使用宏。 然後，在定義類別成員函式的 .cpp 檔案中，使用 `BEGIN_PROPPAGEIDS` 宏、每個控制項屬性頁的宏專案，以及用 `END_PROPPAGEIDS` 來宣告屬性頁清單結尾的宏。

如需屬性頁的詳細資訊，請參閱 [ActiveX 控制項：屬性頁（Property pages](../mfc-activex-controls-property-pages.md)）一文。

### <a name="requirements"></a>規格需求

**標頭：** afxctl.h。h

## <a name="declare_serial"></a><a name="declare_serial"></a> DECLARE_SERIAL

產生可序列化之衍生類別所需的 c + + 標頭 `CObject` 程式碼。

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

### <a name="remarks"></a>備註

序列化是在檔案中來回寫入或讀取物件內容的程式。

在 .h 模組中使用 DECLARE_SERIAL 宏，然後將該模組包含在所有需要存取此類別物件的 .cpp 模組中。

如果類別宣告中包含 DECLARE_SERIAL，則 IMPLEMENT_SERIAL 必須包含在類別實中。

DECLARE_SERIAL 宏包含 DECLARE_DYNAMIC 和 DECLARE_DYNCREATE 的所有功能。

您可以使用 AFX_API 宏，自動匯出 `CArchive` 使用 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 宏之類別的解壓縮運算子。 使用下列程式碼，在 .h 檔案中找到類別宣告 (的括弧) ：

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

如需 DECLARE_SERIAL 宏的詳細資訊，請參閱 [CObject 類別主題](../../mfc/using-cobject.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="implement_dynamic"></a><a name="implement_dynamic"></a> IMPLEMENT_DYNAMIC

產生動態衍生類別所需的 c + + 程式碼，並將 `CObject` 執行時間存取權提供給階層內的類別名稱和位置。

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

*base_class_name*<br/>
基底類別的名稱。

### <a name="remarks"></a>備註

使用 .cpp 模組中的 IMPLEMENT_DYNAMIC 宏，然後只連結產生的物件程式碼一次。

如需詳細資訊，請參閱 [CObject 類別主題](../../mfc/using-cobject.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="implement_dyncreate"></a><a name="implement_dyncreate"></a> IMPLEMENT_DYNCREATE

`CObject`當搭配 DECLARE_DYNCREATE 宏使用時，可在執行時間動態建立衍生類別的物件。

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

*base_class_name*<br/>
基類的實際名稱。

### <a name="remarks"></a>備註

此架構會使用這種功能，以動態方式建立新的物件，例如，當它在序列化期間從磁片讀取物件時。 在類別實檔案中加入 IMPLEMENT_DYNCREATE 宏。 如需詳細資訊，請參閱 [CObject 類別主題](../../mfc/using-cobject.md)。

如果您使用 DECLARE_DYNCREATE 並 IMPLEMENT_DYNCREATE 宏，您可以在執行時間使用 RUNTIME_CLASS 宏和成員函式 `CObject::IsKindOf` 來判斷物件的類別。

如果類別宣告中包含 DECLARE_DYNCREATE，則 IMPLEMENT_DYNCREATE 必須包含在類別實中。

請注意，此巨集定義將會叫用您類別的預設的函式。 如果類別明確地執行非一般的函式，它也必須明確地執行預設的函式。 您可以將預設的函式加入至類別 **`private`** 或 **`protected`** 成員區段，以防止從類別的執行外部呼叫它。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="implement_olecreate_flags"></a><a name="implement_olecreate_flags"></a> IMPLEMENT_OLECREATE_FLAGS

這個宏或 [IMPLEMENT_OLECREATE](#implement_olecreate) 必須出現在任何使用 DECLARE_OLECREATE 之類別的執行檔中。

### <a name="syntax"></a>語法

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

*external_name*<br/>
公開給其他應用程式的物件名稱 (以引號括住) 。

*nFlags*<br/>
包含下列一或多個旗標：

- `afxRegInsertable` 讓控制項出現在 OLE 物件的 [插入物件] 對話方塊中。
- `afxRegApartmentThreading` 將登錄中的執行緒模型設定為 >threadingmodel = 公寓。
- `afxRegFreeThreading` 將登錄中的執行緒模型設定為 >threadingmodel = Free。

您可以結合這兩個旗標 `afxRegApartmentThreading` ，並 `afxRegFreeThreading` 設定 >threadingmodel = Both。 如需有關執行緒模型註冊的詳細資訊，請參閱 Windows SDK 中的 [InprocServer32](/windows/win32/com/inprocserver32) 。

*l*、 *w1*、 *w2*、 *b1*、 *b2*、 *B3*、 *b4*、 *b5*、 *b6*、 *b7*、類別 CLSID 的 *b8* 元件。

### <a name="remarks"></a>備註

> [!NOTE]
> 如果您使用 IMPLEMENT_OLECREATE_FLAGS，可以使用 *nFlags* 參數來指定物件支援的執行緒模型。 如果您只想要支援單一 treading 模型，請使用 IMPLEMENT_OLECREATE。

外部名稱是公開給其他應用程式的識別碼。 用戶端應用程式會使用外部名稱，從 automation 伺服器要求這個類別的物件。

OLE 類別識別碼是物件的唯一128位識別碼。 它是由一個 **`long`** 、兩個 **單字**和八個 **位元組**s 所組成，如 *l*、 *w1*、 *w2*和 *b1* 透過語法描述中的 *b8* 所代表。 [應用程式] 和 [程式碼] 嚮導會視需要為您建立唯一的 OLE 類別識別碼。

### <a name="requirements"></a>規格需求

**標頭：** afxdisp.h

## <a name="implement_olectltype"></a><a name="implement_olectltype"></a> IMPLEMENT_OLECTLTYPE

實作為 `GetUserTypeNameID` 控制項類別的和成員函式 `GetMiscStatus` 。

### <a name="syntax"></a>語法

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```

### <a name="parameters"></a>參數

*class_name*<br/>
控制項類別的名稱。

*idsUserTypeName*<br/>
字串的資源識別碼，包含控制項的外部名稱。

*dwOleMisc*<br/>
包含一或多個旗標的列舉。 如需此列舉的詳細資訊，請參閱 Windows SDK 中的 [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) 。

### <a name="remarks"></a>備註

除了 IMPLEMENT_OLECTLTYPE 之外，您還必須將 DECLARE_OLECTLTYPE 宏加入至控制項類別宣告。

成員函式 `GetUserTypeNameID` 會傳回識別您控制項類別的資源字串。 `GetMiscStatus` 傳回控制項的 OLEMISC 位。 此列舉會指定描述控制項其他特性的設定集合。 如需 OLEMISC 設定的完整說明，請參閱 Windows SDK 中的 [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) 。

> [!NOTE]
> ActiveX ControlWizard 所使用的預設設定為： OLEMISC_ACTI加值稅EWHENVISIBLE、OLEMISC_SETCLIENTSITEFIRST、OLEMISC_INSIDEOUT、OLEMISC_CANTLINKINSIDE 和 OLEMISC_RECOMPOSEONRESIZE。

### <a name="requirements"></a>規格需求

**標頭：** afxctl.h。h

## <a name="implement_serial"></a><a name="implement_serial"></a> IMPLEMENT_SERIAL

產生動態衍生類別所需的 c + + 程式碼，並將 `CObject` 執行時間存取權提供給階層內的類別名稱和位置。

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

*base_class_name*<br/>
基底類別的名稱。

*wSchema*<br/>
將在封存中編碼的 UINT "version number"，可讓還原序列化程式識別並處理舊版程式所建立的資料。 類別架構編號不得為-1。

### <a name="remarks"></a>備註

使用 .cpp 模組中的 IMPLEMENT_SERIAL 宏;然後只連結產生的物件程式碼一次。

您可以使用 AFX_API 宏，自動匯出 `CArchive` 使用 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 宏之類別的解壓縮運算子。 使用下列程式碼，在 .h 檔案中找到類別宣告 (的括弧) ：

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

如需詳細資訊，請參閱 [CObject 類別主題](../../mfc/using-cobject.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="runtime_class"></a><a name="runtime_class"></a> RUNTIME_CLASS

從 c + + 類別的名稱取得執行時間類別結構。

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱 (不會以引號括住) 。

### <a name="remarks"></a>備註

RUNTIME_CLASS 傳回*class_name*所指定之類別的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構指標。 只有 `CObject` 使用 DECLARE_DYNAMIC、DECLARE_DYNCREATE 或 DECLARE_SERIAL 宣告的衍生類別會傳回結構的指標 `CRuntimeClass` 。

如需詳細資訊，請參閱 [CObject 類別主題](../../mfc/using-cobject.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="declare_olecreate"></a><a name="declare_olecreate"></a> DECLARE_OLECREATE

讓衍生類別的物件可 `CCmdTarget` 透過 OLE automation 建立。

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

### <a name="remarks"></a>備註

這個宏可讓其他具有 OLE 功能的應用程式建立此類型的物件。

將 DECLARE_OLECREATE 宏加入至類別的 .h 模組中，然後將該模組包含在所有需要存取此類別物件的 .cpp 模組中。

如果類別宣告中包含 DECLARE_OLECREATE，則 IMPLEMENT_OLECREATE 必須包含在類別實中。 使用 DECLARE_OLECREATE 的類別宣告也必須使用 DECLARE_DYNCREATE 或 DECLARE_SERIAL。

### <a name="requirements"></a>規格需求

**標頭**： afxdisp.h。h

## <a name="implement_olecreate"></a><a name="implement_olecreate"></a> IMPLEMENT_OLECREATE

這個宏或 [IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags) 必須出現在使用之任何類別的執行檔中 `DECLARE_OLECREATE` 。

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類別的實際名稱。

*external_name*<br/>
公開給其他應用程式的物件名稱 (以引號括住) 。

*l*、 *w1*、 *w2*、 *b1*、 *b2*、 *B3*、 *b4*、 *b5*、 *b6*、 *b7*、類別 CLSID 的 *b8* 元件。

### <a name="remarks"></a>備註

> [!NOTE]
> 如果您使用 IMPLEMENT_OLECREATE，則預設只支援單一線程模型。 如果您使用 IMPLEMENT_OLECREATE_FLAGS，可以使用 *nFlags* 參數來指定物件支援的執行緒模型。

外部名稱是公開給其他應用程式的識別碼。 用戶端應用程式會使用外部名稱，從 automation 伺服器要求這個類別的物件。

OLE 類別識別碼是物件的唯一128位識別碼。 它是由一個 **`long`** 、兩個 **單字**和八個 **位元組**s 所組成，如 *l*、 *w1*、 *w2*和 *b1* 透過語法描述中的 *b8* 所代表。 [應用程式] 和 [程式碼] 嚮導會視需要為您建立唯一的 OLE 類別識別碼。

### <a name="requirements"></a>規格需求

**標頭**： afxdisp.h。h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[MFC 通用控制項程式庫的隔離](../isolation-of-the-mfc-common-controls-library.md)<br/>
[CLSID 金鑰](/windows/win32/com/clsid-key-hklm)
