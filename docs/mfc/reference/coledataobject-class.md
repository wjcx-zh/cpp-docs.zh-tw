---
title: COleDataObject 類別
ms.date: 11/04/2016
f1_keywords:
- COleDataObject
- AFXOLE/COleDataObject
- AFXOLE/COleDataObject::COleDataObject
- AFXOLE/COleDataObject::Attach
- AFXOLE/COleDataObject::AttachClipboard
- AFXOLE/COleDataObject::BeginEnumFormats
- AFXOLE/COleDataObject::Detach
- AFXOLE/COleDataObject::GetData
- AFXOLE/COleDataObject::GetFileData
- AFXOLE/COleDataObject::GetGlobalData
- AFXOLE/COleDataObject::GetNextFormat
- AFXOLE/COleDataObject::IsDataAvailable
- AFXOLE/COleDataObject::Release
helpviewer_keywords:
- COleDataObject [MFC], COleDataObject
- COleDataObject [MFC], Attach
- COleDataObject [MFC], AttachClipboard
- COleDataObject [MFC], BeginEnumFormats
- COleDataObject [MFC], Detach
- COleDataObject [MFC], GetData
- COleDataObject [MFC], GetFileData
- COleDataObject [MFC], GetGlobalData
- COleDataObject [MFC], GetNextFormat
- COleDataObject [MFC], IsDataAvailable
- COleDataObject [MFC], Release
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
ms.openlocfilehash: e706489a84ad564949e2c2d3d193173fc19b9828
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883645"
---
# <a name="coledataobject-class"></a>COleDataObject 類別

用於資料傳輸以透過剪貼簿、拖放作業或內嵌 OLE 項目擷取各種格式的資料。

## <a name="syntax"></a>語法

```
class COleDataObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleDataObject：： COleDataObject](#coledataobject)|建構 `COleDataObject` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDataObject：： Attach](#attach)|將指定的 OLE 資料物件附加至 `COleDataObject`。|
|[COleDataObject：： AttachClipboard](#attachclipboard)|附加位於剪貼簿上的資料物件。|
|[COleDataObject：： BeginEnumFormats](#beginenumformats)|準備一或多個後續的 `GetNextFormat` 呼叫。|
|[COleDataObject：:D etach](#detach)|卸離關聯的 `IDataObject` 物件。|
|[COleDataObject：：操作](#getdata)|以指定的格式從附加的 OLE 資料物件複製資料。|
|[COleDataObject：： GetFileData](#getfiledata)|以指定的格式，將資料從附加的 OLE 資料物件複製到 `CFile` 指標。|
|[COleDataObject：： GetGlobalData](#getglobaldata)|以指定的格式，將資料從附加的 OLE 資料物件複製到 `HGLOBAL`。|
|[COleDataObject：： GetNextFormat](#getnextformat)|傳回下一個可用的資料格式。|
|[COleDataObject：： IsDataAvailable](#isdataavailable)|檢查資料是否以指定的格式提供。|
|[COleDataObject：： Release](#release)|卸離和釋放關聯的 `IDataObject` 物件。|

## <a name="remarks"></a>備註

`COleDataObject` 沒有基類。

這類資料傳輸包含來源和目的地。 資料來源會實作為[COleDataSource](../../mfc/reference/coledatasource-class.md)類別的物件。 每當目的地應用程式已捨棄資料，或要求從剪貼簿執行貼上作業時，就必須建立 `COleDataObject` 類別的物件。

這個類別可讓您判斷資料是否以指定的格式存在。 您也可以列舉可用的資料格式，或檢查給定的格式是否可用，然後以慣用的格式抓取資料。 物件抓取可以透過數種不同的方式來完成，包括使用[CFile](../../mfc/reference/cfile-class.md)、HGLOBAL 或 `STGMEDIUM` 結構。

如需詳細資訊，請參閱 Windows SDK 中的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構。

如需在應用程式中使用資料物件的詳細資訊，請參閱[資料物件和資料來源（OLE）](../../mfc/data-objects-and-data-sources-ole.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

`COleDataObject`

## <a name="requirements"></a>需求

**標頭：** afxole。h

##  <a name="attach"></a>COleDataObject：： Attach

呼叫此函式可將 `COleDataObject` 物件與 OLE 資料物件產生關聯。

```
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>參數

