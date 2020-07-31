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
ms.openlocfilehash: 4a24fcab0eb34bbba597ba0b5c1fac22a929c0c0
ms.sourcegitcommit: 13f42c339fb7af935e3a93ac80e350d5e784c9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2020
ms.locfileid: "87470910"
---
# <a name="coledataobject-class"></a>COleDataObject 類別

用於資料傳輸以透過剪貼簿、拖放作業或內嵌 OLE 項目擷取各種格式的資料。

## <a name="syntax"></a>語法

```
class COleDataObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[COleDataObject：： COleDataObject](#coledataobject)|建構 `COleDataObject` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[COleDataObject：： Attach](#attach)|將指定的 OLE 資料物件附加至 `COleDataObject` 。|
|[COleDataObject：： AttachClipboard](#attachclipboard)|附加位於剪貼簿上的資料物件。|
|[COleDataObject：： BeginEnumFormats](#beginenumformats)|準備一或多個後續 `GetNextFormat` 呼叫。|
|[COleDataObject：:D etach](#detach)|卸離關聯的 `IDataObject` 物件。|
|[COleDataObject：：操作](#getdata)|以指定的格式從附加的 OLE 資料物件複製資料。|
|[COleDataObject：： GetFileData](#getfiledata)|將資料從附加的 OLE 資料物件複製到 `CFile` 指定格式的指標。|
|[COleDataObject：： GetGlobalData](#getglobaldata)|以指定的格式，將資料從附加的 OLE 資料物件複製到 `HGLOBAL` 中。|
|[COleDataObject：： GetNextFormat](#getnextformat)|傳回下一個可用的資料格式。|
|[COleDataObject：： IsDataAvailable](#isdataavailable)|檢查資料是否以指定的格式提供。|
|[COleDataObject：： Release](#release)|卸離和釋放關聯的 `IDataObject` 物件。|

## <a name="remarks"></a>備註

`COleDataObject`沒有基類。

這類資料傳輸包含來源和目的地。 資料來源會實作為[COleDataSource](../../mfc/reference/coledatasource-class.md)類別的物件。 每當目的地應用程式已捨棄資料，或要求從剪貼簿執行貼上作業時，就 `COleDataObject` 必須建立類別的物件。

這個類別可讓您判斷資料是否以指定的格式存在。 您也可以列舉可用的資料格式，或檢查給定的格式是否可用，然後以慣用的格式抓取資料。 物件抓取可以透過數種不同的方式來完成，包括使用[CFile](../../mfc/reference/cfile-class.md)、HGLOBAL 或 `STGMEDIUM` 結構。

如需詳細資訊，請參閱 Windows SDK 中的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1)結構。

如需在應用程式中使用資料物件的詳細資訊，請參閱[資料物件和資料來源（OLE）](../../mfc/data-objects-and-data-sources-ole.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`COleDataObject`

## <a name="requirements"></a>需求

**標頭：** afxole。h

## <a name="coledataobjectattach"></a><a name="attach"></a>COleDataObject：： Attach

呼叫此函式可將 `COleDataObject` 物件與 OLE 資料物件產生關聯。

```cpp
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>參數

*lpDataObject*<br/>
指向 OLE 資料物件。

*bAutoRelease*<br/>
如果要在終結物件時釋放 OLE 資料物件，則為 TRUE， `COleDataObject` 否則為 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) 。

## <a name="coledataobjectattachclipboard"></a><a name="attachclipboard"></a>COleDataObject：： AttachClipboard

呼叫此函式，將目前在剪貼簿上的資料物件附加至 `COleDataObject` 物件。

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

> [!NOTE]
> 呼叫這個函式會鎖定剪貼簿，直到釋放此資料物件為止。 資料物件會在的析構函式中釋放 `COleDataObject` 。 如需詳細資訊，請參閱 Win32 檔中的[OpenClipboard](/windows/win32/api/winuser/nf-winuser-openclipboard)和[CloseClipboard](/windows/win32/api/winuser/nf-winuser-closeclipboard) 。

## <a name="coledataobjectbeginenumformats"></a><a name="beginenumformats"></a>COleDataObject：： BeginEnumFormats

呼叫此函式以準備後續呼叫，以 `GetNextFormat` 從專案中抓取資料格式清單。

```cpp
void BeginEnumFormats();
```

### <a name="remarks"></a>備註

呼叫之後 `BeginEnumFormats` ，會儲存這個資料物件所支援之第一個格式的位置。 後續的呼叫 `GetNextFormat` 將會列舉資料物件中的可用格式清單。

