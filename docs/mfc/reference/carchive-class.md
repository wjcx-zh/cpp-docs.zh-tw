---
title: CArchive 類別
ms.date: 11/04/2016
f1_keywords:
- CArchive
- AFX/CArchive
- AFX/CArchive::CArchive
- AFX/CArchive::Abort
- AFX/CArchive::Close
- AFX/CArchive::Flush
- AFX/CArchive::GetFile
- AFX/CArchive::GetObjectSchema
- AFX/CArchive::IsBufferEmpty
- AFX/CArchive::IsLoading
- AFX/CArchive::IsStoring
- AFX/CArchive::MapObject
- AFX/CArchive::Read
- AFX/CArchive::ReadClass
- AFX/CArchive::ReadObject
- AFX/CArchive::ReadString
- AFX/CArchive::SerializeClass
- AFX/CArchive::SetLoadParams
- AFX/CArchive::SetObjectSchema
- AFX/CArchive::SetStoreParams
- AFX/CArchive::Write
- AFX/CArchive::WriteClass
- AFX/CArchive::WriteObject
- AFX/CArchive::WriteString
- AFX/CArchive::m_pDocument
helpviewer_keywords:
- CArchive [MFC], CArchive
- CArchive [MFC], Abort
- CArchive [MFC], Close
- CArchive [MFC], Flush
- CArchive [MFC], GetFile
- CArchive [MFC], GetObjectSchema
- CArchive [MFC], IsBufferEmpty
- CArchive [MFC], IsLoading
- CArchive [MFC], IsStoring
- CArchive [MFC], MapObject
- CArchive [MFC], Read
- CArchive [MFC], ReadClass
- CArchive [MFC], ReadObject
- CArchive [MFC], ReadString
- CArchive [MFC], SerializeClass
- CArchive [MFC], SetLoadParams
- CArchive [MFC], SetObjectSchema
- CArchive [MFC], SetStoreParams
- CArchive [MFC], Write
- CArchive [MFC], WriteClass
- CArchive [MFC], WriteObject
- CArchive [MFC], WriteString
- CArchive [MFC], m_pDocument
ms.assetid: 9e950d23-b874-456e-ae4b-fe00781a7699
ms.openlocfilehash: 3cf5c3b7a79e846928b5a7ee0af12a3324e141a3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855260"
---
# <a name="carchive-class"></a>CArchive 類別

可讓您以永久二進位格式（通常是磁片儲存體）儲存物件的複雜網路，這些物件會在刪除這些物件之後保存。

## <a name="syntax"></a>語法

