---
title: OLE 控制項的持續性
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: f3ef5a1f465cc478b429b9fa41d6478f22030a8a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843608"
---
# <a name="persistence-of-ole-controls"></a>OLE 控制項的持續性

OLE 控制項的其中一個功能是屬性持續性 (或序列化)，其允許 OLE 控制項對檔案或資料流來回讀取或寫入屬性值。 即使在應用程式已終結控制項之後，容器應用程式仍可以使用序列化來儲存控制項的屬性值。 當控制項的新執行個體在稍後建立時，便可以從檔案或資料流讀取 OLE 控制項的屬性值。

### <a name="persistence-of-ole-controls"></a>OLE 控制項的持續性

|名稱|描述|
|-|-|
|[PX_Blob](#px_blob)|交換儲存二進位大型物件 (BLOB) 資料的控制項屬性。|
|[PX_Bool](#px_bool)|交換 **BOOL**類型的控制項屬性。|
|[PX_Color](#px_color)|交換控制項的色彩屬性。|
|[PX_Currency](#px_currency)|交換類型為 **CY**的控制項屬性。|
|[PX_DataPath](#px_datapath)|交換 `CDataPathProperty` 類型的控制項屬性。|
|[PX_Double](#px_double)|交換類型的控制項屬性 **`double`** 。|
|[PX_Font](#px_font)|交換控制項的字型屬性。|
|[PX_Float](#px_float)|交換類型的控制項屬性 **`float`** 。|
|[PX_IUnknown](#px_iunknown)|交換未定義類型的控制項屬性。|
|[PX_Long](#px_long)|交換類型的控制項屬性 **`long`** 。|
|[PX_Picture](#px_picture)|交換控制項的圖片屬性。|
|[PX_Short](#px_short)|交換類型的控制項屬性 **`short`** 。|
|[PX_ULong](#px_ulong)|交換類型 **ULONG**的控制項屬性。|
|[PX_UShort](#px_ushort)|交換類型 **USHORT**的控制項屬性。|
|[PXstring](#px_string)|交換字元字串控制項屬性。|
|[PX_VBXFontConvert](#px_vbxfontconvert)|交換 VBX 控制項的字型相關屬性與 OLE 控制項的字型屬性。|

此外， `AfxOleTypeMatchGuid` 也會提供全域函式來測試 TYPEDESC 與指定 GUID 之間是否相符。

## <a name="px_blob"></a><a name="px_blob"></a> PX_Blob

在控制項的成員函式中呼叫此函式 `DoPropExchange` ，以序列化或初始化屬性，以將二進位大型物件儲存 (BLOB) 資料。

```cpp
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>參數

*pPX*<br/>
[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標通常會以參數的形式傳遞至 `DoPropExchange`) 的 (。

*pszPropName*<br/>
要交換之屬性的名稱。

*hBlob*<br/>
參考屬性儲存 (變數通常是) 類別的成員變數。

*hBlobDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果 exchange 成功，則為非零;如果不成功，則為0。

### <a name="remarks"></a>備註

將會視情況將屬性的值讀取或寫入至 *hBlob*所參考的變數。 在第一次呼叫時，這個變數應該初始化為 Null `PX_Blob` ， (通常會在控制項的函式) 中完成。 如果指定 *hBlobDefault* ，則會使用它做為屬性的預設值。 如果基於任何原因，控制項的初始化或序列化程式失敗，則會使用這個值。

*HBlob*和*hBlobDefault*的控制碼會參考包含下列各項的記憶體區塊：

- DWORD，其中包含下列二進位資料的長度（以位元組為單位），後面緊接著

- 記憶體區塊，其中包含實際的二進位資料。

請注意， `PX_Blob` 在載入 BLOB 類型屬性時，會使用 Windows [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) API 來配置記憶體。 您必須負責釋放這個記憶體。 因此，您的控制項的函式應該在任何 BLOB 型別的屬性控制碼上呼叫 [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) ，以釋出配置給您的控制項的任何記憶體。

## <a name="px_bool"></a><a name="px_bool"></a> PX_Bool

在控制項的成員函式中呼叫此函式 `DoPropExchange` ，以序列化或初始化 BOOL 類型的屬性。

```cpp
BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue);

BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue,
    BOOL bDefault);
```

### <a name="parameters"></a>參數

*pPX*<br/>
[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標通常會以參數的形式傳遞至 `DoPropExchange`) 的 (。

*pszPropName*<br/>
要交換之屬性的名稱。

*其中 bvalue system.boolean.true*<br/>
參考屬性儲存 (變數通常是) 類別的成員變數。

*bDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果 exchange 成功，則為非零;如果不成功，則為0。

### <a name="remarks"></a>備註

將會視情況將屬性的值讀取或寫入至 *其中 bvalue system.boolean.true*所參考的變數。 如果指定 *bDefault* ，則會使用它做為屬性的預設值。 如果基於任何原因，控制項的序列化程式失敗，則會使用這個值。

## <a name="px_color"></a><a name="px_color"></a> PX_Color

在控制項的成員函式中呼叫此函式 `DoPropExchange` ，以序列化或初始化 OLE_COLOR 類型的屬性。

```cpp
BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue);

BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue,
    OLE_COLOR clrDefault);
```

### <a name="parameters"></a>參數

*pPX*<br/>
[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標通常會以參數的形式傳遞至 `DoPropExchange`) 的 (。

*pszPropName*<br/>
要交換之屬性的名稱。

*clrValue*<br/>
參考屬性儲存 (變數通常是) 類別的成員變數。

*clrDefault*<br/>
屬性的預設值，如控制項開發人員所定義。

### <a name="return-value"></a>傳回值

如果 exchange 成功，則為非零;如果不成功，則為0。

### <a name="remarks"></a>備註

將會視情況將屬性的值讀取或寫入至 *clrValue*所參考的變數。 如果指定 *clrDefault* ，則會使用它做為屬性的預設值。 如果基於任何原因，控制項的序列化程式失敗，則會使用這個值。

## <a name="px_currency"></a><a name="px_currency"></a> PX_Currency

在控制項的成員函式中呼叫此函式 `DoPropExchange` ，以序列化或初始化 **貨幣**類型的屬性。

```cpp
BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue);

BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue,
    CY cyDefault);
```

### <a name="parameters"></a>參數

*pPX*<br/>
[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標通常會以參數的形式傳遞至 `DoPropExchange`) 的 (。

*pszPropName*<br/>
要交換之屬性的名稱。

*cyValue*<br/>
參考屬性儲存 (變數通常是) 類別的成員變數。

*cyDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果 exchange 成功，則為非零;如果不成功，則為0。

### <a name="remarks"></a>備註

將會視情況將屬性的值讀取或寫入至 *cyValue*所參考的變數。 如果指定 *cyDefault* ，則會使用它做為屬性的預設值。 如果基於任何原因，控制項的序列化程式失敗，則會使用這個值。

## <a name="px_datapath"></a><a name="px_datapath"></a> PX_DataPath

在控制項的成員函式中呼叫此函式 `DoPropExchange` ，以序列化或初始化 [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)型別的資料路徑屬性。

```cpp
BOOL PX_DataPath(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CDataPathProperty& dataPathProperty);

BOOL PX_DataPath(
    CPropExchange* pPX,
    CDataPathProperty& dataPathProperty);
```

### <a name="parameters"></a>參數

*pPX*<br/>
[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標通常會以參數的形式傳遞至 `DoPropExchange`) 的 (。

*pszPropName*<br/>
要交換之屬性的名稱。

*dataPathProperty*<br/>
參考屬性儲存 (變數通常是) 類別的成員變數。

### <a name="return-value"></a>傳回值

如果 exchange 成功，則為非零;如果不成功，則為0。

### <a name="remarks"></a>備註

資料路徑屬性會執行非同步控制項屬性。 將會視情況將屬性的值讀取或寫入至 *dataPathProperty*所參考的變數。

## <a name="px_double"></a><a name="px_double"></a> PX_Double

在控制項的成員函式中呼叫此函式 `DoPropExchange` ，以序列化或初始化型別的屬性 **`double`** 。

```cpp
BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue);

BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue,
    double doubleDefault);
```

### <a name="parameters"></a>參數

*pPX*<br/>
[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標通常會以參數的形式傳遞至 `DoPropExchange`) 的 (。

*pszPropName*<br/>
要交換之屬性的名稱。

*doubleValue*<br/>
參考屬性儲存 (變數通常是) 類別的成員變數。

*doubleDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果 exchange 成功，則為非零;如果不成功，則為0。

### <a name="remarks"></a>備註

視需要讀取或寫入 *doubleValue*所參考之變數的屬性值。 如果指定 *doubleDefault* ，則會使用它做為屬性的預設值。 如果基於任何原因，控制項的序列化程式失敗，則會使用這個值。

## <a name="px_font"></a><a name="px_font"></a> PX_Font

在控制項的成員函式中呼叫此函式 `DoPropExchange` ，以序列化或初始化字型類型的屬性。

```cpp
BOOL PX_Font(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC FAR* pFontDesc = NULL,
    LPFONTDISP pFontDispAmbient = NULL);
```

### <a name="parameters"></a>參數

*pPX*<br/>
[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標通常會以參數的形式傳遞至 `DoPropExchange`) 的 (。

*pszPropName*<br/>
要交換之屬性的名稱。

*字體*<br/>
`CFontHolder`包含字型屬性之物件的參考。

*pFontDesc*<br/>
結構的指標， `FONTDESC` 其中包含要在初始化字型屬性的預設狀態時使用的值，在此情況下， *PFONTDISPAMBIENT* 為 Null。

*pFontDispAmbient*<br/>
`IFontDisp`用來初始化字型屬性之預設狀態的字型介面指標。

### <a name="return-value"></a>傳回值

如果 exchange 成功，則為非零;如果不成功，則為0。

### <a name="remarks"></a>備註

在適當的情況下，會將屬性的值讀取或寫入至 `font` `CFontHolder` 參考。 如果指定了 *pFontDesc* 和 *pFontDispAmbient* ，則會在必要時用來初始化屬性的預設值。 如果基於任何原因，控制項的序列化程式失敗，則會使用這些值。 一般來說，您會傳遞 Null 給 *pFontDesc* ，以及 `COleControl::AmbientFont` 針對 *pFontDispAmbient*所傳回的環境值。 請注意，所傳回的字型物件 `COleControl::AmbientFont` 必須由成員函式的呼叫來釋放 `IFontDisp::Release` 。

## <a name="px_float"></a><a name="px_float"></a> PX_Float

在控制項的成員函式中呼叫此函式 `DoPropExchange` ，以序列化或初始化型別的屬性 **`float`** 。

```cpp
BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue);

BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue,
    float floatDefault);
```

### <a name="parameters"></a>參數

*pPX*<br/>
[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標通常會以參數的形式傳遞至 `DoPropExchange`) 的 (。

*pszPropName*<br/>
要交換之屬性的名稱。

*floatValue*<br/>
參考屬性儲存 (變數通常是) 類別的成員變數。

*floatDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果 exchange 成功，則為非零;如果不成功，則為0。

### <a name="remarks"></a>備註

視需要讀取或寫入 *floatValue*所參考之變數的屬性值。 如果指定 *floatDefault* ，則會使用它做為屬性的預設值。 如果基於任何原因，控制項的序列化程式失敗，則會使用這個值。

## <a name="px_iunknown"></a><a name="px_iunknown"></a> PX_IUnknown

在控制項的成員函式中呼叫此函 `DoPropExchange` 式，以序列化或初始化由具有衍生介面的物件所表示的屬性 `IUnknown` 。

```cpp
BOOL PX_IUnknown(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    LPUNKNOWN& pUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault = NULL);
```

### <a name="parameters"></a>參數

*pPX*<br/>
[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標通常會以參數的形式傳遞至 `DoPropExchange`) 的 (。

*pszPropName*<br/>
要交換之屬性的名稱。

*朋 克*<br/>
變數的參考，其中包含代表屬性值之物件的介面。

*Iid*<br/>
介面識別碼，指出控制項所使用的屬性物件介面。

*pUnkDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果 exchange 成功，則為非零;如果不成功，則為0。

### <a name="remarks"></a>備註

視需要讀取或寫入 *pUnk*所參考之變數的屬性值。 如果指定 *pUnkDefault* ，則會使用它做為屬性的預設值。 如果基於任何原因，控制項的序列化程式失敗，則會使用這個值。

## <a name="px_long"></a><a name="px_long"></a> PX_Long

在控制項的成員函式中呼叫此函式 `DoPropExchange` ，以序列化或初始化型別的屬性 **`long`** 。

```cpp
BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue);

BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue,
    long lDefault);
```

### <a name="parameters"></a>參數

*pPX*<br/>
[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標通常會以參數的形式傳遞至 `DoPropExchange`) 的 (。

*pszPropName*<br/>
要交換之屬性的名稱。

*左*<br/>
參考屬性儲存 (變數通常是) 類別的成員變數。

*lDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果 exchange 成功，則為非零;如果不成功，則為0。

### <a name="remarks"></a>備註

視需要讀取或寫入 *左*值所參考之變數的屬性值。 如果指定 *lDefault* ，則會使用它做為屬性的預設值。 如果基於任何原因，控制項的序列化程式失敗，則會使用這個值。

## <a name="px_picture"></a><a name="px_picture"></a> PX_Picture

在控制項的成員函式中呼叫此函式 `DoPropExchange` ，以將控制項的圖片屬性序列化或初始化。

```cpp
BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict);

BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict,
    CPictureHolder& pictDefault);
```

### <a name="parameters"></a>參數

*pPX*<br/>
[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標通常會以參數的形式傳遞至 `DoPropExchange`) 的 (。

*pszPropName*<br/>
要交換之屬性的名稱。

*pict*<br/>
[CPictureHolder](../../mfc/reference/cpictureholder-class.md)物件的參考，其中屬性會儲存 (通常是) 類別的成員變數。

*pictDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果 exchange 成功，則為非零;如果不成功，則為0。

### <a name="remarks"></a>備註

當適當的情況下，屬性的值會讀取或寫入至 *pict*所參考的變數。 如果指定 *pictDefault* ，則會使用它做為屬性的預設值。 如果基於任何原因，控制項的序列化程式失敗，則會使用這個值。

## <a name="px_short"></a><a name="px_short"></a> PX_Short

在控制項的成員函式中呼叫此函式 `DoPropExchange` ，以序列化或初始化型別的屬性 **`short`** 。

```cpp
BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue);

BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue,
    short sDefault);