若要以指定的格式檢查資料的可用性，請使用[COleDataObject：： IsDataAvailable](#isdataavailable)。

如需詳細資訊，請參閱 Windows SDK 中的[IDataObject：： EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) 。

## <a name="coledataobjectcoledataobject"></a><a name="coledataobject"></a>COleDataObject：： COleDataObject

建構 `COleDataObject` 物件。

```
COleDataObject();
```

### <a name="remarks"></a>備註

呼叫[COleDataObject：： Attach](#attach)或[COleDataObject：： AttachClipboard](#attachclipboard)之前，必須先進行呼叫，再呼叫其他函式 `COleDataObject` 。

> [!NOTE]
> 由於拖放處理常式的其中一個參數是的指標 `COleDataObject` ，因此不需要呼叫此函式來支援拖放。

## <a name="coledataobjectdetach"></a><a name="detach"></a>COleDataObject：:D etach

呼叫此函式可 `COleDataObject` 從其相關聯的 OLE 資料物件中斷連結化物件，而不需要釋放資料物件。

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>傳回值

已卸離之 OLE 資料物件的指標。

### <a name="remarks"></a>備註

## <a name="coledataobjectgetdata"></a><a name="getdata"></a>COleDataObject：：操作

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
指向將接收資料的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1)結構。

*lpFormatEtc*<br/>
指向描述要傳回資料之格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果您想要指定超出*cfFormat*所指定剪貼簿格式的其他格式資訊，請提供此參數的值。 如果它是 Null，則會將預設值用於結構中的其他欄位 `FORMATETC` 。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的[IDataObject：：](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1)和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 。

如需詳細資訊，請參閱 Windows SDK 中的[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

## <a name="coledataobjectgetfiledata"></a><a name="getfiledata"></a>COleDataObject：： GetFileData

呼叫此函式可建立 `CFile` 或 `CFile` 衍生物件，並將指定格式的資料抓取到指標中 `CFile` 。

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要傳回資料的格式。 這個參數可以是預先定義的剪貼簿格式之一，或是原生 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數所傳回的值。

*lpFormatEtc*<br/>
指向描述要傳回資料之格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果您想要指定超出*cfFormat*所指定剪貼簿格式的其他格式資訊，請提供此參數的值。 如果它是 Null，則會將預設值用於結構中的其他欄位 `FORMATETC` 。

### <a name="return-value"></a>傳回值

如果成功，則 `CFile` 為 `CFile` 包含資料的新或衍生物件的指標; 否則為 Null。

### <a name="remarks"></a>備註

根據儲存資料的媒體，傳回值所指向的實際型別可以是 `CFile` 、 `CSharedFile` 或 `COleStreamFile` 。

> [!NOTE]
> 這個函式 `CFile` 的傳回值所存取的物件是由呼叫端所擁有。 這是呼叫者對物件的責任 **`delete`** `CFile` ，因而關閉檔案。

如需詳細資訊，請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 。

如需詳細資訊，請參閱 Windows SDK 中的[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

## <a name="coledataobjectgetglobaldata"></a><a name="getglobaldata"></a>COleDataObject：： GetGlobalData

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
指向描述要傳回資料之格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果您想要指定超出*cfFormat*所指定剪貼簿格式的其他格式資訊，請提供此參數的值。 如果它是 Null，則會將預設值用於結構中的其他欄位 `FORMATETC` 。

### <a name="return-value"></a>傳回值

如果成功，則為包含資料的全域記憶體區塊的控制碼;否則為 Null。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 。

如需詳細資訊，請參閱 Windows SDK 中的[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

## <a name="coledataobjectgetnextformat"></a><a name="getnextformat"></a>COleDataObject：： GetNextFormat

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

呼叫[COleDataObject：： BeginEnumFormats](#beginenumformats)之後，會儲存這個資料物件所支援的第一個格式位置。 後續的呼叫 `GetNextFormat` 將會列舉資料物件中的可用格式清單。 使用這些函數來列出可用的格式。

若要檢查指定格式的可用性，請呼叫[COleDataObject：： IsDataAvailable](#isdataavailable)。

如需詳細資訊，請參閱 Windows SDK 中的[IEnumXXXX：： Next](/previous-versions/ms695273\(v=vs.85\)) 。

## <a name="coledataobjectisdataavailable"></a><a name="isdataavailable"></a>COleDataObject：： IsDataAvailable

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
指向描述所需格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 只有當您想要指定超出*cfFormat*所指定剪貼簿格式的其他格式資訊時，才提供此參數的值。 如果它是 Null，則會將預設值用於結構中的其他欄位 `FORMATETC` 。

### <a name="return-value"></a>傳回值

如果資料是以指定的格式提供，則為非零值;否則為0。

### <a name="remarks"></a>備註

此函式在呼叫、或之前很有用 `GetData` `GetFileData` `GetGlobalData` 。

如需詳細資訊，請參閱 Windows SDK 中的[IDataObject：： QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata)和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 。

如需詳細資訊，請參閱 Windows SDK 中的[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

### <a name="example"></a>範例

  請參閱[CRichEditView：： QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata)的範例。

## <a name="coledataobjectrelease"></a><a name="release"></a>COleDataObject：： Release

呼叫此函式以釋放先前與物件相關聯的[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)物件擁有權 `COleDataObject` 。

```cpp
void Release();
```

### <a name="remarks"></a>備註

`IDataObject`已藉 `COleDataObject` 由呼叫 `Attach` 或 `AttachClipboard` 明確或由架構來與建立關聯。 如果的*bAutoRelease*參數 `Attach` 為 FALSE，則 `IDataObject` 不會釋放物件。 在此情況下，呼叫者會負責 `IDataObject` 呼叫[IUnknown：： Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)來釋放。

## <a name="see-also"></a>請參閱

[MFC 範例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDataSource 類別](../../mfc/reference/coledatasource-class.md)<br/>
[COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)