```
class CArchive
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CArchive：： CArchive](#carchive)|建立 `CArchive` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CArchive：： Abort](#abort)|關閉封存，而不擲回例外狀況。|
|[CArchive：： Close](#close)|排清不成文的資料，並從 `CFile`中斷連接。|
|[CArchive：： Flush](#flush)|排清不成文封存緩衝區中的資料。|
|[CArchive：： GetFile](#getfile)|取得此封存的 `CFile` 物件指標。|
|[CArchive：： GetObjectSchema](#getobjectschema)|從 `Serialize` 函式呼叫，以判斷正在還原序列化的物件版本。|
|[CArchive：： IsBufferEmpty](#isbufferempty)|判斷在 Windows 通訊端接收進程期間，緩衝區是否已清空。|
|[CArchive：： IsLoading](#isloading)|判斷是否正在載入封存。|
|[CArchive：： IsStoring](#isstoring)|判斷封存是否正在儲存。|
|[CArchive：： MapObject](#mapobject)|將物件放在對應中，而不會序列化為檔案，但可供子物件參考。|
|[CArchive：： Read](#read)|讀取原始位元組。|
|[CArchive：： ReadClass](#readclass)|讀取先前與 `WriteClass`儲存的類別參考。|
|[CArchive：： ReadObject](#readobject)|呼叫物件的 `Serialize` 函式以進行載入。|
|[CArchive：： ReadString](#readstring)|讀取一行文字。|
|[CArchive：： SerializeClass](#serializeclass)|根據 `CArchive`的方向，讀取或寫入 `CArchive` 物件的類別參考。|
|[CArchive：： SetLoadParams](#setloadparams)|設定負載陣列增加的大小。 必須在載入任何物件之前，或呼叫 `MapObject` 或 `ReadObject` 之前呼叫。|
|[CArchive：： SetObjectSchema](#setobjectschema)|設定儲存在 archive 物件中的物件架構。|
|[CArchive：： SetStoreParams](#setstoreparams)|設定在序列化過程中用來識別唯一物件之對應的雜湊資料表大小和區塊大小。|
|[CArchive：： Write](#write)|寫入原始位元組。|
|[CArchive：： WriteClass](#writeclass)|將 `CRuntimeClass` 的參考寫入 `CArchive`。|
|[CArchive：： WriteObject](#writeobject)|呼叫物件的 `Serialize` 函數來儲存。|
|[CArchive：： WriteString](#writestring)|寫入一行文字。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CArchive：： operator &lt;&lt;](#operator_lt_lt)|將物件和基本類型儲存至封存。|
|[CArchive：： operator &gt;&gt;](#operator_gt_gt)|從封存載入物件和基本類型。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CArchive：： m_pDocument](#m_pdocument)||

## <a name="remarks"></a>備註

`CArchive` 沒有基類。

稍後您可以從持續性儲存體載入物件，並在記憶體中重組它們。 這種讓資料持續的程式稱為「序列化」。

您可以將 archive 物件視為一種二進位資料流程。 如同輸入/輸出資料流程，封存會與檔案相關聯，並允許在儲存體之間進行資料的緩衝寫入和讀取。 輸入/輸出資料流程會處理 ASCII 字元的序列，但是封存會以有效率的 nonredundant 格式處理二進位物件資料。

您必須先建立[CFile](../../mfc/reference/cfile-class.md)物件，才能建立 `CArchive` 物件。 此外，您必須確定封存的負載/存放區狀態與檔案的開啟模式相容。 您的每個檔案只能有一個作用中封存。

當您建立 `CArchive` 物件時，您會將它附加至代表已開啟檔案之類別 `CFile` （或衍生類別）的物件。 您也可以指定是否要將封存用於載入或儲存。 `CArchive` 物件不僅可以處理基本類型，也能處理針對序列化而設計之[CObject](../../mfc/reference/cobject-class.md)衍生類別的物件。 可序列化的類別通常會有 `Serialize` 成員函式，而且通常會使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)宏，如類別 `CObject`底下所述。

多載的提取（ **>>** ）和插入（ **<<** ）運算子是方便的封存程式設計介面，可同時支援基本型別和 `CObject`衍生的類別。

`CArchive` 也支援以 MFC Windows 通訊端類別[CSocket](../../mfc/reference/csocket-class.md)和[CSocketFile](../../mfc/reference/csocketfile-class.md)進行程式設計。 [IsBufferEmpty](#isbufferempty)成員函式支援該使用方式。

如需 `CArchive`的詳細資訊，請參閱文章[序列化](../../mfc/serialization-in-mfc.md)和[Windows 通訊端：搭配使用通訊端與](../../mfc/windows-sockets-using-sockets-with-archives.md)封存。

## <a name="inheritance-hierarchy"></a>繼承階層

`CArchive`

## <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="abort"></a>CArchive：： Abort

呼叫此函式以關閉封存，而不擲回例外狀況。

```
void Abort ();
```

### <a name="remarks"></a>備註

`CArchive` 的函式通常會呼叫 `Close`，這會將尚未儲存的任何資料排清到相關聯的 `CFile` 物件。 這可能會造成例外狀況。

攔截這些例外狀況時，最好使用 `Abort`，讓 `CArchive` 物件銷毀不會造成進一步的例外狀況。 處理例外狀況時，`CArchive::Abort` 不會在失敗時擲回例外狀況，因為與[CArchive：： Close](#close)不同，`Abort` 會忽略失敗。

如果您使用**new**在堆積上配置 `CArchive` 物件，則必須在關閉檔案之後將其刪除。

### <a name="example"></a>範例

  請參閱[CArchive：： WriteClass](#writeclass)的範例。

##  <a name="carchive"></a>CArchive：： CArchive

會建立 `CArchive` 物件，並指定是否要使用它來載入或儲存物件。

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>參數

*pFile*<br/>
`CFile` 物件的指標，這是持續性資料的最終來源或目的地。

*nMode*<br/>
指定是否要從封存載入或儲存物件的旗標。 *NMode*參數必須具有下列其中一個值：

- `CArchive::load` 從封存載入資料。 只需要 `CFile` 讀取權限。

- `CArchive::store` 會將資料儲存至封存。 需要 `CFile` 寫入權限。

- `CArchive::bNoFlushOnDelete` 在呼叫封存的析構函式時，防止封存自動呼叫 `Flush`。 如果您設定此旗標，您必須負責在呼叫析構函式之前明確地呼叫 `Close`。 如果沒有這麼做，您的資料將會損毀。

*nBufSize*<br/>
指定內部檔案緩衝區大小（以位元組為單位）的整數。 請注意，預設緩衝區大小為4096個位元組。 如果您定期封存大型物件，當您使用的緩衝區大小大於檔案緩衝區大小的倍數時，將會改善效能。

*lpBuf*<br/>
使用者提供之*nBufSize*大小緩衝區的選擇性指標。 如果您未指定這個參數，封存就會從本機堆積配置緩衝區，並在終結物件時釋放它。 封存不會釋放使用者提供的緩衝區。

### <a name="remarks"></a>備註

建立封存之後，即無法變更此規格。

您不得使用 `CFile` 作業來改變檔案的狀態，直到您關閉封存為止。 任何這類作業都會損毀封存的完整性。 您可以在序列化期間隨時存取檔案指標的位置，方法是從[GetFile](#getfile)成員函式取得封存檔案物件，然後使用[CFile：： GetPosition](../../mfc/reference/cfile-class.md#getposition)函式。 在取得檔案指標的位置之前，您應該呼叫[CArchive：： Flush](#flush) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

##  <a name="close"></a>CArchive：： Close

排清緩衝區中剩餘的任何資料、關閉封存，然後中斷封存與檔案的連線。

```
void Close();
```

### <a name="remarks"></a>備註

不允許對封存進行進一步的作業。 關閉封存之後，您可以為相同的檔案建立另一個封存，或關閉檔案。

成員函式 `Close` 可確保所有資料都已從封存傳送到檔案，並使封存無法使用。 若要完成從檔案到儲存媒體的傳輸，您必須先使用[CFile：： Close](../../mfc/reference/cfile-class.md#close) ，然後終結 `CFile` 物件。

### <a name="example"></a>範例

  請參閱[CArchive：： WriteString](#writestring)的範例。

##  <a name="flush"></a>CArchive：： Flush

強制將封存緩衝區中剩餘的任何資料寫入檔案中。

```
void Flush();
```

### <a name="remarks"></a>備註

成員函式 `Flush` 可確保所有資料都會從封存傳送到檔案。 您必須呼叫[CFile：： Close](../../mfc/reference/cfile-class.md#close) ，才能完成從檔案到儲存媒體的傳輸。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

##  <a name="getfile"></a>CArchive：： GetFile

取得此封存的 `CFile` 物件指標。

```
CFile* GetFile() const;
```

### <a name="return-value"></a>傳回值

使用中 `CFile` 物件的常數指標。

### <a name="remarks"></a>備註

使用 `GetFile`之前，您必須先清除封存。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

##  <a name="getobjectschema"></a>CArchive：： GetObjectSchema

從 `Serialize` 函式呼叫此函式，以判斷目前正在還原序列化的物件版本。

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>傳回值

在還原序列化期間，要讀取的物件版本。

### <a name="remarks"></a>備註

只有在載入 `CArchive` 物件時，才會呼叫這個函式（ [CArchive：： IsLoading](#isloading)會傳回非零）。 它應該是 `Serialize` 函式中的第一個呼叫，而且只呼叫一次。 傳回值（UINT）-1 表示版本號碼不明。

`CObject`衍生的類別可以使用 VERSIONABLE_SCHEMA 結合（使用位**or**）與架構版本本身（在 IMPLEMENT_SERIAL 宏中）來建立「可控制版本物件」，也就是其 `Serialize` 成員函式可以讀取多個版本的物件。 預設的架構功能（不 VERSIONABLE_SCHEMA）是在版本不相符時擲回例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

##  <a name="isbufferempty"></a>CArchive：： IsBufferEmpty

呼叫這個成員函式，以判斷封存物件的內部緩衝區是否為空的。

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>傳回值

如果封存的緩衝區是空的，則為非零;否則為0。

### <a name="remarks"></a>備註

提供此函式是為了支援使用 MFC Windows 通訊端類別 `CSocketFile`進行程式設計。 您不需要將它用於與 `CFile` 物件相關聯的封存。

使用 `IsBufferEmpty` 與 `CSocketFile` 物件相關聯的封存的原因，是封存的緩衝區可能包含一個以上的訊息或記錄。 收到一則訊息之後，您應該使用 `IsBufferEmpty` 控制會繼續接收資料的迴圈，直到緩衝區是空的為止。 如需詳細資訊，請參閱類別 `CAsyncSocket`的 Receive 成員函式，其[會](../../mfc/reference/casyncsocket-class.md#receive)顯示如何使用 `IsBufferEmpty`。

如需詳細資訊，請參閱[Windows socket：搭配使用通訊端與](../../mfc/windows-sockets-using-sockets-with-archives.md)封存。

##  <a name="isloading"></a>CArchive：： IsLoading

判斷保存是否正在載入資料。

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>傳回值

如果封存目前用於載入，則為非零值;否則為0。

### <a name="remarks"></a>備註

這個成員函式是由封存類別的 `Serialize` 函式所呼叫。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

##  <a name="isstoring"></a>CArchive：： IsStoring

判斷封存是否正在儲存資料。

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>傳回值

如果封存目前用於儲存，則為非零值;否則為0。

### <a name="remarks"></a>備註

這個成員函式是由封存類別的 `Serialize` 函式所呼叫。

如果封存的 `IsStoring` 狀態為非零，則其 `IsLoading` 狀態為0，反之亦然。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

##  <a name="mapobject"></a>CArchive：： MapObject

呼叫這個成員函式，將物件放在對應中，而這些物件並未真正序列化為檔案，但可供子物件參考。

```
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>參數

