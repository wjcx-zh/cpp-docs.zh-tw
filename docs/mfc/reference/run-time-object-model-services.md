---
title: 執行階段物件模型服務
ms.date: 03/27/2019
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
ms.openlocfilehash: f1cefdad368ebcd006dcb4ecf653247147f36d03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372948"
---
# <a name="run-time-object-model-services"></a>執行階段物件模型服務

類[CObject](../../mfc/reference/cobject-class.md)和[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)封裝了多個物件服務,包括造訪執行時類資訊、序列化和動態物件創建。 從 `CObject` 衍生的所有類別都會繼承此功能。

對執行階段類別資訊的存取可讓您決定在執行階段的物件類別相關資訊。 當您需要進行函式引數的額外類別檢查時，以及當您必須根據物件類別撰寫特殊用途的程式碼時，能夠在執行階段決定物件的類別就很有用。 C++ 語言並不直接支援執行階段類別資訊。

序列化是對於檔案來回寫入或讀取物件內容的程序。 即使應用程式結束之後，您還是可以使用序列化儲存物件的內容。 當應用程式重新啟動時，您可以從檔案讀取物件。 這類資料物件稱為「持續性」。

動態物件建立可讓您在執行階段建立指定類別的物件。 例如，因為架構需要動態建立文件、檢視和框架物件，所以必須支援動態建立。

下表列出支援的執行階段類別資訊、序列化和動態建立的 MFC 巨集。

