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
ms.openlocfilehash: 7818b15e502bb32640d6b9dbfe1a6e4927c70650
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363977"
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
|[CPropExchange::交換BlobProp](#exchangeblobprop)|交換二進位大型物件 (BLOB) 屬性。|
|[CPropExchange::交換方普羅普](#exchangefontprop)|交換字體屬性。|
|[CPropExchange::交換持久](#exchangepersistentprop)|在控制項和文件之間交換屬性。|
|[CPropExchange:交換](#exchangeprop)|交換任何內置類型的屬性。|
|[CPropExchange:交換版本](#exchangeversion)|交換 OLE 控制項版本號。|
|[CPropExchange:取得版本](#getversion)|檢索 OLE 控件的版本號。|
|[CPropExchange:是同步的](#isasynchronous)|確定屬換是否異步完成。|
|[CPropExchange:正在載入](#isloading)|指示屬性是載入到控制項中還是從控制項中保存。|

## <a name="remarks"></a>備註

`CPropExchange`沒有基類。

建立財產交換的上下文和方向。

持久性是控件本身和介質之間的狀態資訊(通常由其屬性表示)的交換。

框架建構從`CPropExchange`通知 OLE 控制的屬性將從持久儲存載入或儲存到持久儲存時派生的物件。

框架將指向此`CPropExchange`物件的指標傳遞給控件的`DoPropExchange`函數。 如果使用精靈為控制項建立啟動檔,則控制項的`DoPropExchange`函數會呼叫`COleControl::DoPropExchange`。 基類版本交換控件的股票屬性;修改派生類的版本以交換已添加到控制項的屬性。

`CPropExchange`可用於在載入或創建控制項時序列化控制項的屬性或初始化控制項的屬性。 和`ExchangeProp``ExchangeFontProp`成員函數`CPropExchange`能夠將屬性存儲到並從不同的媒體載入它們。

有關`CPropExchange`使用的詳細資訊,請參閱文章[MFC ActiveX 控制件:屬性頁](../../mfc/mfc-activex-controls-property-pages.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CPropExchange`

## <a name="requirements"></a>需求

**標題:** afxctl.h

## <a name="cpropexchangeexchangeblobprop"></a><a name="exchangeblobprop"></a>CPropExchange::交換BlobProp

序列化儲存二進位大型物件 (BLOB) 資料的屬性。

```
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,
    HGLOBAL* phBlob,
    HGLOBAL hBlobDefault = NULL) = 0;
```

### <a name="parameters"></a>參數

*pszProp名稱*<br/>
要交換的屬性的名稱。

*phBlob*<br/>
指向指向屬性存儲位置的變數的指標(變數通常是類的成員)。

*hBlobDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

屬性的值從*phBlob*引用的變數讀取或寫入(視情況而定)。 如果指定*了 hBlobDefault,* 它將用作屬性的預設值。 如果由於任何原因,控件的序列化失敗,則使用此值。

函數`CArchivePropExchange::ExchangeBlobProp`,`CResetPropExchange::ExchangeBlobProp``CPropsetPropExchange::ExchangeBlobProp`並重寫此純虛擬函數。

## <a name="cpropexchangeexchangefontprop"></a><a name="exchangefontprop"></a>CPropExchange::交換方普羅普

在存儲介質和控件之間交換字體屬性。

```
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC* pFontDesc,
    LPFONTDISP pFontDispAmbient) = 0;
```

### <a name="parameters"></a>參數

*pszProp名稱*<br/>
要交換的屬性的名稱。

*字型*<br/>
對包含字體屬性的[CFontHolder](../../mfc/reference/cfontholder-class.md)物件的引用。

*普豐德斯茨*<br/>
指向[FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc)結構的指標,其中包含用於在*pFontDispAmbient*為 NULL 時初始化字體屬性的預設狀態的值。

*pFontDisp 環境*<br/>
指向用於初始化`IFontDisp`字體屬性的預設狀態的字體介面的指標。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

如果字體屬性從媒體載入到控制項,則從媒體中檢索字體的特徵,並且`CFontHolder`*使用字型*引用的物件進行初始化。 如果正在儲存字體屬性,則字體物件中的特徵將寫入介質。

函數`CArchivePropExchange::ExchangeFontProp`,`CResetPropExchange::ExchangeFontProp``CPropsetPropExchange::ExchangeFontProp`並重寫此純虛擬函數。

## <a name="cpropexchangeexchangepersistentprop"></a><a name="exchangepersistentprop"></a>CPropExchange::交換持久

在控制項和文件之間交換屬性。

```
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,
    LPUNKNOWN* ppUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault) = 0;
```

### <a name="parameters"></a>參數

*pszProp名稱*<br/>
要交換的屬性的名稱。

*普恩克*<br/>
指向包含指向屬性介面的指標的`IUnknown`變數的指標(此變數通常是類的成員)。

*Iid*<br/>
控制項將使用的屬性上的介面的介面的介面 ID。

*pUnkDefault*<br/>
屬性的預設值。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

如果屬性從檔載入到控制項,則從檔案創建和初始化該屬性。 如果正在存儲該屬性,則其值將寫入檔。

函數`CArchivePropExchange::ExchangePersistentProp`,`CResetPropExchange::ExchangePersistentProp``CPropsetPropExchange::ExchangePersistentProp`並重寫此純虛擬函數。

## <a name="cpropexchangeexchangeprop"></a><a name="exchangeprop"></a>CPropExchange:交換

在存儲介質和控制之間交換屬性。

```
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,
    VARTYPE vtProp,
    void* pvProp,
    const void* pvDefault = NULL) = 0 ;
```

### <a name="parameters"></a>參數

*pszProp名稱*<br/>
要交換的屬性的名稱。

*vtProp*<br/>
指定要交換的屬性類型的符號。 可能的值包括：

|符號|屬性類型|
|------------|-------------------|
|VT_I2|**short**|
|VT_I4|**長**|
|VT_BOOL|**Bool**|
|VT_BSTR|`CString`|
|VT_CY|**CY**|
|VT_R4|**浮動**|
|VT_R8|**double**|

*pvProp*<br/>
指向屬性值的指標。

*pvDefault*<br/>
指向屬性的預設值的指標。

### <a name="return-value"></a>傳回值

如果交換成功,則非零;0,如果不成功。

### <a name="remarks"></a>備註

如果屬性從媒體載入到控制項,則從媒體檢索該屬性的值並存儲在*pvProp*指向的物件中。 如果屬性被儲存到媒體,*則 pvProp*指向的物件的值將寫入媒體。

函數`CArchivePropExchange::ExchangeProp`,`CResetPropExchange::ExchangeProp``CPropsetPropExchange::ExchangeProp`並重寫此純虛擬函數。

## <a name="cpropexchangeexchangeversion"></a><a name="exchangeversion"></a>CPropExchange:交換版本

由框架調用來處理版本號的持久性。

```
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,
    DWORD dwVersionDefault,
    BOOL bConvert);
```

### <a name="parameters"></a>參數

*dwVersionLoaded*<br/>
引用將存儲要載入的持久資料的版本號的變數。

*dwVersionDefault*<br/>
控件的當前版本號。

*b轉換*<br/>
指示是將持久性數據轉換為當前版本,還是將其保留在載入的相同版本。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;0 否則。

## <a name="cpropexchangegetversion"></a><a name="getversion"></a>CPropExchange:取得版本

調用此函數以檢索控制件的版本號。

```
DWORD GetVersion();
```

### <a name="return-value"></a>傳回值

控件的版本號。

## <a name="cpropexchangeisasynchronous"></a><a name="isasynchronous"></a>CPropExchange:是同步的

確定屬換是否異步完成。

```
BOOL IsAsynchronous();
```

### <a name="return-value"></a>傳回值

如果以非同步方式交換屬性,則返回 TRUE,否則為 FALSE。

## <a name="cpropexchangeisloading"></a><a name="isloading"></a>CPropExchange:正在載入

調用此函數以確定屬性是載入到控制項還是從控制項中保存。

```
BOOL IsLoading();
```

### <a name="return-value"></a>傳回值

如果正在載入屬性,則非零;否則 0。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleControl::DoPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)
