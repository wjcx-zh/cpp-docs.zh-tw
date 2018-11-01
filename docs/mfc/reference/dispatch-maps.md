---
title: 分派對應
ms.date: 06/20/2018
f1_keywords:
- vc.mfc.macros.maps
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: 5ebedaa02a03bcc7802110977b96659dae45f174
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585077"
---
# <a name="dispatch-maps"></a>分派對應

OLE Automation 提供方式呼叫方法，以及跨應用程式中存取屬性。 Microsoft Foundation 類別庫，用於分派這些要求所提供的機制是 「 分派對應 」 指定的物件函式和屬性，以及資料類型和屬性本身的內部及外部名稱函式引數。

|分派對應巨集|描述|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|宣告的分派對應，將用來公開類別的方法和屬性 （必須使用類別宣告中）。|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|啟動分派對應的定義。|
|[END_DISPATCH_MAP](#end_dispatch_map)|結束的分派對應的定義。|
|[DISP_FUNCTION](#disp_function)|分派對應中使用，用來定義 OLE automation 函式。|
|[DISP_PROPERTY](#disp_property)|定義 OLE automation 屬性。|
|[DISP_PROPERTY_EX](#disp_property_ex)|定義 OLE automation 屬性和名稱的 Get 和 Set 函式。|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|定義通知的 OLE automation 屬性。|
|[DISP_PROPERTY_PARAM](#disp_property_param)|定義會採用參數和名稱的 Get 和 Set 函式的 OLE automation 屬性。|
|[DISP_DEFVALUE](#disp_defvalue)|將現有的屬性設為物件的預設值。|

## <a name="declare_dispatch_map"></a>  DECLARE_DISPATCH_MAP

如果`CCmdTarget`-衍生的類別，在程式中支援 OLE Automation，類別必須提供公開其方法和屬性的分派對應。

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>備註

在類別宣告結尾使用 DECLARE_DISPATCH_MAP 巨集。 然後，在。定義類別，該成員函式的 CPP 檔案使用 BEGIN_DISPATCH_MAP 巨集。 針對每個您的類別公開的方法和屬性 （DISP_FUNCTION、 DISP_PROPERTY，等等），然後包含巨集項目。 最後，使用 END_DISPATCH_MAP 巨集。

> [!NOTE]
> 如果您之後 DECLARE_DISPATCH_MAP 宣告任何成員，您必須指定新的存取類型 (**公開**，**私人**，或**保護**) 它們。

應用程式精靈和程式碼精靈會協助建立 Automation 類別以及維護分派對應。 如需有關分派對應的詳細資訊，請參閱[Automation 伺服程式](../../mfc/automation-servers.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="begin_dispatch_map"></a>  BEGIN_DISPATCH_MAP

宣告您的分派對應的定義。

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
指定擁有此分派對應之類別的名稱。

*baseClass*<br/>
指定的基底類別名稱*theClass*。

### <a name="remarks"></a>備註

在實作 (.cpp) 檔案中定義您的類別成員函式，BEGIN_DISPATCH_MAP 巨集啟動分派對應，針對每個分派函式和屬性新增巨集項目並完成與 END_DISPATCH_ 分派對應對應巨集。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="end_dispatch_map"></a>  END_DISPATCH_MAP

結束您的分派對應的定義。

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>備註

它必須用於 BEGIN_DISPATCH_MAP 搭配使用。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="disp_function"></a>  DISP_FUNCTION

分派對應中定義的 OLE automation 函式。

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
外部函式的名稱。

*pfnMember*<br/>
此成員函式的名稱。

*vtRetVal*<br/>
值，指定函式的傳回型別。

*vtsParams*<br/>
指定函式的參數清單的一或多個常數以空格分隔清單。

### <a name="remarks"></a>備註

*VtRetVal*引數是 VARTYPE 類型。 下列可能的值，這個引數取自`VARENUM`列舉型別：

|符號|傳回型別|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

*VtsParams*引數是以空格分隔的清單中的值`VTS_*`常數。 一或多個以空格 （非逗號） 分隔這些值會指定函式的參數清單。 例如，套用至物件的

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

指定包含短整數的指標所遵循的短整數的清單。

`VTS_`常數和其意義如下：

|符號|參數類型|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_CY|`const CY` 或 `CY*`|
|VTS_DATE|DATE|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*` 或 `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__short\*__|
|VTS_PI4|__長\*__|
|VTS_PR4|__浮點數\*__|
|VTS_PR8|__雙精度浮點數\*__|
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

## <a name="disp_property"></a>  DISP_PROPERTY

分派對應中定義的 OLE automation 屬性。

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
屬性外部名稱。

*成員名稱*<br/>
儲存屬性的成員變數的名稱。

*vtPropType*<br/>
值，指定屬性的型別。

### <a name="remarks"></a>備註

*VtPropType*引數是類型**VARTYPE**。 可能的值，這個引數是取自 VARENUM 列舉：

|符號|屬性類型|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

當外部用戶端變更的屬性，指定的成員變數的值*memberName*變更; 沒有變更的通知。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="disp_property_ex"></a>  DISP_PROPERTY_EX

用來取得和設定屬性的值，在分派對應中的函式定義 OLE automation 屬性和名稱。

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
屬性外部名稱。

*memberGet*<br/>
用來取得屬性的成員函式的名稱。

*成員集合*<br/>
用來設定屬性的成員函式的名稱。

*vtPropType*<br/>
值，指定屬性的型別。

### <a name="remarks"></a>備註

*MemberGet*並*memberSet*函式具有所決定的簽章*vtPropType*引數。 *MemberGet*函式不接受引數，並傳回所指定之類型值*vtPropType*。 *MemberSet*函式接受引數所指定的型別*vtPropType*和不傳回任何東西。

*VtPropType*引數是 VARTYPE 類型。 可能的值，這個引數是取自 VARENUM 列舉型別。 如需這些值的清單，請參閱的 < 備註 > *vtRetVal*中的參數[DISP_FUNCTION](#disp_function)。 請注意，做為屬性的資料類型不允許為 VT_EMPTY，DISP_FUNCTION < 備註 > 中所列。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="disp_property_notify"></a>  DISP_PROPERTY_NOTIFY

分派對應中會定義通知的 OLE automation 屬性。

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
屬性外部名稱。

*成員名稱*<br/>
儲存屬性的成員變數的名稱。

*pfnAfterSet*<br/>
針對通知函式名稱*szExternalName*。

*vtPropType*<br/>
值，指定屬性的型別。

### <a name="remarks"></a>備註

不像使用 DISP_PROPERTY 定義的屬性，定義 DISP_PROPERTY_NOTIFY 屬性會自動呼叫所指定的函數*pfnAfterSet*屬性變更時。

*VtPropType*引數是 VARTYPE 類型。 可能的值，這個引數是取自 VARENUM 列舉：

|符號|屬性類型|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="disp_property_param"></a>  DISP_PROPERTY_PARAM

定義存取使用不同的屬性`Get`和`Set`成員函式。

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
屬性外部名稱。

*pfnGet*<br/>
用來取得屬性的成員函式的名稱。

*pfnSet*<br/>
用來設定屬性的成員函式的名稱。

*vtPropType*<br/>
值，指定屬性的型別。

*vtsParams*<br/>
以空格分隔的字串`VTS_*`variant 參數類型，其中每個參數。

### <a name="remarks"></a>備註

不同於 DISP_PROPERTY_EX 巨集，這個巨集可讓您指定之屬性的參數清單。 這是適合用來實作屬性編製索引或參數化。

### <a name="example"></a>範例

請考慮下列宣告的 get 和集合成員函數可讓使用者存取屬性時，要求特定資料列和資料行：

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

這些會對應至下列 DISP_PROPERTY_PARAM 巨集，在控制項分派對應中：

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

另舉一例，請考慮使用下列 get 並設定成員函式：

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

這些會對應至下列 DISP_PROPERTY_PARAM 巨集，在控制項分派對應中：

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="disp_defvalue"></a>  DISP_DEFVALUE

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

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