*lpDataObject*<br/>
指向 OLE 資料物件。

*bAutoRelease*<br/>
如果應該在終結 `COleDataObject` 物件時釋放 OLE 資料物件，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) 。

##  <a name="attachclipboard"></a>COleDataObject：： AttachClipboard

呼叫此函式，將目前在剪貼簿上的資料物件附加至 `COleDataObject` 物件。

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

> [!NOTE]
>  呼叫這個函式會鎖定剪貼簿，直到釋放此資料物件為止。 資料物件會在 `COleDataObject`的析構函式中發行。 如需詳細資訊，請參閱 Win32 檔中的[OpenClipboard](/windows/win32/api/winuser/nf-winuser-openclipboard)和[CloseClipboard](/windows/win32/api/winuser/nf-winuser-closeclipboard) 。

##  <a name="beginenumformats"></a>COleDataObject：： BeginEnumFormats

呼叫此函式以準備後續呼叫 `GetNextFormat`，以從專案中抓取資料格式清單。

```
void BeginEnumFormats();
```

### <a name="remarks"></a>備註

呼叫 `BeginEnumFormats`之後，就會儲存這個資料物件所支援之第一個格式的位置。 後續呼叫 `GetNextFormat` 將會列舉資料物件中的可用格式清單。

若要以指定的格式檢查資料的可用性，請使用[COleDataObject：： IsDataAvailable](#isdataavailable)。

如需詳細資訊，請參閱 Windows SDK 中的[IDataObject：： EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) 。

##  <a name="coledataobject"></a>COleDataObject：： COleDataObject

建構 `COleDataObject` 物件。

```
COleDataObject();
```

### <a name="remarks"></a>備註

呼叫[COleDataObject：： Attach](#attach)或[COleDataObject：： AttachClipboard](#attachclipboard)之前，必須先進行呼叫，才能呼叫其他 `COleDataObject` 函數。

> [!NOTE]
>  由於拖放處理常式的其中一個參數是指向 `COleDataObject`的指標，因此不需要呼叫此函式來支援拖放。

##  <a name="detach"></a>COleDataObject：:D etach

呼叫此函式可從其相關聯的 OLE 資料物件卸離 `COleDataObject` 物件，而不會釋出資料物件。

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>傳回值

已卸離之 OLE 資料物件的指標。

### <a name="remarks"></a>備註

##  <a name="getdata"></a>COleDataObject：：操作

呼叫此函式，以指定的格式從專案中取出資料。

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要傳回資料的格式。 這個參數可以是預先定義的剪貼簿格式之一，或是原生 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數所傳回的值。

*lpStgMedium*<br/>
指向將接收資料的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構。

*lpFormatEtc*<br/>
指向描述要傳回資料之格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果您想要指定超出*cfFormat*所指定剪貼簿格式的其他格式資訊，請提供此參數的值。 如果它是 Null，則預設值會用於 `FORMATETC` 結構中的其他欄位。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的[IDataObject：：](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 。

如需詳細資訊，請參閱 Windows SDK 中的[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

##  <a name="getfiledata"></a>COleDataObject：： GetFileData

呼叫此函式來建立 `CFile` 或 `CFile`衍生的物件，並將指定格式的資料抓取至 `CFile` 指標。

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要傳回資料的格式。 這個參數可以是預先定義的剪貼簿格式之一，或是原生 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數所傳回的值。

*lpFormatEtc*<br/>
指向描述要傳回資料之格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果您想要指定超出*cfFormat*所指定剪貼簿格式的其他格式資訊，請提供此參數的值。 如果它是 Null，則預設值會用於 `FORMATETC` 結構中的其他欄位。

### <a name="return-value"></a>傳回值

如果成功，則為包含資料的新 `CFile` 或 `CFile`衍生物件的指標;否則為 Null。

### <a name="remarks"></a>備註

根據儲存資料的媒體，傳回值所指向的實際類型可能會 `CFile`、`CSharedFile`或 `COleStreamFile`。

> [!NOTE]
>  這個函式的傳回值所存取的 `CFile` 物件是由呼叫端所擁有。 呼叫者必須負責**刪除**`CFile` 物件，因此會關閉檔案。

如需詳細資訊，請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 。

如需詳細資訊，請參閱 Windows SDK 中的[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

##  <a name="getglobaldata"></a>COleDataObject：： GetGlobalData

呼叫此函式可配置全域記憶體區塊，以及將指定格式的資料抓取至 HGLOBAL。

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要傳回資料的格式。 這個參數可以是預先定義的剪貼簿格式之一，或是原生 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數所傳回的值。

*lpFormatEtc*<br/>
指向描述要傳回資料之格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果您想要指定超出*cfFormat*所指定剪貼簿格式的其他格式資訊，請提供此參數的值。 如果它是 Null，則預設值會用於 `FORMATETC` 結構中的其他欄位。

### <a name="return-value"></a>傳回值

如果成功，則為包含資料的全域記憶體區塊的控制碼;否則為 Null。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 。

如需詳細資訊，請參閱 Windows SDK 中的[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

##  <a name="getnextformat"></a>COleDataObject：： GetNextFormat

重複呼叫此函式，以取得可用於從專案中抓取資料的所有格式。

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向在函式呼叫傳回時接收格式資訊的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。

### <a name="return-value"></a>傳回值

如果有其他格式，則為非零;否則為0。

### <a name="remarks"></a>備註

呼叫[COleDataObject：： BeginEnumFormats](#beginenumformats)之後，會儲存這個資料物件所支援的第一個格式位置。 後續呼叫 `GetNextFormat` 將會列舉資料物件中的可用格式清單。 使用這些函數來列出可用的格式。

若要檢查指定格式的可用性，請呼叫[COleDataObject：： IsDataAvailable](#isdataavailable)。

如需詳細資訊，請參閱 Windows SDK 中的[IEnumXXXX：： Next](/previous-versions//ms695273\(v=vs.85\)) 。

##  <a name="isdataavailable"></a>COleDataObject：： IsDataAvailable

呼叫此函式可判斷是否有特定的格式可用於從 OLE 專案中抓取資料。

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要在*lpFormatEtc*所指向的結構中使用的剪貼簿資料格式。 這個參數可以是預先定義的剪貼簿格式之一，或是原生 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數所傳回的值。

*lpFormatEtc*<br/>
指向描述所需格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 只有當您想要指定超出*cfFormat*所指定剪貼簿格式的其他格式資訊時，才提供此參數的值。 如果它是 Null，則預設值會用於 `FORMATETC` 結構中的其他欄位。

### <a name="return-value"></a>傳回值

如果資料是以指定的格式提供，則為非零值;否則為0。

### <a name="remarks"></a>備註

此函式在呼叫 `GetData`、`GetFileData`或 `GetGlobalData`之前很有用。

如需詳細資訊，請參閱 Windows SDK 中的[IDataObject：： QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata)和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 。

如需詳細資訊，請參閱 Windows SDK 中的[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

### <a name="example"></a>範例

  請參閱[CRichEditView：： QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata)的範例。

##  <a name="release"></a>COleDataObject：： Release

呼叫此函式以釋放先前與 `COleDataObject` 物件相關聯的[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)物件擁有權。

```
void Release();
```

### <a name="remarks"></a>備註

`IDataObject` 是與 `COleDataObject` 相關聯，方法是明確地呼叫 `Attach` 或 `AttachClipboard` 或架構。 如果 `Attach` 的*bAutoRelease*參數為 FALSE，則不會釋放 `IDataObject` 物件。 在此情況下，呼叫者會負責呼叫[IUnknown：： Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)來釋放 `IDataObject`。

## <a name="see-also"></a>另請參閱

[MFC 範例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDataSource 類別](../../mfc/reference/coledatasource-class.md)<br/>
[COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)
