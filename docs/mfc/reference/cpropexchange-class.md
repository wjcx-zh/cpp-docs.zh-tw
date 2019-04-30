---
title: CPropExchange 類別
ms.date: 11/04/2016
f1_keywords:
- CPropExchange
- AFXCTL/CPropExchange
- AFXCTL/CPropExchange::ExchangeBlobProp
- AFXCTL/CPropExchange::ExchangeFontProp
- AFXCTL/CPropExchange::ExchangePersistentProp
- AFXCTL/CPropExchange::ExchangeProp
- AFXCTL/CPropExchange::ExchangeVersion
- AFXCTL/CPropExchange::GetVersion
- AFXCTL/CPropExchange::IsAsynchronous
- AFXCTL/CPropExchange::IsLoading
helpviewer_keywords:
- CPropExchange [MFC], ExchangeBlobProp
- CPropExchange [MFC], ExchangeFontProp
- CPropExchange [MFC], ExchangePersistentProp
- CPropExchange [MFC], ExchangeProp
- CPropExchange [MFC], ExchangeVersion
- CPropExchange [MFC], GetVersion
- CPropExchange [MFC], IsAsynchronous
- CPropExchange [MFC], IsLoading
ms.assetid: ed872180-e770-4942-892a-92139d501fab
ms.openlocfilehash: 4210399e32c2bb39008afa75b787c19e3338a7d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372422"
---
# <a name="cpropexchange-class"></a>CPropExchange 類別

支援 OLE 控制項的永續性實作。

## <a name="syntax"></a>語法

```
class AFX_NOVTABLE CPropExchange
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|交換的二進位大型物件 (BLOB) 的屬性。|
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|交換的字型屬性。|
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|交換控制項和檔案之間的屬性。|
|[CPropExchange::ExchangeProp](#exchangeprop)|交換任何內建類型的屬性。|
|[CPropExchange::ExchangeVersion](#exchangeversion)|交換 OLE 控制項的版本號碼。|
|[CPropExchange::GetVersion](#getversion)|擷取 OLE 控制項的版本號碼。|
|[CPropExchange::IsAsynchronous](#isasynchronous)|判斷屬性交換會以非同步方式完成。|
|[CPropExchange::IsLoading](#isloading)|指出屬性是否在載入控制項，或從其儲存。|

## <a name="remarks"></a>備註

`CPropExchange` 沒有基底類別。

建立內容和屬性交換的方向。

持續性是交換控制項的狀態資訊，通常由其屬性，控制項本身與中度之間。

此架構會建構物件衍生自`CPropExchange`時它會通知 OLE 控制項的屬性是要從載入或儲存到永續性儲存體。

架構會將指標傳遞給這`CPropExchange`至您的控制項物件`DoPropExchange`函式。 如果您使用精靈來建立您的控制項，您的控制項的起始檔案`DoPropExchange`函式呼叫`COleControl::DoPropExchange`。 基底類別版本交換控制項的內建屬性;您修改您的衍生的類別版本，以 exchange 屬性已加入您的控制項。

`CPropExchange` 可用來序列化控制項的屬性，或初始化時載入或建立控制項的控制項的屬性。 `ExchangeProp`並`ExchangeFontProp`成員函式`CPropExchange`能夠儲存到的屬性，以及從不同的媒體載入它們。

如需有關使用`CPropExchange`，請參閱文章[MFC ActiveX 控制項：屬性頁](../../mfc/mfc-activex-controls-property-pages.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`CPropExchange`

## <a name="requirements"></a>需求

**標頭：** afxctl.h

##  <a name="exchangeblobprop"></a>  CPropExchange::ExchangeBlobProp

序列化屬性，可儲存二進位大型物件 (BLOB) 資料。

```
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,
    HGLOBAL* phBlob,
    HGLOBAL hBlobDefault = NULL) = 0;
```

### <a name="parameters"></a>參數

*pszPropName*<br/>
在交換元素的屬性名稱。

*phBlob*<br/>
指標，指向 儲存屬性的變數 （變數通常是您類別的成員）。

*hBlobDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

非零值，如果交換成功;0，如果不成功。

### <a name="remarks"></a>備註

屬性的值是讀取或寫入至，適當地所參考的變數*phBlob*。 如果*hBlobDefault*指定，它將用於做為屬性的預設值。 如果因為任何原因而失敗控制項的序列化，則會使用此值。

函式`CArchivePropExchange::ExchangeBlobProp`， `CResetPropExchange::ExchangeBlobProp`，和`CPropsetPropExchange::ExchangeBlobProp`覆寫這個純虛擬函式。

##  <a name="exchangefontprop"></a>  CPropExchange::ExchangeFontProp

交換儲存媒體和控制項之間的字型屬性。

```
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC* pFontDesc,
    LPFONTDISP pFontDispAmbient) = 0;
