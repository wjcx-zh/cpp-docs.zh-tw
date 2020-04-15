---
title: 分派對應
ms.date: 06/20/2018
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: 59dd8c7a7b0b930ffdb68fd96410fd73aeb02e81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365747"
---
# <a name="dispatch-maps"></a>分派對應

OLE 自動化提供了調用方法和跨應用程式訪問屬性的方法。 Microsoft 基礎類庫提供的用於調度這些請求的機制是「調度映射」,它指定物件函數和屬性的內部和外部名稱,以及屬性本身和函數參數的數據類型。

|調度對應巨集|描述|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|聲明調度對應將用於公開類的方法和屬性(必須在類聲明中使用)。|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|開始調度映射的定義。|
|[END_DISPATCH_MAP](#end_dispatch_map)|結束調度映射的定義。|
|[DISP_FUNCTION](#disp_function)|在調度映射中用於定義 OLE 自動化功能。|
|[DISP_PROPERTY](#disp_property)|定義 OLE 自動化屬性。|
|[DISP_PROPERTY_EX](#disp_property_ex)|定義 OLE 自動化屬性並命名"獲取和設定" 函數。|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|定義帶有通知的 OLE 自動化屬性。|
|[DISP_PROPERTY_PARAM](#disp_property_param)|定義一個 OLE 自動化屬性,該屬性採用參數並命名"獲取"和"設定"函數。|
|[DISP_DEFVALUE](#disp_defvalue)|將現有的屬性設為物件的預設值。|

## <a name="declare_dispatch_map"></a><a name="declare_dispatch_map"></a>DECLARE_DISPATCH_MAP

如果程式中`CCmdTarget`的派生類支援 OLE 自動化,則該類必須提供調度映射才能公開其方法和屬性。

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>備註

在類聲明末尾使用DECLARE_DISPATCH_MAP宏。 然後,在中。定義類成員函數的 CPP 檔,使用BEGIN_DISPATCH_MAP宏。 然後包括每個類公開方法和屬性(DISP_FUNCTION、DISP_PROPERTY等)的宏條目。 最後,使用END_DISPATCH_MAP宏。

> [!NOTE]
> 如果在DECLARE_DISPATCH_MAP之後聲明任何成員,則必須為其指定新的訪問類型(**公共**、**私有**或**受保護**)。

應用程式精靈和程式碼精靈可幫助創建自動化類和維護調度映射。 有關調度映射的詳細資訊,請參閱[自動化伺服器](../../mfc/automation-servers.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="begin_dispatch_map"></a><a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP

宣告您的分派對應的定義。

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>參數

*類別*<br/>
指定擁有此分派對應之類別的名稱。

*基類*<br/>
指定*類的*基類名稱。

### <a name="remarks"></a>備註

在定義類成員函數的實現 (.cpp) 檔中,使用BEGIN_DISPATCH_MAP宏啟動調度映射,為每個調度函數和屬性添加宏條目,以及使用END_DISPATCH_MAP宏完成調度映射。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="end_dispatch_map"></a><a name="end_dispatch_map"></a>END_DISPATCH_MAP

結束您的分派對應的定義。

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>備註

它必須與BEGIN_DISPATCH_MAP一起使用。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="disp_function"></a><a name="disp_function"></a>DISP_FUNCTION

在調度對應中定義 OLE 自動化功能。

```cpp
DISP_FUNCTION(
    theClass,
    pszName,
    pfnMember,
    vtRetVal,
    vtsParams)
```

### <a name="parameters"></a>參數

*類別*<br/>
類別的名稱。

*pszName*<br/>
函數的外部名稱。

*pfn 成員*<br/>
成員函數的名稱。

*弗特雷特瓦爾*<br/>
指定函數傳回類型的值。

*vtsParams*<br/>
指定函數參數清單的一個或多個常量的空間分隔清單。

### <a name="remarks"></a>備註

*vtRetVal*參數的類型為 VARTYPE。 此參數的以下可能值取自`VARENUM`枚舉:

|符號|傳回類型|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**長**|
|VT_R4|**浮動**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|日期|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

*vtsParams*參數是空格分隔的值清單`VTS_*`和 常量。 一個或多個這些值由空格(不是逗號)分隔,指定函數的參數清單。 例如，

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

指定包含短整數的清單,後跟指向短整數的指標。

常`VTS_`量及其含義如下:

|符號|參數類型|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**長**|
|VTS_R4|**浮動**|
|VTS_R8|**double**|
|VTS_CY|`const CY` 或 `CY*`|
|VTS_DATE|日期|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*` 或 `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__短\*__|
|VTS_PI4|__長\*__|
|VTS_PR4|__浮動\*__|
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

## <a name="disp_property"></a><a name="disp_property"></a>DISP_PROPERTY

在調度對應中定義 OLE 自動化屬性。

```cpp
DISP_PROPERTY(
    theClass,
    pszName,
    memberName,
    vtPropType)
```

### <a name="parameters"></a>參數

*類別*<br/>
類別的名稱。

*pszName*<br/>
屬性的外部名稱。

*成員名稱*<br/>
屬性存儲在其中的成員變數的名稱。

*vtPropType*<br/>
指定屬性類型的值。

### <a name="remarks"></a>備註

*vtPropType*參數的類型為**VARTYPE**。 此參數的可能值取自 VARENUM 枚舉:

|符號|屬性類型|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**長**|
|VT_R4|**浮動**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|日期|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

當外部用戶端更改屬性時,*成員名稱*指定的成員變數的值將更改;沒有更改的通知。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="disp_property_ex"></a><a name="disp_property_ex"></a>DISP_PROPERTY_EX

定義 OLE 自動化屬性,並在調度映射中命名用於獲取和設置該屬性值的函數。

```cpp
DISP_PROPERTY_EX(
    theClass,
    pszName,
    memberGet,
    memberSet,
    vtPropType)
```

### <a name="parameters"></a>參數

*類別*<br/>
類別的名稱。

*pszName*<br/>
屬性的外部名稱。

*成員抓取*<br/>
用於獲取屬性的成員函數的名稱。

*成員集*<br/>
用於設置屬性的成員函數的名稱。

*vtPropType*<br/>
指定屬性類型的值。

### <a name="remarks"></a>備註

*iGet*和*iset*函數具有由*vtPropType*參數確定的簽名。 *iget*函數不採用任何參數,並返回*vtPropType*指定的類型的值。 *成員集*函數採用*vtPropType*指定的類型的參數,不返回任何內容。

*vtPropType*參數的類型為 VARTYPE。 此參數的可能值取自 VARENUM 枚舉。 有關這些值的清單,請參閱[DISP_FUNCTION](#disp_function)中的*vtRetVal*參數的備註。 請注意,DISP_FUNCTION註釋中列出的VT_EMPTY不允許作為屬性數據類型。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="disp_property_notify"></a><a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY

在調度對應中定義具有通知的 OLE 自動化屬性。

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    szExternalName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>參數

*類別*<br/>
類別的名稱。

*sz 外部名稱*<br/>
屬性的外部名稱。

*成員名稱*<br/>
屬性存儲在其中的成員變數的名稱。

*pfn 後集*<br/>
*sz外部名稱*的通知函數的名稱。

*vtPropType*<br/>
指定屬性類型的值。

### <a name="remarks"></a>備註

與使用DISP_PROPERTY定義的屬性不同,使用DISP_PROPERTY_NOTIFY定義的屬性將在更改該屬性時自動調用*pfnAfterSet*指定的函數。

*vtPropType*參數的類型為 VARTYPE。 此參數的可能值取自 VARENUM 枚舉:

|符號|屬性類型|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**長**|
|VT_R4|**浮動**|
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

## <a name="disp_property_param"></a><a name="disp_property_param"></a>DISP_PROPERTY_PARAM

定義使用單獨的`Get`和`Set`成員函數訪問的屬性。

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

*類別*<br/>
類別的名稱。

*psz外部名稱*<br/>
屬性的外部名稱。

*普芬獲取*<br/>
用於獲取屬性的成員函數的名稱。

*pfnSet*<br/>
用於設置屬性的成員函數的名稱。

*vtPropType*<br/>
指定屬性類型的值。

*vtsParams*<br/>
空間分隔`VTS_*`變體參數類型的字串,每個參數一個。

### <a name="remarks"></a>備註

與DISP_PROPERTY_EX宏不同,此宏允許您為屬性指定參數清單。 這對於實現索引或參數化的屬性非常有用。

### <a name="example"></a>範例

請考慮以下 get 與 set 成員函數的聲明,這些函數允許使用者在存取屬性時請求特定的行和列:

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

這些對應於控制排程的以下DISP_PROPERTY_PARAM巨集:

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

作為另一個範例,請考慮以下獲取和設定成員函數:

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

這些對應於控制排程的以下DISP_PROPERTY_PARAM巨集:

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="disp_defvalue"></a><a name="disp_defvalue"></a>DISP_DEFVALUE

將現有的屬性設為物件的預設值。

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>參數

*類別*<br/>
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
