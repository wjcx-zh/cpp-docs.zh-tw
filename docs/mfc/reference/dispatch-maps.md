---
title: 分派對應
ms.date: 06/20/2018
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: f1afa95d7c20d54f2015255a7e4e0d7ad9ae9c2b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856646"
---
# <a name="dispatch-maps"></a>分派對應

OLE Automation 提供方法來呼叫方法，並在應用程式之間存取屬性。 分派這些要求的 MFC 程式庫所提供的機制是「分派對應」，它會指定物件函式和屬性的內部和外部名稱，以及屬性本身和的資料類型函式引數。

|分派對應宏|描述|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|宣告分派對應將用來公開類別的方法和屬性（必須在類別宣告中使用）。|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|啟動分派對應的定義。|
|[END_DISPATCH_MAP](#end_dispatch_map)|結束分派對應的定義。|
|[DISP_FUNCTION](#disp_function)|用於分派對應中，以定義 OLE automation 函數。|
|[DISP_PROPERTY](#disp_property)|定義 OLE automation 屬性。|
|[DISP_PROPERTY_EX](#disp_property_ex)|定義 OLE automation 屬性，並命名 Get 和 Set 函式。|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|以通知定義 OLE automation 屬性。|
|[DISP_PROPERTY_PARAM](#disp_property_param)|定義 OLE automation 屬性，它會接受參數並命名 Get 和 Set 函式。|
|[DISP_DEFVALUE](#disp_defvalue)|將現有的屬性設為物件的預設值。|

## <a name="declare_dispatch_map"></a>DECLARE_DISPATCH_MAP

如果程式中的 `CCmdTarget`衍生類別支援 OLE Automation，該類別就必須提供分派對應來公開其方法和屬性。

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>備註

在類別宣告的結尾使用 DECLARE_DISPATCH_MAP 宏。 然後，在中。定義類別之成員函式的 CPP 檔案，請使用 BEGIN_DISPATCH_MAP 宏。 然後，為每個類別的公開方法和屬性（DISP_FUNCTION、DISP_PROPERTY 等等）包含宏專案。 最後，使用 END_DISPATCH_MAP 宏。

> [!NOTE]
> 如果您在 DECLARE_DISPATCH_MAP 之後宣告任何成員，您必須為它們指定新的存取類型（**公用**、**私**用或**受保護**）。

應用程式精靈和程式碼嚮導會協助建立自動化類別，以及維護分派對應。 如需分派對應的詳細資訊，請參閱[Automation 伺服器](../../mfc/automation-servers.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP

宣告您的分派對應的定義。

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
指定擁有此分派對應之類別的名稱。

*baseClass*<br/>
指定*theClass*的基類名稱。

### <a name="remarks"></a>備註

在為您的類別定義成員函式的執行（.cpp）檔案中，使用 BEGIN_DISPATCH_MAP 宏啟動分派對應、為每個分派函式和屬性新增宏專案，以及使用 END_DISPATCH_ 完成分派對應MAP 宏。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="end_dispatch_map"></a>END_DISPATCH_MAP

結束您的分派對應的定義。

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>備註

它必須與 BEGIN_DISPATCH_MAP 搭配使用。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="disp_function"></a>DISP_FUNCTION

在分派對應中定義 OLE automation 函數。

```cpp
DISP_FUNCTION(
    theClass,
    pszName,
    pfnMember,
    vtRetVal,
    vtsParams)
```

### <a name="parameters"></a>參數

*theClass*<br/>
類別的名稱。

*pszName*<br/>
函數的外部名稱。

*pfnMember*<br/>
成員函式的名稱。

*vtRetVal*<br/>
值，指定函式的傳回型別。

*vtsParams*<br/>
一或多個以空格分隔的清單，其中會指定函式的參數清單。

### <a name="remarks"></a>備註

*VtRetVal*引數的類型為 VARTYPE。 此引數的下列可能值取自 `VARENUM` 列舉：

|符號|傳回類型|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|日期|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

*VtsParams*引數是以空格分隔的清單，其中的值是來自 `VTS_*` 常數。 以空格分隔的其中一個或多個值（不是逗號）會指定函式的參數清單。 例如，

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

指定包含短整數的清單，後面加上短整數的指標。

`VTS_` 常數和其意義如下：

|符號|參數類型|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_CY|`const CY` 或 `CY*`|
|VTS_DATE|日期|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*` 或 `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__簡短\*__|
|VTS_PI4|__長\*__|
|VTS_PR4|__float\*__|
|VTS_PR8|__double\*__|
|VTS_PCY|`CY*`|
|VTS_PDATE|`DATE*`|
|VTS_PBSTR|`BSTR*`|
|VTS_PDISPATCH|`LPDISPATCH*`|
|VTS_PSCODE|`SCODE*`|
|VTS_PBOOL|`BOOL*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_PUNKNOWN|`LPUNKNOWN*`|
|VTS_NONE|沒有參數|

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="disp_property"></a>DISP_PROPERTY

定義分派對應中的 OLE automation 屬性。

```cpp
DISP_PROPERTY(
    theClass,
    pszName,
    memberName,
    vtPropType)
```

### <a name="parameters"></a>參數

*theClass*<br/>
類別的名稱。

*pszName*<br/>
屬性的外部名稱。

*基*<br/>
儲存屬性的成員變數名稱。

*vtPropType*<br/>
指定屬性類型的值。

### <a name="remarks"></a>備註

*VtPropType*引數的類型為**VARTYPE**。 此引數的可能值取自 VARENUM 列舉：

|符號|屬性類型|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|日期|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

當外部客戶*端變更屬性時，由成員*指定的成員變數值會變更;沒有變更的通知。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="disp_property_ex"></a>DISP_PROPERTY_EX

定義 OLE automation 屬性，並命名用來在分派對應中取得和設定屬性值的函式。

```cpp
DISP_PROPERTY_EX(
    theClass,
    pszName,
    memberGet,
    memberSet,
    vtPropType)
```

### <a name="parameters"></a>參數

*theClass*<br/>
類別的名稱。

*pszName*<br/>
屬性的外部名稱。

*memberGet*<br/>
用來取得屬性之成員函式的名稱。

*其間*<br/>
用來設定屬性的成員函式名稱。

*vtPropType*<br/>
指定屬性類型的值。

### <a name="remarks"></a>備註

*MemberGet*和*成員集*函數具有*vtPropType*引數所決定的簽章。 *MemberGet*函數不接受引數，而且會傳回*vtPropType*所指定之類型的值。 *成員集*函數接受*vtPropType*指定之類型的引數，並不傳回任何內容。

*VtPropType*引數的類型為 VARTYPE。 這個引數的可能值取自 VARENUM 列舉。 如需這些值的清單，請參閱[DISP_FUNCTION](#disp_function)中的*vtRetVal*參數備註。 請注意，不允許在 DISP_FUNCTION 備註中列出 VT_EMPTY 做為屬性資料類型。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY

在分派對應中定義具有通知的 OLE automation 屬性。

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    szExternalName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>參數

*theClass*<br/>
類別的名稱。

*szExternalName*<br/>
屬性的外部名稱。

*基*<br/>
儲存屬性的成員變數名稱。

*pfnAfterSet*<br/>
*SzExternalName*的通知函數名稱。

*vtPropType*<br/>
指定屬性類型的值。

### <a name="remarks"></a>備註

不同于以 DISP_PROPERTY 定義的屬性，以 DISP_PROPERTY_NOTIFY 定義的屬性會在屬性變更時，自動呼叫*pfnAfterSet*所指定的函式。

*VtPropType*引數的類型為 VARTYPE。 此引數的可能值取自 VARENUM 列舉：

|符號|屬性類型|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|日期|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="disp_property_param"></a>DISP_PROPERTY_PARAM

定義以個別的 `Get` 和 `Set` 成員函式存取的屬性。

```cpp
DISP_PROPERTY_PARAM(
    theClass,
    pszExternalName,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>參數

*theClass*<br/>
類別的名稱。

*pszExternalName*<br/>
屬性的外部名稱。

*pfnGet*<br/>
用來取得屬性之成員函式的名稱。

*pfnSet*<br/>
用來設定屬性的成員函式名稱。

*vtPropType*<br/>
指定屬性類型的值。

*vtsParams*<br/>
以空格分隔 `VTS_*` variant 參數類型的字串，每個參數各一個。

### <a name="remarks"></a>備註

與 DISP_PROPERTY_EX 宏不同的是，這個宏可讓您指定屬性的參數清單。 這適用于執行已編制索引或參數化的屬性。

### <a name="example"></a>範例

請考慮下列 get 和 set 成員函式的宣告，這些函數可讓使用者在存取屬性時要求特定的資料列和資料行：

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

這些會對應至控制項分派對應中的下列 DISP_PROPERTY_PARAM 宏：

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

另舉一個例子，請考慮下列 get 和 set 成員函式：

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

這些會對應至控制項分派對應中的下列 DISP_PROPERTY_PARAM 宏：

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="disp_defvalue"></a>DISP_DEFVALUE

將現有的屬性設為物件的預設值。

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>參數

*theClass*<br/>
類別的名稱。

*pszName*<br/>
屬性外部名稱，表示物件的｢值｣。

### <a name="remarks"></a>備註

使用預設值可以使設計 Visual Basic 應用程式的自動化物件時更為簡單。

您的物件的「預設值」就是物件的參考不指定屬性或成員函式時，所擷取或設定的屬性。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="see-also"></a>另請參閱

[宏和全域](../../mfc/reference/mfc-macros-and-globals.md)