```

### <a name="parameters"></a>參數

*pszPropName*<br/>
在交換元素的屬性名稱。

*font*<br/>
參考[CFontHolder](../../mfc/reference/cfontholder-class.md)物件，包含字型屬性。

*pFontDesc*<br/>
指標[FONTDESC](/windows/desktop/api/olectl/ns-olectl-tagfontdesc)結構，其中包含用於初始化的字型屬性的預設狀態的值時*pFontDispAmbient*是 NULL。

*pFontDispAmbient*<br/>
指標`IFontDisp`介面將字型會用來初始化 [字型] 屬性的預設狀態。

### <a name="return-value"></a>傳回值

非零值，如果交換成功;0，如果不成功。

### <a name="remarks"></a>備註

如果正在從媒體載入至控制項的字型屬性，從媒體擷取字型的特性和`CFontHolder`所參考的物件*字型*與其初始化。 如果已儲存的字型屬性，字型物件中的特性會寫入至媒體。

函式`CArchivePropExchange::ExchangeFontProp`， `CResetPropExchange::ExchangeFontProp`，和`CPropsetPropExchange::ExchangeFontProp`覆寫這個純虛擬函式。

##  <a name="exchangepersistentprop"></a>  CPropExchange::ExchangePersistentProp

交換控制項和檔案之間的屬性。

```
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,
    LPUNKNOWN* ppUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault) = 0;
```

### <a name="parameters"></a>參數

*pszPropName*<br/>
在交換元素的屬性名稱。

*ppUnk*<br/>
包含屬性的指標變數的指標`IUnknown`（這個變數通常是您類別的成員） 的介面。

*iid*<br/>
控制項將使用的屬性上之介面的介面識別碼。

*pUnkDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

非零值，如果交換成功;0，如果不成功。

### <a name="remarks"></a>備註

如果屬性從檔案載入至控制項，此屬性建立，並從檔案初始化。 如果已儲存的屬性，其值會寫入檔案中。

函式`CArchivePropExchange::ExchangePersistentProp`， `CResetPropExchange::ExchangePersistentProp`，和`CPropsetPropExchange::ExchangePersistentProp`覆寫這個純虛擬函式。

##  <a name="exchangeprop"></a>  CPropExchange::ExchangeProp

交換儲存媒體和控制項之間的屬性。

```
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,
    VARTYPE vtProp,
    void* pvProp,
    const void* pvDefault = NULL) = 0 ;
```

### <a name="parameters"></a>參數

*pszPropName*<br/>
在交換元素的屬性名稱。

*vtProp*<br/>
符號，指定在交換元素的屬性型別。 可能的值為：

|符號|屬性類型|
|------------|-------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_BOOL|**BOOL**|
|VT_BSTR|`CString`|
|VT_CY|**CY**|
|VT_R4|**float**|
|VT_R8|**double**|

*pvProp*<br/>
屬性的值的指標。

*pvDefault*<br/>
屬性的預設值的指標。

### <a name="return-value"></a>傳回值

非零值，如果交換成功;0，如果不成功。

### <a name="remarks"></a>備註

如果屬性從媒體載入至控制項，該屬性的值會從媒體擷取，並儲存在所指向的物件*pvProp*。 如果屬性儲存媒體中，物件的值所指向*pvProp*寫入至媒體。

函式`CArchivePropExchange::ExchangeProp`， `CResetPropExchange::ExchangeProp`，和`CPropsetPropExchange::ExchangeProp`覆寫這個純虛擬函式。

##  <a name="exchangeversion"></a>  CPropExchange::ExchangeVersion

由架構呼叫以處理持續性的版本號碼。

```
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,
    DWORD dwVersionDefault,
    BOOL bConvert);
```

### <a name="parameters"></a>參數

*dwVersionLoaded*<br/>
參考變數，將儲存所載入的永續性資料的版本號碼。

*dwVersionDefault*<br/>
控制項的目前版本號碼。

*bConvert*<br/>
指出是否將永續性資料轉換成目前的版本，或將它保留在相同的版本中已載入。

### <a name="return-value"></a>傳回值

如果函式成功，否則為非零值否則為 0。

##  <a name="getversion"></a>  CPropExchange::GetVersion

呼叫此函式可擷取控制項的版本號碼。

```
DWORD GetVersion();
```

### <a name="return-value"></a>傳回值

控制項版本號碼。

##  <a name="isasynchronous"></a>  CPropExchange::IsAsynchronous

判斷屬性交換會以非同步方式完成。

```
BOOL IsAsynchronous();
```

### <a name="return-value"></a>傳回值

傳回 TRUE，如果屬性被交換以非同步的方式，否則為 FALSE。

##  <a name="isloading"></a>  CPropExchange::IsLoading

呼叫此函式可判斷屬性是否在控制項載入或儲存它。

```
BOOL IsLoading();
```

### <a name="return-value"></a>傳回值

正在載入內容; 如果為非零否則為 0。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleControl::DoPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)
