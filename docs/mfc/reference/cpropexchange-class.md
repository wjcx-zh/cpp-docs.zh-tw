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
ms.openlocfilehash: e9ad7c363f2580200af20baeb0acd7a93c1f603b
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420992"
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
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|交換二進位大型物件（BLOB）屬性。|
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|交換字型屬性。|
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|在控制項和檔案之間交換屬性。|
|[CPropExchange::ExchangeProp](#exchangeprop)|任何內建類型的交換屬性。|
|[CPropExchange::ExchangeVersion](#exchangeversion)|交換 OLE 控制項的版本號碼。|
|[CPropExchange：： GetVersion](#getversion)|抓取 OLE 控制項的版本號碼。|
|[CPropExchange：： IsAsynchronous](#isasynchronous)|判斷屬性交換是否以非同步方式完成。|
|[CPropExchange：： IsLoading](#isloading)|指出屬性是否已載入控制項或從中儲存。|

## <a name="remarks"></a>備註

`CPropExchange` 沒有基類。

建立屬性交換的內容和方向。

持續性是在控制項本身與媒體之間交換控制項的狀態資訊，通常以其屬性工作表示。

當通知 OLE 控制項的屬性要從持續性儲存體載入或儲存時，架構會建立衍生自 `CPropExchange` 的物件。

架構會將這個 `CPropExchange` 物件的指標傳遞至控制項的 `DoPropExchange` 函數。 如果您使用 wizard 來建立控制項的入門檔案，控制項的 `DoPropExchange` 函數會呼叫 `COleControl::DoPropExchange`。 基類版本會交換控制項的內建屬性;您可以將衍生類別的版本修改為您已新增至控制項的 exchange 屬性。

`CPropExchange` 可以用來序列化控制項的屬性，或在控制項的載入或建立時初始化控制項的屬性。 `CPropExchange` 的 `ExchangeProp` 和 `ExchangeFontProp` 成員函式可以儲存屬性，並從不同的媒體載入它們。

如需使用 `CPropExchange`的詳細資訊，請參閱[MFC ActiveX 控制項：屬性頁](../../mfc/mfc-activex-controls-property-pages.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

`CPropExchange`

## <a name="requirements"></a>需求

**標頭：** afxctl.h。h

##  <a name="exchangeblobprop"></a>CPropExchange::ExchangeBlobProp

序列化儲存二進位大型物件（BLOB）資料的屬性。

```
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,
    HGLOBAL* phBlob,
    HGLOBAL hBlobDefault = NULL) = 0;
```

### <a name="parameters"></a>參數

*pszPropName*<br/>
正在交換的屬性名稱。

*phBlob*<br/>
指向屬性儲存位置之變數的指標（變數通常是類別的成員）。

*hBlobDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果交換成功，則為非零;如果失敗，則為0。

### <a name="remarks"></a>備註

屬性的值會視需要讀取或寫入*phBlob*所參考的變數。 如果指定*hBlobDefault* ，則會使用它做為屬性的預設值。 如果基於任何原因，控制項的序列化失敗，就會使用這個值。

函式 `CArchivePropExchange::ExchangeBlobProp`、`CResetPropExchange::ExchangeBlobProp`和 `CPropsetPropExchange::ExchangeBlobProp` 覆寫此純虛擬函數。

##  <a name="exchangefontprop"></a>CPropExchange::ExchangeFontProp

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
正在交換的屬性名稱。

*字體*<br/>
包含字型屬性之[CFontHolder](../../mfc/reference/cfontholder-class.md)物件的參考。

*pFontDesc*<br/>
[FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc)結構的指標，其中包含在*pFontDispAmbient*為 Null 時，用來初始化字型屬性之預設狀態的值。

*pFontDispAmbient*<br/>
字型之 `IFontDisp` 介面的指標，用來初始化字型屬性的預設狀態。

### <a name="return-value"></a>傳回值

如果交換成功，則為非零;如果失敗，則為0。

### <a name="remarks"></a>備註

如果字型屬性是從媒體載入至控制項，字型的特性會從媒體抓取，而*字型*所參考的 `CFontHolder` 物件則會使用它們來初始化。 如果字型屬性正在儲存，字型物件中的特性會寫入到媒體中。

函式 `CArchivePropExchange::ExchangeFontProp`、`CResetPropExchange::ExchangeFontProp`和 `CPropsetPropExchange::ExchangeFontProp` 覆寫此純虛擬函數。

##  <a name="exchangepersistentprop"></a>CPropExchange::ExchangePersistentProp

在控制項和檔案之間交換屬性。

```
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,
    LPUNKNOWN* ppUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault) = 0;
```

### <a name="parameters"></a>參數

*pszPropName*<br/>
正在交換的屬性名稱。

*ppUnk*<br/>
變數的指標，其中包含屬性之 `IUnknown` 介面（此變數通常是類別的成員）的指標。

*iid*<br/>
控制項將使用之屬性上介面的介面識別碼。

*pUnkDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果交換成功，則為非零;如果失敗，則為0。

### <a name="remarks"></a>備註

如果將屬性從檔案載入至控制項，則會從檔案建立並初始化屬性。 如果正在儲存屬性，其值會寫入檔案。

函式 `CArchivePropExchange::ExchangePersistentProp`、`CResetPropExchange::ExchangePersistentProp`和 `CPropsetPropExchange::ExchangePersistentProp` 覆寫此純虛擬函數。

##  <a name="exchangeprop"></a>CPropExchange::ExchangeProp

在儲存媒體和控制項之間交換屬性。

```
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,
    VARTYPE vtProp,
    void* pvProp,
    const void* pvDefault = NULL) = 0 ;
```

### <a name="parameters"></a>參數

*pszPropName*<br/>
正在交換的屬性名稱。

*vtProp*<br/>
指定所交換屬性類型的符號。 可能的值包括：

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
屬性值的指標。

*pvDefault*<br/>
屬性之預設值的指標。

### <a name="return-value"></a>傳回值

如果交換成功，則為非零;如果失敗，則為0。

### <a name="remarks"></a>備註

如果將屬性從媒體載入至控制項，則會從媒體中取出屬性的值，並儲存在*pvProp*所指向的物件中。 如果將屬性儲存到媒體中， *pvProp*所指向的物件值就會寫入媒體中。

函式 `CArchivePropExchange::ExchangeProp`、`CResetPropExchange::ExchangeProp`和 `CPropsetPropExchange::ExchangeProp` 覆寫此純虛擬函數。

##  <a name="exchangeversion"></a>CPropExchange::ExchangeVersion

由架構呼叫以處理版本號碼的持續性。

```
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,
    DWORD dwVersionDefault,
    BOOL bConvert);
```

### <a name="parameters"></a>參數

*dwVersionLoaded*<br/>
參考所要載入之持續性資料的版本號碼將會儲存的變數。

*dwVersionDefault*<br/>
控制項的目前版本號碼。

*bConvert*<br/>
指出是否要將持續性資料轉換成目前的版本，或將它保留在載入的相同版本。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則為0。

##  <a name="getversion"></a>CPropExchange：： GetVersion

呼叫此函式可取得控制項的版本號碼。

```
DWORD GetVersion();
```

### <a name="return-value"></a>傳回值

控制項的版本號碼。

##  <a name="isasynchronous"></a>CPropExchange：： IsAsynchronous

判斷屬性交換是否以非同步方式完成。

```
BOOL IsAsynchronous();
```

### <a name="return-value"></a>傳回值

如果以非同步方式交換屬性，則傳回 TRUE，否則傳回 FALSE。

##  <a name="isloading"></a>CPropExchange：： IsLoading

呼叫此函式，以判斷屬性是否正在載入控制項或從中儲存。

```
BOOL IsLoading();
```

### <a name="return-value"></a>傳回值

如果正在載入屬性，則為非零;否則為0。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleControl：:D oPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)