*pOb*<br/>
要儲存之物件的常數指標。

### <a name="remarks"></a>備註

例如，您可能不會序列化檔，但您會序列化屬於檔的專案。 藉由呼叫 `MapObject`，您可以讓這些專案（或子物件）參考檔。 此外，序列化的子工作可以將其*m_pDocument*的反向指標序列化。

當您儲存並從 `CArchive` 物件載入時，可以呼叫 `MapObject`。 `MapObject` 會將指定的物件加入至在序列化和還原序列化期間由 `CArchive` 物件維護的內部資料結構，但與[ReadObject](#readobject)和[WriteObject](#writeobject)不同的是，它不會呼叫物件上的序列化。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

##  <a name="m_pdocument"></a>CArchive：： m_pDocument

設定為 Null：根據預設，此 `CDocument` 的指標可以設定為 `CArchive` 實例的使用者所需的任何專案。

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>備註

這個指標的常見用法是將有關序列化程式的其他資訊傳達給所有序列化的物件。 這是藉由使用序列化的檔（`CDocument`衍生類別）來初始化指標來達成，如此一來，檔內的物件就可以在必要時存取檔。 在序列化期間，`COleClientItem` 物件也會使用這個指標。

架構會在使用者發出檔案開啟或儲存命令時，將*m_pDocument*設定為要序列化的檔。 如果您針對檔案開啟或儲存以外的原因序列化物件連結和內嵌（OLE）容器檔案，則必須明確地設定*m_pDocument*。 例如，當您將容器檔案序列化至剪貼簿時，會執行這項操作。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

##  <a name="operator_lt_lt"></a>CArchive：： operator &lt;&lt;

將指定的物件或基本類型儲存至封存。

```
friend CArchive& operator<<(
    CArchive& ar,
    const CObject* pOb);

throw(
    CArchiveException*,
    CFileException*);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator<<(
    const ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator<<(BYTE by);
CArchive& operator<<(WORD w);
CArchive& operator<<(LONG l);
CArchive& operator<<(DWORD dw);
CArchive& operator<<(float f);
CArchive& operator<<(double d);
CArchive& operator<<(int i);
CArchive& operator<<(short w);
CArchive& operator<<(char ch);
CArchive& operator<<(wchar_t ch);
CArchive& operator<<(unsigned u);
CArchive& operator<<(bool b);
CArchive& operator<<(ULONGLONG dwdw);
CArchive& operator<<(LONGLONG dwdw);
```

### <a name="return-value"></a>傳回值

在單一行上啟用多個插入運算子的 `CArchive` 參考。

### <a name="remarks"></a>備註

上述的最後兩個版本專門用來儲存64位整數。

如果您在類別實中使用了 IMPLEMENT_SERIAL 宏，則對 `CObject` 進行多載的插入運算子會呼叫受保護的 `WriteObject`。 此函式接著會呼叫類別的 `Serialize` 函式。

[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)插入運算子（< <）支援將診斷傾印並儲存至封存。

### <a name="example"></a>範例

這個範例示範如何使用 `CArchive` 插入運算子，< < 和**int**和**long**類型。

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>範例

這個範例2示範如何使用 `CArchive` 插入運算子，< < 與 `CStringT` 型別。

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

##  <a name="operator_gt_gt"></a>CArchive：： operator &gt;&gt;

從封存載入指定的物件或基本類型。

```
friend CArchive& operator>>(
    CArchive& ar,
    CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

friend CArchive& operator>>(
    CArchive& ar,
    const CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator>>(
    ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator>>(BYTE& by);
CArchive& operator>>(WORD& w);
CArchive& operator>>(int& i);
CArchive& operator>>(LONG& l);
CArchive& operator>>(DWORD& dw);
CArchive& operator>>(float& f);
CArchive& operator>>(double& d);
CArchive& operator>>(short& w);
CArchive& operator>>(char& ch);
CArchive& operator>>(wchar_t& ch);
CArchive& operator>>(unsigned& u);
CArchive& operator>>(bool& b);
CArchive& operator>>(ULONGLONG& dwdw);
CArchive& operator>>(LONGLONG& dwdw);
```

### <a name="return-value"></a>傳回值

在單一行上啟用多個抽取運算子的 `CArchive` 參考。

### <a name="remarks"></a>備註

上述的最後兩個版本專門用來載入64位整數。

如果您在類別實中使用了 IMPLEMENT_SERIAL 宏，則 `CObject` 呼叫受保護的 `ReadObject` 函式（具有非零的執行時間類別指標），就會為多載的提取運算子。 此函式接著會呼叫類別的 `Serialize` 函式。

[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)解壓縮運算子（> >）支援從封存載入。

### <a name="example"></a>範例

這個範例示範如何使用 `CArchive` 的抽取運算子，> > 與**int**型別。

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>範例

這個範例示範如何使用 `CArchive` 的插入和抽取運算子，<\<，以及 > 類型的 > `CStringT`。

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

##  <a name="read"></a>CArchive：： Read

從封存讀取指定的位元組數目。

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
使用者提供之緩衝區的指標，用來接收從封存讀取的資料。

*N 上限*<br/>
不帶正負號的整數，指定要從封存中讀取的位元組數目。

### <a name="return-value"></a>傳回值

不帶正負號的整數，其中包含實際讀取的位元組數目。 如果傳回值小於所要求的數目，則已達到檔案結尾。 檔案結尾條件上不會擲回任何例外狀況。

### <a name="remarks"></a>備註

封存不會解讀位元組。

您可以使用 `Serialize` 函式內的 `Read` 成員函式，來讀取物件中包含的一般結構。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

##  <a name="readclass"></a>CArchive：： ReadClass

呼叫這個成員函式可讀取先前與[WriteClass](#writeclass)儲存之類別的參考。

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>參數

*pClassRefRequested*<br/>
對應至所要求類別參考之[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構的指標。 可以是 NULL。

*pSchema*<br/>
先前儲存之執行時間類別架構的指標。

*pObTag*<br/>
參考物件唯一標記的數位。 由[ReadObject](#readobject)的實作為內部使用。 僅針對先進的程式設計而公開;*pObTag*通常應該是 Null。

### <a name="return-value"></a>傳回值

[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構的指標。

### <a name="remarks"></a>備註

如果*pClassRefRequested*不是 Null，`ReadClass` 會確認封存的類別資訊與您的執行時間類別相容。 如果不相容，`ReadClass` 將會擲回[CArchiveException](../../mfc/reference/carchiveexception-class.md)。

您的執行時間類別必須使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial);否則，`ReadClass` 將會擲回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

如果*pSchema*為 Null，則可以藉由呼叫[CArchive：： GetObjectSchema](#getobjectschema)來抓取預存類別的架構。否則， <strong>\*</strong> *pSchema*會包含先前儲存之執行時間類別的架構。

您可以使用[SerializeClass](#serializeclass)而不是 `ReadClass`，這會同時處理類別參考的讀取和寫入。

### <a name="example"></a>範例

  請參閱[CArchive：： WriteClass](#writeclass)的範例。

##  <a name="readobject"></a>CArchive：： ReadObject

從封存讀取物件資料，並建立適當類型的物件。

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>參數

*pClass*<br/>
[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構的常數指標，其對應至您想要讀取的物件。

### <a name="return-value"></a>傳回值

必須使用[cobject：： IsKindOf](../../mfc/reference/cobject-class.md#iskindof)，安全地轉換成正確衍生類別的[CObject](../../mfc/reference/cobject-class.md)指標。

### <a name="remarks"></a>備註

此函式通常是由針對[CObject](../../mfc/reference/cobject-class.md)指標多載的 `CArchive` 抽取（ **>>** ）運算子所呼叫。 `ReadObject`，接著會呼叫封存類別的 `Serialize` 功能。

如果您提供非零的*pClass*參數（由[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)宏取得），則函式會驗證封存物件的執行時間類別。 這會假設您已在類別的執行中使用 IMPLEMENT_SERIAL 宏。

### <a name="example"></a>範例

  請參閱[CArchive：： WriteObject](#writeobject)的範例。

##  <a name="readstring"></a>CArchive：： ReadString

呼叫這個成員函式，從與 `CArchive` 物件相關聯的檔案中，將文字資料讀取至緩衝區。

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>參數

*rString*<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)的參考，在從與 CArchive 物件相關聯的檔案中讀取後，將包含結果字串。

*lpsz*<br/>
指定使用者提供之緩衝區的指標，此緩衝區將會接收以 null 結束的文字字串。

*N 上限*<br/>
指定要讀取的最大字元數。 應小於*lpsz*緩衝區的大小。

### <a name="return-value"></a>傳回值

在傳回 BOOL 的版本中，如果成功，則為 TRUE;否則為 FALSE。

在傳回 `LPTSTR`的版本中，包含文字資料的緩衝區指標。如果已到達檔案結尾，則為 Null。

### <a name="remarks"></a>備註

在具有*n 上限*參數的成員函式版本中，緩衝區最多會保留*n 上限*-1 個字元的限制。 讀取是由一組換行的傳回線所停止。 一律會移除尾端分行符號。 在任一情況下，都會附加 null 字元（' \ 0 '）。

[CArchive：： Read](#read)也適用于文字模式輸入，但它不會在換行的傳回分行符號時結束。

### <a name="example"></a>範例

  請參閱[CArchive：： WriteString](#writestring)的範例。

##  <a name="serializeclass"></a>CArchive：： SerializeClass

當您想要儲存和載入基類的版本資訊時，請呼叫這個成員函式。

```
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>參數

*pClassRef*<br/>
基類之執行時間類別物件的指標。

### <a name="remarks"></a>備註

`SerializeClass` 會根據 `CArchive`的方向，讀取或寫入類別到 `CArchive` 物件的參考。 使用 `SerializeClass` 取代[ReadClass](#readclass)和[WriteClass](#writeclass) ，以方便您序列化基類物件;`SerializeClass` 需要較少的程式碼和較少的參數。

如同 `ReadClass`，`SerializeClass` 會確認封存的類別資訊與您的執行時間類別相容。 如果不相容，`SerializeClass` 將會擲回[CArchiveException](../../mfc/reference/carchiveexception-class.md)。

您的執行時間類別必須使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial);否則，`SerializeClass` 將會擲回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

使用[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)宏來取出*pRuntimeClass*參數的值。 基類必須使用[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)宏。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

##  <a name="setloadparams"></a>CArchive：： SetLoadParams

當您要從封存讀取大量的 `CObject`衍生物件時，請呼叫 `SetLoadParams`。

```
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>參數

*nGrowBy*<br/>
如果需要增加大小，要配置的元素位置數目下限。

### <a name="remarks"></a>備註

`CArchive` 使用載入陣列來解析封存檔案中所儲存之物件的參考。 `SetLoadParams` 可讓您設定負載陣列所增加的大小。

在載入任何物件之後，或在呼叫[MapObject](#mapobject)或[ReadObject](#readobject)之後，您都不能呼叫 `SetLoadParams`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="setobjectschema"></a>CArchive：： SetObjectSchema

呼叫這個成員函式，將儲存在封存物件中的物件架構設定為*nSchema*。

```
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>參數

*nSchema*<br/>
指定物件的架構。

### <a name="remarks"></a>備註

下一次呼叫[GetObjectSchema](#getobjectschema)時，將會傳回儲存在*nSchema*中的值。

使用 `SetObjectSchema` 進行 advanced 版本設定;例如，當您想要強制在衍生類別的 `Serialize` 函式中讀取特定版本時。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

##  <a name="setstoreparams"></a>CArchive：： SetStoreParams

在封存中儲存大量 `CObject`衍生的物件時，請使用 `SetStoreParams`。

```
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>參數

*nHashSize*<br/>
介面指標對應的雜湊表大小。 應該是質數。

*nBlockSize*<br/>
指定擴充參數的記憶體配置資料細微性。 應該是2的乘冪，才能獲得最佳效能。

### <a name="remarks"></a>備註

`SetStoreParams` 可讓您設定雜湊表大小，以及在序列化過程中用來識別唯一物件的對應區塊大小。

您不能在儲存任何物件之後，或在呼叫[MapObject](#mapobject)或[WriteObject](#writeobject)之後呼叫 `SetStoreParams`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="write"></a>CArchive：： Write

將指定的位元組數目寫入封存。

```
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
使用者提供之緩衝區的指標，其中包含要寫入封存的資料。

*N 上限*<br/>
整數，指定要寫入封存的位元組數目。

### <a name="remarks"></a>備註

封存不會格式化位元組。

您可以使用 `Serialize` 函式內的 `Write` 成員函式，來撰寫物件中包含的一般結構。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

##  <a name="writeclass"></a>CArchive：： WriteClass

在序列化衍生類別期間，使用 `WriteClass` 來儲存基類的版本和類別資訊。

```
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>參數

*pClassRef*<br/>
對應至所要求類別參考之[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構的指標。

### <a name="remarks"></a>備註

`WriteClass` 會將基類的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)參考寫入 `CArchive`。 使用[CArchive：： ReadClass](#readclass)來取出參考。

`WriteClass` 確認封存的類別資訊與您的執行時間類別相容。 如果不相容，`WriteClass` 將會擲回[CArchiveException](../../mfc/reference/carchiveexception-class.md)。

您的執行時間類別必須使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial);否則，`WriteClass` 將會擲回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

您可以使用[SerializeClass](#serializeclass)而不是 `WriteClass`，這會同時處理類別參考的讀取和寫入。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

##  <a name="writeobject"></a>CArchive：： WriteObject

將指定的 `CObject` 儲存至封存。

```
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>參數

*pOb*<br/>
要儲存之物件的常數指標。

### <a name="remarks"></a>備註

此函式通常是由針對 `CObject`所多載的 `CArchive` 插入（ **<<** ）運算子所呼叫。 `WriteObject`，接著會呼叫封存類別的 `Serialize` 功能。

您必須使用 IMPLEMENT_SERIAL 宏來啟用封存。 `WriteObject` 會將 ASCII 類別名稱寫入封存。 此類別名稱稍後會在載入過程中進行驗證。 特殊的編碼配置會針對類別的多個物件避免不必要的類別名稱重複。 此配置也可防止以多個指標為目標之物件的重複儲存。

確切的物件編碼方法（包括 ASCII 類別名稱的存在）是一個執行詳細資料，而且可能會在程式庫的未來版本中變更。

> [!NOTE]
>  開始封存之前，請先完成建立、刪除和更新所有物件。 如果您混用了物件修改的封存，封存將會損毀。

### <a name="example"></a>範例

如需類別 `CAge`的定義，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist)的範例。

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

##  <a name="writestring"></a>CArchive：： WriteString

使用此成員函式，將緩衝區中的資料寫入與 `CArchive` 物件相關聯的檔案。

```
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>參數

*lpsz*<br/>
指定包含以 null 結束之文字字串的緩衝區指標。

### <a name="remarks"></a>備註

終止的 null 字元（' \ 0 '）不會寫入檔案;也不是自動寫入的新行。

`WriteString` 會擲回例外狀況，以回應數個條件，包括磁片完整的條件。

`Write` 也可以使用，但不會在 null 字元上終止，而是會將要求的位元組數目寫入檔案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFile 類別](../../mfc/reference/cfile-class.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[CSocket 類別](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile 類別](../../mfc/reference/csocketfile-class.md)