```

### <a name="parameters"></a>參數

*pPX*<br/>
[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標通常會以參數的形式傳遞至 `DoPropExchange`) 的 (。

*pszPropName*<br/>
要交換之屬性的名稱。

*sValue*<br/>
參考屬性儲存 (變數通常是) 類別的成員變數。

*sDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果 exchange 成功，則為非零;如果不成功，則為0。

### <a name="remarks"></a>備註

視需要讀取或寫入 *sValue*所參考之變數的屬性值。 如果指定 *sDefault* ，則會使用它做為屬性的預設值。 如果基於任何原因，控制項的序列化程式失敗，則會使用這個值。

## <a name="px_ulong"></a><a name="px_ulong"></a> PX_ULong

在控制項的成員函式中呼叫此函式 `DoPropExchange` ，以序列化或初始化 **ULONG**類型的屬性。

```cpp
BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue);

BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue,
    long ulDefault);
```

### <a name="parameters"></a>參數

*pPX*<br/>
[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標通常會以參數的形式傳遞至 `DoPropExchange`) 的 (。

*pszPropName*<br/>
要交換之屬性的名稱。

*ulValue*<br/>
參考屬性儲存 (變數通常是) 類別的成員變數。

*ulDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果 exchange 成功，則為非零;如果不成功，則為0。

### <a name="remarks"></a>備註

視需要讀取或寫入 *ulValue*所參考之變數的屬性值。 如果指定 *ulDefault* ，則會使用它做為屬性的預設值。 如果基於任何原因，控制項的序列化程式失敗，則會使用這個值。

## <a name="px_ushort"></a><a name="px_ushort"></a> PX_UShort

在控制項的成員函式中呼叫此函式 `DoPropExchange` ，以序列化或初始化型別的屬性 **`unsigned short`** 。

```cpp
BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue);

BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue,
    USHORT usDefault);
```

### <a name="parameters"></a>參數

*pPX*<br/>
[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標通常會以參數的形式傳遞至 `DoPropExchange`) 的 (。

*pszPropName*<br/>
要交換之屬性的名稱。

*usValue*<br/>
參考屬性儲存 (變數通常是) 類別的成員變數。

*usDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果 exchange 成功，則為非零;如果不成功，則為0。

### <a name="remarks"></a>備註

視需要讀取或寫入 *usValue*所參考之變數的屬性值。 如果指定 *usDefault* ，則會使用它做為屬性的預設值。 如果基於任何原因，控制項的序列化程式失敗，則會使用這個值。

## <a name="pxstring"></a><a name="px_string"></a> PXstring

在控制項的成員函式中呼叫此函式 `DoPropExchange` ，以將字元字串屬性序列化或初始化。

```cpp
BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue);

BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue,
    CString strDefault);
```

### <a name="parameters"></a>參數

*pPX*<br/>
[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標通常會以參數的形式傳遞至 `DoPropExchange`) 的 (。

*pszPropName*<br/>
要交換之屬性的名稱。

*strValue*<br/>
參考屬性儲存 (變數通常是) 類別的成員變數。

*strDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果 exchange 成功，則為非零;如果不成功，則為0。

### <a name="remarks"></a>備註

視需要讀取或寫入 *strValue*所參考之變數的屬性值。 如果指定 *strDefault* ，則會使用它做為屬性的預設值。 如果基於任何原因，控制項的序列化程式失敗，則會使用這個值。

## <a name="px_vbxfontconvert"></a><a name="px_vbxfontconvert"></a> PX_VBXFontConvert

在控制項的成員函式中呼叫此函 `DoPropExchange` 式，藉由轉換 VBX 控制項的字型相關屬性來初始化字型屬性。

```cpp
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>參數

*pPX*<br/>
[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標通常會以參數的形式傳遞至 `DoPropExchange`) 的 (。

*字體*<br/>
將包含已轉換 VBX 字型相關屬性之 OLE 控制項的字型屬性。

### <a name="return-value"></a>傳回值

如果 exchange 成功，則為非零;如果不成功，則為0。

### <a name="remarks"></a>備註

這個函式只能由設計為 VBX 控制項直接取代的 OLE 控制項使用。 當 Visual Basic 開發環境轉換包含 VBX 控制項的表單以使用對應的取代 OLE 控制項時，它會呼叫控制項的函式 `IDataObject::SetData` ，並傳入包含 VBX 控制項屬性資料的屬性集。 這項作業接著會導致叫用控制項的函式 `DoPropExchange` 。 `DoPropExchange` 可以呼叫， `PX_VBXFontConvert` 將 VBX 控制項的字型相關屬性 (例如 "FontName"、"FontSize" 等，) 到 OLE 控制項字型屬性的對應元件中。

`PX_VBXFontConvert` 只有在實際從 VBX 表單應用程式轉換控制項時，才應該呼叫。 例如：

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
