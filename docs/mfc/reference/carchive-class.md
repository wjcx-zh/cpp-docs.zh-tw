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
ms.openlocfilehash: 46d30e38674d10aecdfdbf7be91c48063ba9f493
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377069"
---
# <a name="carchive-class"></a>CArchive 類別

允許您以永久二進位形式(通常是磁碟儲存)保存複雜的物件網路,這些二進位形式在刪除這些物件後仍然存在。

## <a name="syntax"></a>語法

```
class CArchive
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C 壓縮檔:C 壓縮檔](#carchive)|建立 `CArchive` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C存檔::中止](#abort)|關閉存檔而不引發異常。|
|[C 壓縮檔:關閉](#close)|重新載入的資料並從斷線連線`CFile`。|
|[C存檔:沖洗](#flush)|從存檔緩衝區刷新不寫入的數據。|
|[C 壓縮檔:抓取檔案](#getfile)|獲取`CFile`此存檔的對象指標。|
|[C 壓縮檔:抓取物件架構](#getobjectschema)|從`Serialize`函數調用以確定正在反序列化的物件的版本。|
|[C存檔::是緩衝區空](#isbufferempty)|確定緩衝區在 Windows 套接字接收過程中是否已清空。|
|[C 壓縮檔:正在載入](#isloading)|確定存檔是否正在載入。|
|[C 壓縮檔:正在儲存](#isstoring)|確定存檔是否正在存儲。|
|[C 壓縮檔:mapObject](#mapobject)|在地圖中放置未序列化到檔但可用於子物件引用的物件。|
|[C 壓縮檔:閱讀](#read)|讀取原始位元組。|
|[C 存檔:閱讀類](#readclass)|讀取以前與 一`WriteClass`起 存儲的類引用。|
|[C 壓縮檔:讀取物件](#readobject)|調用物件的`Serialize`函數以進行載入。|
|[C 壓縮檔::閱讀字串](#readstring)|讀取一行文本。|
|[C 壓縮檔:序列化類別](#serializeclass)|根據的方向讀取或寫入對`CArchive`物件的類引用`CArchive`。|
|[C 壓縮檔::設定載入參數](#setloadparams)|設置負載陣列增長的大小。 必須在載入任何物件之前、載入或之前`MapObject`調用。 `ReadObject`|
|[C 壓縮檔:設定物件架構](#setobjectschema)|設置存儲在存檔物件中的對象架構。|
|[C 壓縮檔:設定儲存參數](#setstoreparams)|設置哈希表大小和映射的塊大小,用於在序列化過程中標識唯一物件。|
|[C 壓縮檔:寫入](#write)|寫入原始位元組。|
|[C壓縮檔:寫入類別](#writeclass)|寫入對的`CRuntimeClass``CArchive`引用。|
|[C 壓縮檔:寫入物件](#writeobject)|調用物件的`Serialize`函數進行存儲。|
|[C 壓縮檔::寫入字串](#writestring)|寫入一行文字。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[C 壓縮檔::運算子&lt;&lt;](#operator_lt_lt)|將物件和基元類型存儲到存檔中。|
|[C 壓縮檔::運算子&gt;&gt;](#operator_gt_gt)|從存檔載入物件和基元類型。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[C 存檔:m_pDocument](#m_pdocument)||

## <a name="remarks"></a>備註

`CArchive`沒有基類。

稍後,可以從持久存儲載入物件,在記憶體中重新構建它們。 使數據持久化的過程稱為"序列化"

您可以將存檔對象視為一種二進位流。 與輸入/輸出流一樣,存檔與文件相關聯,並允許緩衝寫入和讀取數據,並從存儲中讀取數據。 輸入/輸出流處理 ASCII 字元序列,但存檔以有效的非冗餘格式處理二進位物件資料。

必須先創建[CFile](../../mfc/reference/cfile-class.md)物件,然後`CArchive`才能創建 物件。 此外,必須確保存檔的載入/儲存狀態與檔的打開模式相容。 每個檔只能使用一個活動存檔。

建構`CArchive`物件時,將其附加到表示打開檔的`CFile`類 (或派生類)的物件。 您還可以指定存檔是否將用於載入或儲存。 對`CArchive`象 不僅可以處理基元類型,還可以處理用於序列化的[CObject](../../mfc/reference/cobject-class.md)派生類的物件。 可序列化類通常`Serialize`具有成員函數,它通常使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)宏,如類`CObject`下所述。

重載提取**>>**(**<<**) 和 插入 ( ) 運算子`CObject`是支援基元類型和 派生類的方便的存檔程式設計介面。

`CArchive`還支援使用 MFC Windows 套接字類 CSocket 和[CSocketFile](../../mfc/reference/csocket-class.md)進行程式設計。 [CSocketFile](../../mfc/reference/csocketfile-class.md) [IsBufferEmpty](#isbufferempty)成員函數支援該用法。

有關 的詳細`CArchive`資訊 ,請參閱文章[序列化和](../../mfc/serialization-in-mfc.md)Windows[socket:使用帶存檔的 socket](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CArchive`