有關這些執行時物件服務和序列化的詳細資訊,請參閱文章[CObject 類別:存取執行時類別資訊](../../mfc/accessing-run-time-class-information.md)。

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
|[DECLARE_OLECTLTYPE](#declare_olectltype)|聲明控件類`GetUserTypeNameID``GetMiscStatus`的和成員函數。|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|聲明 OLE 控制者提供屬性頁清單以顯示其屬性。|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|讓物件經由 OLE 系統建立。|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|實現控制`GetUserTypeNameID`項類`GetMiscStatus`的和成員函數。|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|此宏或[IMPLEMENT_OLECREATE](#implement_olecreate)必須出現在`DECLARE_OLECREATE`任何使用 的類的實現檔中。 |

## <a name="afx_comctl32_if_exists"></a><a name="afx_comctl32_if_exists"></a>AFX_COMCTL32_IF_EXISTS

判斷通用控制項程式庫是否實作指定的 API。

### <a name="syntax"></a>語法

```
AFX_COMCTL32_IF_EXISTS(  proc );
```

### <a name="parameters"></a>參數

*proc*<br/>
包含函式名稱以 Null 結束之字串的指標或指定函式的序數值。 如果這個參數是序數值，它必須是低序位文字；高序位文字必須為零。 這個參數必須是 Unicode 值。

### <a name="remarks"></a>備註

使用此宏可以確定公共控制項是否庫了*proc*指定的函數(而不是調用[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress))。

### <a name="requirements"></a>需求

afxcomctl32.h、afxcomctl32.inl

## <a name="afx_comctl32_if_exists2"></a><a name="afx_comctl32_if_exists2"></a>AFX_COMCTL32_IF_EXISTS2

確定公共控制項庫是否實現指定的 API(這是[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)的 Unicode 版本)。

### <a name="syntax"></a>語法

```
AFX_COMCTL32_IF_EXISTS2( proc );
```

### <a name="parameters"></a>參數

*proc*<br/>
包含函式名稱以 Null 結束之字串的指標或指定函式的序數值。 如果這個參數是序數值，它必須是低序位文字；高序位文字必須為零。 這個參數必須是 Unicode 值。

### <a name="remarks"></a>備註

使用此宏可以確定公共控制項是否庫了*proc*指定的函數(而不是調用[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress))。 此宏是AFX_COMCTL32_IF_EXISTS的 Unicode 版本。

### <a name="requirements"></a>需求

afxcomctl32.h、afxcomctl32.inl

## <a name="declare_dynamic"></a><a name="declare_dynamic"></a>DECLARE_DYNAMIC

添加從`CObject`派生類時訪問有關物件的類的運行時資訊的能力。

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類的實際名稱。

### <a name="remarks"></a>備註

將DECLARE_DYNAMIC宏添加到類的標頭 (.h) 模組,然後將該模組包含在需要存取此類物件的所有 .cpp 模組中。

如果使用DECLARE_ DYNAMIC 和IMPLEMENT_DYNAMIC宏,則可以使用RUNTIME_CLASS`CObject::IsKindOf`宏和 函數來確定運行時物件的類。

如果DECLARE_DYNAMIC包含在類聲明中,則必須在類實現中包括IMPLEMENT_DYNAMIC。

有關DECLARE_DYNAMIC巨集的詳細資訊,請參閱[CObject 類別主題](../../mfc/using-cobject.md)。

### <a name="example"></a>範例

請參閱[IMPLEMENT_DYNAMIC](#implement_dynamic)的範例。

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="declare_dyncreate"></a><a name="declare_dyncreate"></a>DECLARE_DYNCREATE

允許在運行時動態`CObject`創建派生類的物件。

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類的實際名稱。

### <a name="remarks"></a>備註

框架使用此功能動態創建新物件。 例如,在打開新文檔時創建的新檢視。 文件、檢視和框架類應支援動態創建,因為框架需要動態創建它們。

在類的 .h 模組中添加DECLARE_DYNCREATE宏,然後將該模組包含在需要存取此類物件的所有 .cpp 模組中。

如果類聲明中包含DECLARE_DYNCREATE,則必須在類實現中包含IMPLEMENT_DYNCREATE。

有關DECLARE_DYNCREATE巨集的詳細資訊,請參閱[CObject 類別主題](../../mfc/using-cobject.md)。

> [!NOTE]
> DECLARE_DYNCREATE宏包括DECLARE_DYNAMIC的所有功能。

### <a name="example"></a>範例

請參閱[IMPLEMENT_DYNCREATE](#implement_dyncreate)的示例。

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="declare_olectltype"></a><a name="declare_olectltype"></a>DECLARE_OLECTLTYPE

聲明控件類`GetUserTypeNameID``GetMiscStatus`的和成員函數。

### <a name="syntax"></a>語法

```
DECLARE_OLECTLTYPE( class_name )
```

### <a name="parameters"></a>參數

*class_name*<br/>
控件類的名稱。

### <a name="remarks"></a>備註

`GetUserTypeNameID`是`GetMiscStatus`純虛擬函數,在中`COleControl`聲明。 由於這些函數是純虛擬的,因此必須在控制類中重寫它們。 除了DECLARE_OLECTLTYPE之外,還必須將IMPLEMENT_OLECTLTYPE宏添加到控件類聲明。

### <a name="requirements"></a>需求

**標題:** afxctl.h

## <a name="declare_proppageids"></a><a name="declare_proppageids"></a>DECLARE_PROPPAGEIDS

聲明 OLE 控制者提供屬性頁清單以顯示其屬性。

### <a name="syntax"></a>語法

```
DECLARE_PROPPAGEIDS( class_name )
```

### <a name="parameters"></a>參數

*class_name*<br/>
擁有屬性頁的控制類類的名稱。

### <a name="remarks"></a>備註

使用類`DECLARE_PROPPAGEIDS`聲明末尾的宏。 然後,在定義類成員函數的 .cpp 檔中,使用每個控制項的屬性`BEGIN_PROPPAGEIDS`頁的宏、宏條`END_PROPPAGEIDS`目和宏來聲明屬性頁清單的末尾。

有關屬性頁的詳細資訊,請參閱文章[ActiveX 控制件:屬性頁](../mfc-activex-controls-property-pages.md)。

### <a name="requirements"></a>需求

**標題:** afxctl.h

## <a name="declare_serial"></a><a name="declare_serial"></a>DECLARE_SERIAL

生成可序列化`CObject`派生類所需的C++標頭代碼。

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類的實際名稱。

### <a name="remarks"></a>備註

序列化是寫入或讀取物件的內容到檔或從檔讀取的過程。

在 .h 模組中使用DECLARE_SERIAL宏,然後將該模組包含在需要訪問此類物件的所有 .cpp 模組中。

如果DECLARE_SERIAL包含在類聲明中,則必須在類實現中包括IMPLEMENT_SERIAL。

DECLARE_SERIAL宏包括DECLARE_DYNAMIC和DECLARE_DYNCREATE的所有功能。

可以使用AFX_API宏自動匯出使用DECLARE_SERIAL和IMPLEMENT_SERIAL宏`CArchive`的類的提取運算符。 使用以下代碼將類別聲明(位於 .h 檔中)括上:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

有關DECLARE_SERIAL巨集的詳細資訊,請參閱[CObject 類別主題](../../mfc/using-cobject.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="implement_dynamic"></a><a name="implement_dynamic"></a>IMPLEMENT_DYNAMIC

生成動態`CObject`派生類所需的C++代碼,該類具有對層次結構中的類名稱和位置的運行時訪問許可權。

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類的實際名稱。

*base_class_name*<br/>
基底類別的名稱。

### <a name="remarks"></a>備註

在 .cpp 模組中使用IMPLEMENT_DYNAMIC宏,然後僅連結一次生成的對象代碼。

有關詳細資訊,請參閱[CObject 類別主題](../../mfc/using-cobject.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="implement_dyncreate"></a><a name="implement_dyncreate"></a>IMPLEMENT_DYNCREATE

啟用`CObject`與DECLARE_DYNCREATE宏一起使用時,在運行時動態創建派生類的物件。

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類的實際名稱。

*base_class_name*<br/>
基類的實際名稱。

### <a name="remarks"></a>備註

框架使用此功能動態創建新物件,例如,在序列化期間從磁碟讀取物件時。 在類實現檔中添加IMPLEMENT_DYNCREATE宏。 有關詳細資訊,請參閱[CObject 類別主題](../../mfc/using-cobject.md)。

如果使用DECLARE_DYNCREATE和IMPLEMENT_DYNCREATE宏,則可以使用RUNTIME_CLASS宏和`CObject::IsKindOf`成員函數來確定運行時物件的類。

如果類聲明中包含DECLARE_DYNCREATE,則必須在類實現中包含IMPLEMENT_DYNCREATE。

請注意,此宏定義將調用類的預設構造函數。 如果非普通構造函數由類顯式實現,它還必須顯式實現預設構造函數。 可以將預設構造函數添加到類的**私有**或**受保護**成員部分,以防止從類實現外部調用它。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="implement_olecreate_flags"></a><a name="implement_olecreate_flags"></a>IMPLEMENT_OLECREATE_FLAGS

對於使用DECLARE_OLECREATE的任何類,此宏或[IMPLEMENT_OLECREATE](#implement_olecreate)必須出現在實現檔中。

### <a name="syntax"></a>語法

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類的實際名稱。

*external_name*<br/>
公開給其他應用程式的物件名稱(以引弧括起來)。

*nFlags*<br/>
包含以下一個或多個標誌:

- `afxRegInsertable`允許控制項顯示在 OLE 物件的「插入物件」對話框中。
- `afxRegApartmentThreading`將註冊表中的線程模型設置為線程模型_公寓。
- `afxRegFreeThreading`將註冊表中的線程模型設置為線程模型_自由。

可以組合兩個標誌`afxRegApartmentThreading``afxRegFreeThreading`並設置線程模型_兩者。 有關線程模型註冊的詳細資訊,請參閱 Windows SDK 中的[InprocServer32。](/windows/win32/com/inprocserver32)

*l,* *w1,* *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8*類 CLSID 的元件.

### <a name="remarks"></a>備註

> [!NOTE]
> 如果使用IMPLEMENT_OLECREATE_FLAGS,則可以使用*nFlags*參數指定物件支援的線程模型。 如果只想支援單線程模型,請使用IMPLEMENT_OLECREATE。

外部名稱是公開給其他應用程式的標識符。 用戶端應用程式使用外部名稱從自動化伺服器請求此類的物件。

OLE 類 ID 是物件的唯一 128 位標識符。 它由一**個長**、兩個**WORD**和八**個 BYTE**組成,*l*在語法描述中由 l、w1、w2 和 b1 到*w1**w2**b8*表示。 *b8* 應用程式精靈和程式碼精靈根據需要為您創建唯一的 OLE 類 ID。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="implement_olectltype"></a><a name="implement_olectltype"></a>IMPLEMENT_OLECTLTYPE

實現控制`GetUserTypeNameID`項類`GetMiscStatus`的和成員函數。

### <a name="syntax"></a>語法

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```

### <a name="parameters"></a>參數

*class_name*<br/>
控件類的名稱。

*idsUserType 名稱*<br/>
包含控制者外部名稱的字串的資源 ID。

*德奧萊米茨*<br/>
包含一個或多個標誌的枚舉。 有關此枚舉的詳細資訊,請參閱 Windows SDK 中的[OLEMISC。](/windows/win32/api/oleidl/ne-oleidl-olemisc)

### <a name="remarks"></a>備註

除了IMPLEMENT_OLECTLTYPE之外,還必須將DECLARE_OLECTLTYPE宏添加到控件類聲明。

成員`GetUserTypeNameID`函數返回標識控制項類的資源字串。 `GetMiscStatus`返回控制項的 OLEMISC 位。 此枚舉指定描述控件的雜項特徵的設置集合。 有關OLEMISC設置的完整說明,請參閱Windows SDK中的[OLEMISC。](/windows/win32/api/oleidl/ne-oleidl-olemisc)

> [!NOTE]
> ActiveX 控制項精靈使用的預設設定是:OLEMISC_ACTIVATEWHENVISIBLE、OLEMISC_SETCLIENTSITEFIRST、OLEMISC_INSIDEOUT、OLEMISC_CANTLINKINSIDE和OLEMISC_RECOMPOSEONRESIZE。

### <a name="requirements"></a>需求

**標題:** afxctl.h

## <a name="implement_serial"></a><a name="implement_serial"></a>IMPLEMENT_SERIAL

生成動態`CObject`派生類所需的C++代碼,該類具有對層次結構中的類名稱和位置的運行時訪問許可權。

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類的實際名稱。

*base_class_name*<br/>
基底類別的名稱。

*wSchema*<br/>
將在存檔中編碼的 UINT"版本號",使反序列化程式能夠識別和處理早期程式版本創建的數據。 類架構編號不能為 -1。

### <a name="remarks"></a>備註

在 .cpp 模組中使用IMPLEMENT_SERIAL宏;然後僅連結一次生成的對象代碼。

可以使用AFX_API宏自動匯出使用DECLARE_SERIAL和IMPLEMENT_SERIAL宏`CArchive`的類的提取運算符。 使用以下代碼將類別聲明(位於 .h 檔中)括上:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

有關詳細資訊,請參閱[CObject 類別主題](../../mfc/using-cobject.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="runtime_class"></a><a name="runtime_class"></a>RUNTIME_CLASS

從C++類的名稱獲取運行時類結構。

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類的實際名稱(不以引弧括起來)。

### <a name="remarks"></a>備註

RUNTIME_CLASS傳回[XRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構的指標,該類別*class_name*class_name指定的 。 只有`CObject`用DECLARE_DYNAMIC、DECLARE_DYNCREATE或DECLARE_SERIAL聲明的派生類才會返回指向結構`CRuntimeClass`的指標。

有關詳細資訊,請參閱[CObject 類別主題](../../mfc/using-cobject.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="declare_olecreate"></a><a name="declare_olecreate"></a>DECLARE_OLECREATE

通過 OLE`CCmdTarget`自動化創建派生類的物件。

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類的實際名稱。

### <a name="remarks"></a>備註

此宏使其他啟用 OLE 的應用程式能夠創建此類型的物件。

在類的 .h 模組中添加DECLARE_OLECREATE宏,然後將該模組包含在需要存取此類物件的所有 .cpp 模組中。

如果類聲明中包含DECLARE_OLECREATE,則必須在類實現中包括IMPLEMENT_OLECREATE。 使用DECLARE_OLECREATE的類聲明還必須使用DECLARE_DYNCREATE或DECLARE_SERIAL。

### <a name="requirements"></a>需求

**標題**: afxdisp.h

## <a name="implement_olecreate"></a><a name="implement_olecreate"></a>IMPLEMENT_OLECREATE

此宏或[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)必須出現在`DECLARE_OLECREATE`任何使用 的類的實現檔中。

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類的實際名稱。

*external_name*<br/>
公開給其他應用程式的物件名稱(以引弧括起來)。

*l,* *w1,* *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8*類 CLSID 的元件.

### <a name="remarks"></a>備註

> [!NOTE]
> 如果使用IMPLEMENT_OLECREATE,默認情況下,您僅支援單個線程模型。 如果使用IMPLEMENT_OLECREATE_FLAGS,則可以使用*nFlags*參數指定物件支援的線程模型。

外部名稱是公開給其他應用程式的標識符。 用戶端應用程式使用外部名稱從自動化伺服器請求此類的物件。

OLE 類 ID 是物件的唯一 128 位標識符。 它由一**個長**、兩個**WORD**和八**個 BYTE**組成,*l*在語法描述中由 l、w1、w2 和 b1 到*w1**w2**b8*表示。 *b8* 應用程式精靈和程式碼精靈根據需要為您創建唯一的 OLE 類 ID。

### <a name="requirements"></a>需求

**標題**: afxdisp.h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[MFC 通用控制項程式庫的隔離](../isolation-of-the-mfc-common-controls-library.md)<br/>
[CLSID 金鑰](/windows/win32/com/clsid-key-hklm)
