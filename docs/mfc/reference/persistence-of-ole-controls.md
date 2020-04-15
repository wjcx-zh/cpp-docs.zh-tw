---
title: OLE 控制項的持續性
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: 88707da503b1d1cdc809827dc4d1bac0ccad9b5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373003"
---
# <a name="persistence-of-ole-controls"></a>OLE 控制項的持續性

OLE 控制項的其中一個功能是屬性持續性 (或序列化)，其允許 OLE 控制項對檔案或資料流來回讀取或寫入屬性值。 即使在應用程式已終結控制項之後，容器應用程式仍可以使用序列化來儲存控制項的屬性值。 當控制項的新執行個體在稍後建立時，便可以從檔案或資料流讀取 OLE 控制項的屬性值。

### <a name="persistence-of-ole-controls"></a>OLE 控制項的持續性

|||
|-|-|
|[PX_Blob](#px_blob)|交換儲存二進位大型物件 (BLOB) 資料的控制項屬性。|
|[PX_Bool](#px_bool)|交換**BOOL**類型的控制屬性。|
|[PX_Color](#px_color)|交換控制項的色彩屬性。|
|[PX_Currency](#px_currency)|交換**CY**類型的控制項屬性 。|
|[PX_DataPath](#px_datapath)|交換 `CDataPathProperty` 類型的控制項屬性。|
|[PX_Double](#px_double)|交換**雙類型的**控制屬性。|
|[PX_Font](#px_font)|交換控制項的字型屬性。|
|[PX_Float](#px_float)|交換類型**浮點**的控制屬性。|
|[PX_IUnknown](#px_iunknown)|交換未定義類型的控制項屬性。|
|[PX_Long](#px_long)|交換**長**類型的控制項屬性 。|
|[PX_Picture](#px_picture)|交換控制項的圖片屬性。|
|[PX_Short](#px_short)|交換**短類型的**控制屬性 。|
|[PX_ULong](#px_ulong)|交換**ULONG**型態的控制項屬性 。|
|[PX_UShort](#px_ushort)|交換**USHORT**類型的控制項屬性 。|
|[PXstring](#px_string)|交換字元字串控制項屬性。|
|[PX_VBXFontConvert](#px_vbxfontconvert)|交換 VBX 控制項的字型相關屬性與 OLE 控制項的字型屬性。|

此外,`AfxOleTypeMatchGuid`還提供全域函數以測試 TYPEDESC 和給定 GUID 之間的匹配。

## <a name="px_blob"></a><a name="px_blob"></a>PX_Blob

在控制項`DoPropExchange`的成員函數中調用此函數以序列化或初始化儲存二進位大型物件 (BLOB) 資料的屬性。

```cpp
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>參數

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標(通常作為參數傳遞`DoPropExchange`給 )。

*pszProp名稱*<br/>
要交換的屬性的名稱。

*hBlob*<br/>
對存儲屬性的變數(通常是類的成員變數)的引用。

*hBlobDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

屬性的值將酌情從*hBlob*引用的變數讀取或寫入。 在首次調用`PX_Blob`之前,應將此變數初始化為 NULL(通常,可以在控制項的構造函數中完成)。 如果指定*了 hBlobDefault,* 它將用作屬性的預設值。 如果由於任何原因,控件的初始化或序列化過程失敗,則使用此值。

句柄*hBlob*和*hBlobDefault*引用包含以下內容的記憶體區塊:

- DWORD,它包含以下二進位資料的長度(以位元組為單位),緊接

- 包含實際二進位數據的記憶體區塊。

請注意,`PX_Blob`在載入 BLOB 類型屬性時,將使用 Windows [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) API 分配記憶體。 您負責釋放此記憶體。 因此,控制項的析構函數應在任何 BLOB 類型屬性句柄上調用[GlobalFree,](/windows/win32/api/winbase/nf-winbase-globalfree)以釋放分配給控制項的任何記憶體。

## <a name="px_bool"></a><a name="px_bool"></a>PX_Bool

在控制項`DoPropExchange`的成員函數中調用此函數以序列化或初始化 BOOL 類型的屬性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標(通常作為參數傳遞`DoPropExchange`給 )。

*pszProp名稱*<br/>
要交換的屬性的名稱。

*bValue*<br/>
對存儲屬性的變數(通常是類的成員變數)的引用。

*b預設*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

屬性的值將酌情從*bValue*引用的變數讀取或寫入。 如果指定*bDefault,* 它將用作屬性的預設值。 如果由於任何原因,控件的序列化過程失敗,則使用此值。

## <a name="px_color"></a><a name="px_color"></a>PX_Color

在控制項`DoPropExchange`的成員函數中調用此函數以序列化或初始化OLE_COLOR類型的屬性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標(通常作為參數傳遞`DoPropExchange`給 )。

*pszProp名稱*<br/>
要交換的屬性的名稱。

*clrValue*<br/>
對存儲屬性的變數(通常是類的成員變數)的引用。

*clrDefault*<br/>
屬性的預設值,由控制項開發人員定義。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

屬性的值將酌情從*clrValue*引用的變數讀取或寫入。 如果指定*clrDefault,* 它將用作屬性的預設值。 如果由於任何原因,控件的序列化過程失敗,則使用此值。

## <a name="px_currency"></a><a name="px_currency"></a>PX_Currency

在控制項`DoPropExchange`的成員函數中調用此函數以序列化或初始化類型**貨幣**的屬性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標(通常作為參數傳遞`DoPropExchange`給 )。

*pszProp名稱*<br/>
要交換的屬性的名稱。

*賽價值*<br/>
對存儲屬性的變數(通常是類的成員變數)的引用。

*cyDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

屬性的值將酌情從*cyValue*引用的變數讀取或寫入。 如果指定*了 cyDefault,* 它將用作屬性的預設值。 如果由於任何原因,控件的序列化過程失敗,則使用此值。

## <a name="px_datapath"></a><a name="px_datapath"></a>PX_DataPath

在控制項`DoPropExchange`的成員函數中調用此函數以序列化或初始化[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)類型的資料路徑屬性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標(通常作為參數傳遞`DoPropExchange`給 )。

*pszProp名稱*<br/>
要交換的屬性的名稱。

*資料路徑屬性*<br/>
對存儲屬性的變數(通常是類的成員變數)的引用。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

數據路徑屬性實現非同步控制屬性。 屬性的值將酌情從*dataPathProperty*引用的變數讀取或寫入。

## <a name="px_double"></a><a name="px_double"></a>PX_Double

在控制項`DoPropExchange`的成員函數中呼叫此函數以序列化或初始化類型**為 double**的屬性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標(通常作為參數傳遞`DoPropExchange`給 )。

*pszProp名稱*<br/>
要交換的屬性的名稱。

*雙值*<br/>
對存儲屬性的變數(通常是類的成員變數)的引用。

*雙預設*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

屬性的值根據需要從*doubleValue*引用的變數讀取或寫入。 如果指定*doubleDefault,* 它將用作屬性的預設值。 如果由於任何原因,控件的序列化過程失敗,則使用此值。

## <a name="px_font"></a><a name="px_font"></a>PX_Font

在控制項`DoPropExchange`的成員函數中調用此功能,以序列化或初始化類型字體的屬性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標(通常作為參數傳遞`DoPropExchange`給 )。

*pszProp名稱*<br/>
要交換的屬性的名稱。

*字型*<br/>
對包含字體屬性`CFontHolder`的物件的引用。

*普豐德斯茨*<br/>
指向包含用於初始`FONTDESC`化字體屬性的預設狀態的值的結構的指標,在*pFontDispAmbient*為 NULL 的情況下。

*pFontDisp 環境*<br/>
指向字型`IFontDisp`介面的指標,用於初始化字體屬性的預設狀態。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

屬性的值在適當時從讀取或寫入`font``CFontHolder`參考 。 如果指定*了 pFontDesc*和*pFontDispAmbient,* 則它們用於在需要時初始化屬性的預設值。 如果由於任何原因,控件的序列化過程失敗,則使用這些值。 通常,您傳遞*pFontDesc*的`COleControl::AmbientFont`NULL 和*pFontDispAmbient*傳回的環境值。 請注意,返回的`COleControl::AmbientFont`字體對象必須通過調`IFontDisp::Release`用 成員功能來釋放。

## <a name="px_float"></a><a name="px_float"></a>PX_Float

在控制項`DoPropExchange`的成員函數中調用此函數以序列化或初始化類型**浮點**的屬性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標(通常作為參數傳遞`DoPropExchange`給 )。

*pszProp名稱*<br/>
要交換的屬性的名稱。

*浮動值*<br/>
對存儲屬性的變數(通常是類的成員變數)的引用。

*浮動預設值*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

屬性的值根據需要從*floatValue*引用的變數讀取或寫入。 如果指定*floatDefault,* 它將用作屬性的預設值。 如果由於任何原因,控件的序列化過程失敗,則使用此值。

## <a name="px_iunknown"></a><a name="px_iunknown"></a>PX_IUnknown

在控件`DoPropExchange`的成員函數中調用此函數,以序列化或初始化由具有`IUnknown`派生介面的物件表示的屬性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標(通常作為參數傳遞`DoPropExchange`給 )。

*pszProp名稱*<br/>
要交換的屬性的名稱。

*龐克*<br/>
引用包含表示屬性值的物件的介面的變數。

*Iid*<br/>
指示控制項使用屬性物件的哪個介面的介面 ID。

*pUnkDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

屬性的值根據需要從*pUnk*引用的變數讀取或寫入。 如果指定*了 pUnkDefault,* 它將用作屬性的預設值。 如果由於任何原因,控件的序列化過程失敗,則使用此值。

## <a name="px_long"></a><a name="px_long"></a>PX_Long

在控制項`DoPropExchange`的成員函數中調用此函數以序列化或初始化**長**類型的屬性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標(通常作為參數傳遞`DoPropExchange`給 )。

*pszProp名稱*<br/>
要交換的屬性的名稱。

*lValue*<br/>
對存儲屬性的變數(通常是類的成員變數)的引用。

*l 預設*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

屬性的值根據需要從*lValue*引用的變數讀取或寫入。 如果指定*了 lDefault,* 它將用作屬性的預設值。 如果由於任何原因,控件的序列化過程失敗,則使用此值。

## <a name="px_picture"></a><a name="px_picture"></a>PX_Picture

在控制項`DoPropExchange`的成員函數中調用此函數以序列化或初始化控制件的圖片屬性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標(通常作為參數傳遞`DoPropExchange`給 )。

*pszProp名稱*<br/>
要交換的屬性的名稱。

*圖片*<br/>
引用存儲屬性的[CPictureHolder](../../mfc/reference/cpictureholder-class.md)物件(通常是類的成員變數)。

*圖片預設*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

屬性的值根據需要從*pict*引用的變數讀取或寫入。 如果指定*pictDefault,* 它將用作屬性的預設值。 如果由於任何原因,控件的序列化過程失敗,則使用此值。

## <a name="px_short"></a><a name="px_short"></a>PX_Short

在控制項`DoPropExchange`的成員函數中調用此函數以序列化或初始化類型**短**的屬性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標(通常作為參數傳遞`DoPropExchange`給 )。

*pszProp名稱*<br/>
要交換的屬性的名稱。

*sValue*<br/>
對存儲屬性的變數(通常是類的成員變數)的引用。

*sDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

屬性的值根據需要從*sValue*引用的變數讀取或寫入。 如果指定*sDefault,* 它將用作屬性的預設值。 如果由於任何原因,控件的序列化過程失敗,則使用此值。

## <a name="px_ulong"></a><a name="px_ulong"></a>PX_ULong

在控制項`DoPropExchange`的成員函數中調用此函數以序列化或初始化**ULONG**類型的屬性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標(通常作為參數傳遞`DoPropExchange`給 )。

*pszProp名稱*<br/>
要交換的屬性的名稱。

*ulValue*<br/>
對存儲屬性的變數(通常是類的成員變數)的引用。

*ulDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

屬性的值根據需要從*ulValue*引用的變數讀取或寫入。 如果指定*了 ulDefault,* 它將用作屬性的預設值。 如果由於任何原因,控件的序列化過程失敗,則使用此值。

## <a name="px_ushort"></a><a name="px_ushort"></a>PX_UShort

在控制項`DoPropExchange`的成員函數中調用此函數以序列化或初始化**類型無符號短**的屬性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標(通常作為參數傳遞`DoPropExchange`給 )。

*pszProp名稱*<br/>
要交換的屬性的名稱。

*usValue*<br/>
對存儲屬性的變數(通常是類的成員變數)的引用。

*我們預設*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

屬性的值根據需要從*usValue*引用的變數讀取或寫入。 如果指定*了 UsDefault,* 它將用作屬性的預設值。 如果由於任何原因,控件的序列化過程失敗,則使用此值。

## <a name="pxstring"></a><a name="px_string"></a>PXstring

在控制項`DoPropExchange`的成員函數中調用此函數以序列化或初始化字串屬性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標(通常作為參數傳遞`DoPropExchange`給 )。

*pszProp名稱*<br/>
要交換的屬性的名稱。

*strValue*<br/>
對存儲屬性的變數(通常是類的成員變數)的引用。

*strDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

屬性的值根據需要從*strValue*引用的變數讀取或寫入。 如果指定*strDefault,* 它將用作屬性的預設值。 如果由於任何原因,控件的序列化過程失敗,則使用此值。

## <a name="px_vbxfontconvert"></a><a name="px_vbxfontconvert"></a>PX_VBXFontConvert

在控制項`DoPropExchange`的成員函數中呼叫此功能,透過轉換 VBX 控制件的字型相關屬性來初始化字體屬性。

```cpp
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>參數

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件的指標(通常作為參數傳遞`DoPropExchange`給 )。

*字型*<br/>
包含轉換後的 VBX 字型相關屬性的 OLE 控制項的字型屬性。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

此功能只能由設計為直接替換 VBX 控制項的 OLE 控制項使用。 當 Visual Basic 開發環境轉換包含 VBX 控制件的窗體以使用相應的取代 OLE 控制件時`IDataObject::SetData`,它將調用控制項的函數,傳入包含 VBX 控制件的屬性數據的屬性集中。 此動作反過來又會導致呼叫控制的功能`DoPropExchange`。 `DoPropExchange`可以呼叫`PX_VBXFontConvert`將 VBX 控制項的字型相關屬性(例如,"FontName"、"FontSize"等)轉換為 OLE 控制元件的字型屬性的相應元件。

`PX_VBXFontConvert`僅當控件實際從VBX表單應用程式轉換時,才應呼叫該控制項。 例如：

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