## <a name="requirements"></a>需求

**標題:** afx.h

## <a name="carchiveabort"></a><a name="abort"></a>C存檔::中止

調用此函數以關閉存檔,而不會引發異常。

```
void Abort ();
```

### <a name="remarks"></a>備註

析`CArchive`構函數通常會調`Close`用 ,這將刷新尚未保存`CFile`到關聯 物件的任何數據。 這可能會導致異常。

捕獲這些異常時,最好使用`Abort`,以便銷`CArchive`毀 物件不會導致進一步的異常。 處理異常時,`CArchive::Abort`不會引發故障異常,因為與[CArchive::Close](#close)不同,`Abort`忽略失敗。

如果使用**new**在`CArchive`堆上 分配物件,則必須在關閉檔後將其刪除。

### <a name="example"></a>範例

  請參閱[CArchive::WriteClass](#writeclass)的範例。

## <a name="carchivecarchive"></a><a name="carchive"></a>C 壓縮檔:C 壓縮檔

建構`CArchive`物件並指定該物件是否用於載入或儲存物件。

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>參數

*pFile*<br/>
指向物件作為`CFile`持久數據的最終源或目標的指標。

*nMode*<br/>
指定對象是從存檔載入還是儲存到存檔的標誌。 *nMode*參數必須具有以下值之一:

- `CArchive::load`從存檔載入數據。 只需要`CFile`讀取許可權。

- `CArchive::store`將數據保存到存檔中。 需要`CFile`寫入許可權。

- `CArchive::bNoFlushOnDelete`防止在調用存檔析構`Flush`函數時自動調用存檔。 如果設置此標誌,則負責在調用析構函數之前`Close`顯式調用。 如果沒有,您的數據將損壞。

*nBufSize*<br/>
指定內部文件緩衝區大小的整數(以位元組為單位)。 請注意,默認緩衝區大小為 4,096 位元組。 如果例行存檔大型物件,則如果使用較大的緩衝區大小(是檔緩衝區大小的倍數)來提高性能。

*lpBuf*<br/>
指向使用者提供的大小*nBufSize*緩衝區的可選指標。 如果不指定此參數,存檔將從本地堆分配緩衝區,並在對象銷毀時釋放它。 存檔不會釋放使用者提供的緩衝區。

### <a name="remarks"></a>備註

建立存檔後,無法更改此規範。

在關閉存檔之前`CFile`,不得使用操作來更改檔案的狀態。 任何此類操作都將損壞存檔的完整性。 在序列化期間,您可以隨時從[GetFile](#getfile)成員函數獲取存檔的檔物件,然後使用[CFile:get 定位](../../mfc/reference/cfile-class.md#getposition)函數來存取檔指標的位置。 在獲取檔指標的位置之前,應調用[CArchive::Flush。](#flush)

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

## <a name="carchiveclose"></a><a name="close"></a>C 壓縮檔:關閉

刷新緩衝區中剩餘的所有數據,關閉存檔,並將存檔與檔斷開連接。

```
void Close();
```

### <a name="remarks"></a>備註

不允許對存檔執行進一步操作。 關閉存檔後,可以為同一檔創建另一個存檔,也可以關閉該檔。

成員函數`Close`可確保所有數據從存檔傳輸到檔案,並使存檔不可用。 要完成從檔案傳輸到存儲介質,必須首先使用[CFile::關閉](../../mfc/reference/cfile-class.md#close),然後`CFile`銷毀 物件。

### <a name="example"></a>範例

  請參閱[CArchive::寫入字串](#writestring)的範例。

## <a name="carchiveflush"></a><a name="flush"></a>C存檔:沖洗

強制將存檔緩衝區中剩餘的任何數據寫入檔。

```
void Flush();
```

### <a name="remarks"></a>備註

成員函數`Flush`可確保所有數據從存檔傳輸到檔。 您必須呼叫[CFile::關閉](../../mfc/reference/cfile-class.md#close)才能完成從檔案傳輸到儲存媒體。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

## <a name="carchivegetfile"></a><a name="getfile"></a>C 壓縮檔:抓取檔案

獲取`CFile`此存檔的對象指標。

```
CFile* GetFile() const;
```

### <a name="return-value"></a>傳回值

指向正在使用的物件的`CFile`常量指標。

### <a name="remarks"></a>備註

在使用`GetFile`之前,必須刷新存檔。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

## <a name="carchivegetobjectschema"></a><a name="getobjectschema"></a>C 壓縮檔:抓取物件架構

從`Serialize`函數調用此函數以確定當前正在反序列化的物件的版本。

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>傳回值

在反序列化期間,正在讀取的物件的版本。

### <a name="remarks"></a>備註

僅當載入物件時,`CArchive`呼叫此函數才有效[(CArchive::IsLoaded](#isloading)傳回非零)。 它應該是函數中的第一個調用`Serialize`,並且只調用一次。 (UINT)-1 的返回值表示版本號未知。

派生類可以使用VERSIONABLE_SCHEMA與架構版本本身(在IMPLEMENT_SERIAL宏中)組合(使用位**或**)來創建一個"可版本物件",即其`Serialize`成員函數可以讀取多個版本的物件`CObject`。 默認框架功能(無VERSIONABLE_SCHEMA)是在版本不匹配時引發異常。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

## <a name="carchiveisbufferempty"></a><a name="isbufferempty"></a>C存檔::是緩衝區空

調用此成員函數以確定存檔物件的內部緩衝區是否為空。

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>傳回值

如果存檔的緩衝區為空,則非零;否則 0。

### <a name="remarks"></a>備註

此功能用於支援 MFC Windows 套`CSocketFile`接字類的程式設計。 不需要將其用於與`CFile`對象關聯的存檔。

與與`CSocketFile`物件關聯`IsBufferEmpty`的存檔一起使用的原因是存檔的緩衝區可能包含多條消息或記錄。 收到一條消息后,應使用`IsBufferEmpty`來控制繼續接收數據的迴圈,直到緩衝區為空。 有關詳細資訊,請參閱`CAsyncSocket`類`IsBufferEmpty`的[接收](../../mfc/reference/casyncsocket-class.md#receive)成員函數,其中演示如何使用 。

有關詳細資訊,請參閱[Windows 通訊卡字:使用帶存檔的通訊字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="carchiveisloading"></a><a name="isloading"></a>C 壓縮檔:正在載入

確定存檔是否正在載入數據。

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>傳回值

如果存檔當前用於載入,則非零;否則 0。

### <a name="remarks"></a>備註

此成員函數由存檔的類`Serialize`的函數調用。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

## <a name="carchiveisstoring"></a><a name="isstoring"></a>C 壓縮檔:正在儲存

確定存檔是否存儲數據。

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>傳回值

如果存檔當前用於存儲,則非零;否則 0。

### <a name="remarks"></a>備註

此成員函數由存檔的類`Serialize`的函數調用。

如果存檔`IsStoring`的狀態為非零,則`IsLoading`其 狀態為 0,反之亦然。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

## <a name="carchivemapobject"></a><a name="mapobject"></a>C 壓縮檔:mapObject

調用此成員函數,將未真正序列化到檔的地圖中的物件放置,但可用於子物件引用的物件。

```
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>參數

*Pob*<br/>
指向要存儲的物件的常量指標。

### <a name="remarks"></a>備註

例如,您可能不會序列化文檔,但可以序列化作為文檔一部分的項。 通過呼叫`MapObject`,允許這些專案或子物件引用文檔。 此外,序列化子項可以序列化其*m_pDocument*回指標。

您可以在儲存物件`MapObject`時調`CArchive`用 物件並從物件載入。 `MapObject`將指定物件添加到`CArchive`物件在序列化和反序列化期間維護的內部資料結構中,但與[ReadObject](#readobject)和[WriteObject](#writeobject)不同,它不調用物件上的序列化。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

## <a name="carchivem_pdocument"></a><a name="m_pdocument"></a>C 存檔:m_pDocument

默認情況下,此指標可以`CDocument`設置為`CArchive`實例使用者想要的任何指標。

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>備註

此指標的常見用法是向所有要序列化的對象傳達有關序列化過程的其他資訊。 這是通過使用正在序列化的文檔`CDocument`( 派生類)初始化指標來實現的,這樣文檔中的物件可以在必要時訪問文檔。 此指標在序列化期間`COleClientItem`也由物件使用。

當使用者發出文件打開或保存命令時,框架將*m_pDocument*文檔序列化。 如果出於檔案開啟或儲存等原因序列化物件連結和嵌入 (OLE) 容器文件,則必須顯式設定*m_pDocument*。 例如,在將容器文檔序列化到剪貼簿時,可以執行此操作。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

## <a name="carchiveoperator-ltlt"></a><a name="operator_lt_lt"></a>C 壓縮檔::運算子&lt;&lt;

將指示的物件或基元類型存儲到存檔中。

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

在`CArchive`一行上啟用多個插入運算符的引用。

### <a name="remarks"></a>備註

上面的最後兩個版本專門用於存儲 64 位整數。

如果在類別上使用IMPLEMENT_SERIAL巨集,則插入運算符重載以`CObject`呼叫以呼叫保護`WriteObject`的 。 此函數反過來調用類`Serialize`的函數。

[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)插入運算符 (<<) 支援診斷轉儲並存儲到存檔。

### <a name="example"></a>範例

此範例演示了插入運算符 << `CArchive` **int**和**長**類型。

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>範例

此範例 2 展示`CArchive`使用插入運算符 << `CStringT`的類型。

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

## <a name="carchiveoperator-gtgt"></a><a name="operator_gt_gt"></a>C 壓縮檔::運算子&gt;&gt;

從存檔載入指示的物件或基元類型。

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

在`CArchive`一行上啟用多個提取運算符的引用。

### <a name="remarks"></a>備註

上面的最後兩個版本專門用於載入64位整數。

如果在類實現中使用IMPLEMENT_SERIAL宏,則提取運算符將重載以`CObject`調用受保護的`ReadObject`函數(使用非零運行時類指標)。 此函數反過來調用類`Serialize`的函數。

[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)提取運算子 (>>) 支援從存檔載入。

### <a name="example"></a>範例

此示例演示了提取運算符 >> `CArchive` **int**類型的使用。

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>範例

此範例展示插入和提取運算子`CArchive`的使用,<,\<並且 >> 與類型。 `CStringT`

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

## <a name="carchiveread"></a><a name="read"></a>C 壓縮檔:閱讀

從存檔中讀取指定數量的位元組。

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
指向使用者提供的緩衝區的指標,用於接收從存檔讀取的數據。

*nMax*<br/>
一個未簽名的整數,用於指定要從存檔中讀取的位元組數。

### <a name="return-value"></a>傳回值

包含實際讀取位元組數的無符號整數。 如果返回值小於請求的數量,則已達到文件結尾。 檔結尾條件上不引發異常。

### <a name="remarks"></a>備註

存檔不解釋位元組。

可以使用`Read``Serialize`函數中的成員函數讀取物件中包含的普通結構。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

## <a name="carchivereadclass"></a><a name="readclass"></a>C 存檔:閱讀類

調用此成員函數以讀取對以前使用[WriteClass](#writeclass)儲存的類的引用。

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>參數

*pClassRef 要求*<br/>
指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構的指標,對應於請求的類引用。 可以是 NULL。

*pSchema*<br/>
指向以前存儲的運行時類的架構的指標。

*pObTag*<br/>
引用物件的唯一標記的數位。 內部使用[ReadObject](#readobject)的實現。 僅用於高級程式設計;*pObTag*通常應為 NULL。

### <a name="return-value"></a>傳回值

指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構的指標。

### <a name="remarks"></a>備註

如果*pClassRef*`ReadClass`請求 不是 NULL,請驗證存檔的類資訊是否與執行時類相容。 如果沒有相容,`ReadClass`會拋出[CArchiveException](../../mfc/reference/carchiveexception-class.md)。

您的執行時類必須使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial);否則,`ReadClass`將拋出[一個CNot被支援例外](../../mfc/reference/cnotsupportedexception-class.md)。

如果*pSchema*為 NULL,則可以通過調用[CArchive::getObjectSchema](#getobjectschema)來檢索存儲類的架構。否則<strong>\*</strong>*,pSchema*將包含以前存儲的運行時類的架構。

可以使用[序列化類](#serializeclass)而不是`ReadClass`,來處理類引用的讀取和寫入。

### <a name="example"></a>範例

  請參閱[CArchive::WriteClass](#writeclass)的範例。

## <a name="carchivereadobject"></a><a name="readobject"></a>C 壓縮檔:讀取物件

從存檔中讀取對象數據並建構相應類型的物件。

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>參數

*pClass*<br/>
指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構的常量指標,對應於您預期讀取的物件。

### <a name="return-value"></a>傳回值

必須使用[CObject::IsKinds](../../mfc/reference/cobject-class.md#iskindof)安全地強制轉換為正確的派生類的[CObject](../../mfc/reference/cobject-class.md)指標。

### <a name="remarks"></a>備註

此函數通常由`CArchive`[CObject](../../mfc/reference/cobject-class.md)**>>** 指標的提取 ( ) 運算符重載呼叫。 `ReadObject`,反過來,`Serialize`調用存檔的類的功能。

如果提供非零*pClass*參數(由[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)宏獲取,則該函數將驗證存檔物件的運行時類。 這假定您在類的實現中使用了IMPLEMENT_SERIAL宏。

### <a name="example"></a>範例

  請參閱[CArchive::WriteObject](#writeobject)的範例。

## <a name="carchivereadstring"></a><a name="readstring"></a>C 壓縮檔::閱讀字串

呼叫此成員函式從與物件關聯的檔案中將文字資料讀取到緩衝區中`CArchive`。

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>參數

*rString*<br/>
對[CString](../../atl-mfc-shared/reference/cstringt-class.md)的引用,該字串將在從與 CArchive 物件關聯的檔中讀取後包含該字串。

*lpsz*<br/>
指定指向使用者提供的緩衝區的指標,該緩衝區將接收 null 終止的文本字串。

*nMax*<br/>
指定要讀取的最大字元數。 應小於*lpsz*緩衝區的大小。

### <a name="return-value"></a>傳回值

在返回 BOOL 的版本中,如果成功,為 TRUE;否則。

在返回`LPTSTR`的版本中,將指向包含文本數據的緩衝區的指標;如果達到檔案結尾,則為 NULL。

### <a name="remarks"></a>備註

在具有*nMax*參數的成員函數版本中,緩衝區將最多保留*nMax* - 1 個字元的限制。 讀取由滑車返回線進給對停止。 尾隨換行符始終被刪除。 在這兩種情況下都附加了空字元 ("\0")。

[CArchive::讀取](#read)也可用於文本模式輸入,但它不會在回車返回行饋送對上終止。

### <a name="example"></a>範例

  請參閱[CArchive::寫入字串](#writestring)的範例。

## <a name="carchiveserializeclass"></a><a name="serializeclass"></a>C 壓縮檔:序列化類別

如果要存儲和載入基類的版本資訊,請調用此成員函數。

```
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>參數

*pClassRef*<br/>
指向基類的運行時類物件的指標。

### <a name="remarks"></a>備註

`SerializeClass`根據`CArchive``CArchive`的方向讀取或寫入對物件的類的引用。 使用`SerializeClass` [ReadClass](#readclass)和[WriteClass](#writeclass)作為序列化基類物件的便捷方法;`SerializeClass`需要更少的代碼和更少的參數。

與`ReadClass``SerializeClass`樣,驗證存檔的類資訊是否與運行時類相容。 如果沒有相容,`SerializeClass`會拋出[CArchiveException](../../mfc/reference/carchiveexception-class.md)。

您的執行時類必須使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial);否則,`SerializeClass`將拋出[一個CNot被支援例外](../../mfc/reference/cnotsupportedexception-class.md)。

使用[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)宏檢索*pRuntimeClass 參數*的值。 基類必須使用了[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)宏。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

## <a name="carchivesetloadparams"></a><a name="setloadparams"></a>C 壓縮檔::設定載入參數

當您`SetLoadParams`要從存檔中讀取`CObject`大量 派生物件時調用。

```
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>參數

*nGrowBy*<br/>
如果需要增加大小,要分配的最小元素槽數。

### <a name="remarks"></a>備註

`CArchive`使用負載數組解析對存檔中儲存物件的引用。 `SetLoadParams`允許您設置負載陣組增長的大小。

在載入任何物件`SetLoadParams`或調用 MapObject 或[ReadObject](#mapobject)[ReadObject](#readobject)之後,不得呼叫。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivesetobjectschema"></a><a name="setobjectschema"></a>C 壓縮檔:設定物件架構

呼叫此成員函數會儲存在存檔物件中的物件架構設定為*nSchema*。

```
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>參數

*NSchema*<br/>
指定物件的架構。

### <a name="remarks"></a>備註

下一次調用[GetObjectSchema](#getobjectschema)將返回存儲在*nSchema*中的值。

用於`SetObjectSchema`高級版本控制;例如,當您要強制在派生類的`Serialize`函數中讀取特定版本時。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

## <a name="carchivesetstoreparams"></a><a name="setstoreparams"></a>C 壓縮檔:設定儲存參數

在`SetStoreParams`存檔中存儲大量`CObject`派生物件時使用。

```
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>參數

*n哈希*<br/>
介面指標對應的哈希表的大小。 應為質數。

*nBlockSize*<br/>
指定用於擴展參數的記憶體分配粒度。 應該是一個功率2的最佳性能。

### <a name="remarks"></a>備註

`SetStoreParams`允許您設置哈希表大小和映射的塊大小,用於在序列化過程中標識唯一物件。

在存儲任何物件`SetStoreParams`或調用 MapObject 或[WriteObject](#mapobject)[WriteObject](#writeobject)之後,不得呼叫。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivewrite"></a><a name="write"></a>C 壓縮檔:寫入

將指定數量的位元組寫入存檔。

```
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
指向使用者提供的緩衝區的指標,其中包含要寫入存檔的數據。

*nMax*<br/>
指定要寫入存檔的位元組數的整數。

### <a name="remarks"></a>備註

存檔不格式化位元組。

可以使用`Write``Serialize`函數中的成員函數編寫包含在物件中的普通結構。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

## <a name="carchivewriteclass"></a><a name="writeclass"></a>C壓縮檔:寫入類別

用於`WriteClass`在派生類的序列化期間存儲基類的版本和類資訊。

```
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>參數

*pClassRef*<br/>
指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構的指標,對應於請求的類引用。

### <a name="remarks"></a>備註

`WriteClass`將基類別的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)的參考寫`CArchive`入 。 使用[CArchive::讀取類](#readclass)來檢索引用。

`WriteClass`驗證存檔的類資訊是否與運行時類相容。 如果沒有相容,`WriteClass`會拋出[CArchiveException](../../mfc/reference/carchiveexception-class.md)。

您的執行時類必須使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial);否則,`WriteClass`將拋出[一個CNot被支援例外](../../mfc/reference/cnotsupportedexception-class.md)。

可以使用[序列化類](#serializeclass)而不是`WriteClass`,來處理類引用的讀取和寫入。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

## <a name="carchivewriteobject"></a><a name="writeobject"></a>C 壓縮檔:寫入物件

將指定的`CObject`內容儲存到存檔。

```
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>參數

*Pob*<br/>
指向要存儲的物件的常量指標。

### <a name="remarks"></a>備註

此函數通常由的`CArchive`插入**<<**( ) 運算`CObject`符重 載呼叫。 `WriteObject`,反過來,`Serialize`調用存檔的類的功能。

您必須使用IMPLEMENT_SERIAL宏來啟用存檔。 `WriteObject`將 ASCII 類名稱寫入存檔。 此類名稱稍後在載入過程中驗證。 特殊的編碼方案可防止類的多個物件的類名稱不必要地重複。 此方案還防止冗餘存儲作為多個指標目標的物件。

確切的物件編碼方法(包括 ASCII 類名稱的存在)是一個實現詳細資訊,並可能在庫的未來版本中更改。

> [!NOTE]
> 在開始存檔所有物件之前,請完成創建、刪除和更新它們。 如果將存檔與物件修改混合在一起,您的存檔將損壞。

### <a name="example"></a>範例

有關類別`CAge`定義,請參閱[CObList::CObList 的範例](../../mfc/reference/coblist-class.md#coblist)。

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

## <a name="carchivewritestring"></a><a name="writestring"></a>C 壓縮檔::寫入字串

使用此成員函數將數據從緩衝區寫入與`CArchive`對象關聯的檔。

```
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>參數

*lpsz*<br/>
指定指向包含 null 終止文字字串的緩衝區的指標。

### <a name="remarks"></a>備註

終止 null 字元 ("\0") 不會寫入檔;因此,不寫入檔。也不是自動寫入的新增文字。

`WriteString`引發一個異常以回應多個條件,包括磁碟滿型條件。

`Write`也可用,但它不是終止 null 字元,而是將請求的位元組數寫入檔。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFile 類別](../../mfc/reference/cfile-class.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[CSocket 類別](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile 類別](../../mfc/reference/csocketfile-class.md)
