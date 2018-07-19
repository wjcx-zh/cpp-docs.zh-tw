---
title: CArchive 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81e76347e197469e4e4fa490d4ddfc42ef0fbd71
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338074"
---
# <a name="carchive-class"></a>CArchive 類別
可讓您將複雜的網路的物件儲存在永久二進位格式 （通常是磁碟儲存體），之後會刪除這些物件仍然存在。  
  
## <a name="syntax"></a>語法  
  
```  
class CArchive  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CArchive::CArchive](#carchive)|建立 `CArchive` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CArchive::Abort](#abort)|關閉封存，而不擲回例外狀況。|  
|[CArchive::Close](#close)|清除未寫入的資料，並中斷`CFile`。|  
|[CArchive::Flush](#flush)|從封存緩衝區中清除未寫入的資料。|  
|[CArchive::GetFile](#getfile)|取得`CFile`物件指標，此封存。|  
|[CArchive::GetObjectSchema](#getobjectschema)|從呼叫`Serialize`函式來判斷正在還原序列化物件的版本。|  
|[CArchive::IsBufferEmpty](#isbufferempty)|判斷是否已在 Windows 通訊端期間清空緩衝區接收程序。|  
|[CArchive::IsLoading](#isloading)|判斷封存是否正在載入。|  
|[CArchive::IsStoring](#isstoring)|決定是否要儲存封存。|  
|[CArchive::MapObject](#mapobject)|置於的對應，不會序列化至檔案，但卻是可供參考的子物件的物件。|  
|[Carchive:: Read](#read)|讀取未經處理位元組。|  
|[CArchive::ReadClass](#readclass)|與先前儲存的類別參考的讀取`WriteClass`。|  
|[CArchive::ReadObject](#readobject)|呼叫物件的`Serialize`載入函式。|  
|[CArchive::ReadString](#readstring)|讀取一行文字。|  
|[CArchive::SerializeClass](#serializeclass)|讀取或寫入的類別參考`CArchive`物件的方向根據`CArchive`。|  
|[CArchive::SetLoadParams](#setloadparams)|設定負載陣列成長時的大小。 載入的任何物件之前，或之前，必須呼叫`MapObject`或`ReadObject`呼叫。|  
|[CArchive::SetObjectSchema](#setobjectschema)|設定封存物件中儲存的物件結構描述。|  
|[CArchive::SetStoreParams](#setstoreparams)|設定雜湊資料表大小和用來識別唯一的物件在序列化程序對應的區塊大小。|  
|[Carchive:: Write](#write)|寫入未經處理位元組。|  
|[CArchive::WriteClass](#writeclass)|寫入的參考`CRuntimeClass`至`CArchive`。|  
|[CArchive::WriteObject](#writeobject)|呼叫物件的`Serialize`函式，來儲存。|  
|[CArchive::WriteString](#writestring)|寫入單一文字行。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CArchive::operator &lt;&lt;](#operator_lt_lt)|儲存物件和封存的基本型別。|  
|[CArchive::operator &gt;&gt;](#operator_gt_gt)|從封存中載入物件及基本類型。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CArchive::m_pDocument](#m_pdocument)||  
  
## <a name="remarks"></a>備註  
 `CArchive` 沒有基底類別。  
  
 稍後您可以載入物件從永續性儲存體，重組它們在記憶體中。 此程序可確保資料持續性稱為 < 序列化 >。  
  
 您可以將封存物件為類型的二進位資料流。 輸入/輸出資料流，例如封存與檔案相關聯，並允許緩衝處理的寫入和讀取資料在儲存體。 輸入/輸出資料流處理順序的 ASCII 字元，但封存處理有效率、 nonredundant 格式的二進位物件資料。  
  
 您必須建立[CFile](../../mfc/reference/cfile-class.md)物件才能建立`CArchive`物件。 此外，您必須確定封存的載入/儲存狀態是與檔案的開啟模式相容。 您受限於一個作用中的封存，每個檔案。  
  
 當您建構`CArchive`物件，將它附加到類別的物件`CFile`（或衍生的類別），表示已開啟的檔案。 您也可以指定封存是否會用於載入或儲存。 A`CArchive`物件可以處理基本型別不僅的物件[CObject](../../mfc/reference/cobject-class.md)-衍生專為序列化的類別。 可序列化的類別通常有`Serialize`成員函式，而且通常會使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)並[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)巨集 類別底下所述`CObject`。  
  
 多載的擷取 ( **>>**) 和插入 ( **<<**) 是方便存取的封存的程式設計介面，支援這兩種基本類型的運算子和`CObject`-衍生的類別。  
  
 `CArchive` 也支援使用 MFC Windows 通訊端類別進行程式設計[CSocket](../../mfc/reference/csocket-class.md)並[CSocketFile](../../mfc/reference/csocketfile-class.md)。 [IsBufferEmpty](#isbufferempty)成員函式支援這種用法。  
  
 如需詳細資訊`CArchive`，請參閱文章[序列化](../../mfc/serialization-in-mfc.md)並[Windows Sockets： 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CArchive`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="abort"></a>  CArchive::Abort  
 呼叫此函式來關閉封存，而不擲回例外狀況。  
  
```  
void Abort ();
```  
  
### <a name="remarks"></a>備註  
 `CArchive`通常會呼叫解構函式`Close`，這會清除任何尚未儲存的資料至相關聯`CFile`物件。 這會造成例外狀況。  
  
 時攔截這些例外狀況，它是個不錯的主意，若要使用`Abort`，如此一來，destructing`CArchive`物件不會造成進一步的例外狀況。 處理例外狀況，當`CArchive::Abort`不會擲回例外狀況失敗因為不同的是[CArchive::Close](#close)，`Abort`會忽略失敗。  
  
 如果您使用**新**配置`CArchive`物件在堆積的則您必須將它刪除後關閉檔案。  
  
### <a name="example"></a>範例  
  範例，請參閱[CArchive::WriteClass](#writeclass)。  
  
##  <a name="carchive"></a>  CArchive::CArchive  
 建構`CArchive`物件，並指定是否將用來載入或儲存的物件。  
  
```  
CArchive(
    CFile* pFile,  
    UINT nMode,  
    int nBufSize = 4096,  
    void* lpBuf = NULL);
```  
  
### <a name="parameters"></a>參數  
 *pFile*  
 指標`CFile`ultimate 的來源或目的地的持續性資料的物件。  
  
 *nMode*  
 指定物件是否會從載入或儲存至封存的旗標。 *NMode*參數必須要有下列值之一：  
  
- `CArchive::load` 從封存中載入資料。 只需要`CFile`讀取權限。  
  
- `CArchive::store` 將資料儲存至封存。 需要`CFile`寫入權限。  
  
- `CArchive::bNoFlushOnDelete` 會自動呼叫時，防止封存`Flush`封存解構函式呼叫時。 如果您設定此旗標時，您必須負責明確呼叫`Close`解構函式呼叫之前。 如果您不這樣做，您的資料將會損毀。  
  
 *nBufSize*  
 指定的內部檔案緩衝區大小，以位元組為單位的整數。 請注意，預設緩衝區大小是 4,096 個位元組。 如果您定期封存大型物件時，您將會改善效能，如果您使用較大的緩衝區大小是檔案緩衝區大小的倍數。  
  
 *lpBuf*  
 使用者提供的緩衝區大小的選擇性指標*nBufSize*。 如果您未指定此參數，封存配置緩衝區，以從本機堆積，並終結物件時釋放它。 封存不會釋放使用者提供的緩衝區。  
  
### <a name="remarks"></a>備註  
 建立封存之後，您無法變更此規格。  
  
 您不得使用`CFile`更改檔案的狀態，直到您關閉封存的作業。 任何這類作業將會造成損害封存的完整性。 您也可以取得 封存的檔案物件的序列化期間，隨時存取之檔案指標的位置[GetFile](#getfile)成員函式，然後使用[CFile::GetPosition](../../mfc/reference/cfile-class.md#getposition)函式. 您應該呼叫[CArchive::Flush](#flush)之前取得檔案指標的位置。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]  
  
##  <a name="close"></a>  CArchive::Close  
 排清緩衝區中剩餘的任何資料、 關閉封存，並中斷連接封存檔從檔案。  
  
```  
void Close();
```  
  
### <a name="remarks"></a>備註  
 不允許任何進一步的作業上的封存。 關閉封存之後，您可以建立另一個封存以供相同的檔案，或者您可以關閉檔案。  
  
 此成員函式`Close`可確保所有的資料傳輸從保存至檔案，並得將封存無法使用。 若要完成從檔案傳送到儲存體中，您必須先使用[CFile::Close](../../mfc/reference/cfile-class.md#close)然後終結`CFile`物件。  
  
### <a name="example"></a>範例  
  範例，請參閱[CArchive::WriteString](#writestring)。  
  
##  <a name="flush"></a>  CArchive::Flush  
 強制寫入檔案的封存緩衝區中剩餘的任何資料。  
  
```  
void Flush();
```  
  
### <a name="remarks"></a>備註  
 此成員函式`Flush`可確保所有的資料傳輸從封存檔案。 您必須呼叫[CFile::Close](../../mfc/reference/cfile-class.md#close)完成可從檔案傳輸到儲存體中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]  
  
##  <a name="getfile"></a>  CArchive::GetFile  
 取得`CFile`物件指標，此封存。  
  
```  
CFile* GetFile() const;  
```  
  
### <a name="return-value"></a>傳回值  
 常數指標`CFile`使用中的物件。  
  
### <a name="remarks"></a>備註  
 您必須排清之前使用封存`GetFile`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]  
  
##  <a name="getobjectschema"></a>  CArchive::GetObjectSchema  
 呼叫此函式從`Serialize`函式來判斷目前正在還原序列化物件的版本。  
  
```  
UINT GetObjectSchema();
```  
  
### <a name="return-value"></a>傳回值  
 還原序列化期間，正在讀取之物件的版本。  
  
### <a name="remarks"></a>備註  
 呼叫此函式時才有效`CArchive`正在載入物件 ( [CArchive::IsLoading](#isloading)傳回非零值)。 它應該是中的第一個呼叫`Serialize`函式和呼叫一次。 傳回值為 (UINT)-1 表示的版本號碼不明。  
  
 A `CObject`-在衍生的類別可能會使用 VERSIONABLE_SCHEMA 結合 (使用位元**或者**) 與結構描述版本 （在 IMPLEMENT_SERIAL 巨集） 來建立 「 可控制版本物件，"也就是物件其`Serialize`成員函式可以讀取多個版本。 （不含 VERSIONABLE_SCHEMA) 的預設架構功能是版本不相符時所擲回例外狀況。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]  
  
##  <a name="isbufferempty"></a>  CArchive::IsBufferEmpty  
 呼叫此成員函式，以判斷保存物件的內部緩衝區是否為空白。  
  
```  
BOOL IsBufferEmpty() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果封存的緩衝區是空的則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式會提供給支援與 MFC Windows 通訊端類別的程式設計`CSocketFile`。 您不需要將它用於與相關聯的封存`CFile`物件。  
  
 使用的原因`IsBufferEmpty`與相關聯的封存`CSocketFile`物件是封存的緩衝區可能包含多個訊息或記錄。 之後收到一則訊息，您應該使用`IsBufferEmpty`控制一個迴圈持續執行直到緩衝區是空的接收資料。 如需詳細資訊，請參閱 <<c0> [ 接收](../../mfc/reference/casyncsocket-class.md#receive)類別成員函式`CAsyncSocket`，但會示範如何使用`IsBufferEmpty`。  
  
 如需詳細資訊，請參閱 < [Windows Sockets： 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
##  <a name="isloading"></a>  CArchive::IsLoading  
 判斷封存是否正在載入資料。  
  
```  
BOOL IsLoading() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果目前正在載入; 使用封存，非零值。否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式會呼叫`Serialize`封存類別的函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]  
  
##  <a name="isstoring"></a>  CArchive::IsStoring  
 判斷封存是否正在儲存資料。  
  
```  
BOOL IsStoring() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零值，如果目前正在使用封存儲存;否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式會呼叫`Serialize`封存類別的函式。  
  
 如果`IsStoring`保存的狀態為非零值，則其`IsLoading`狀態為 0，反之亦然。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]  
  
##  <a name="mapobject"></a>  CArchive::MapObject  
 呼叫此成員函式，將物件的對應，實際上不會序列化至檔案，但所提供的參考的子物件。  
  
```  
void MapObject(const CObject* pOb);
```  
  
### <a name="parameters"></a>參數  
 *pOb*  
 儲存物件的常數指標。  
  
### <a name="remarks"></a>備註  
 比方說，您可能不會序列化文件，但您會將序列化的文件一部分的項目。 藉由呼叫`MapObject`，您允許這些項目或子物件，參考文件。 此外，序列化的子項目可以將序列化其*m_pDocument*返回指標。  
  
 您可以呼叫`MapObject`當您要儲存並載入從`CArchive`物件。 `MapObject` 將指定的物件加入至所維護的內部資料結構`CArchive`物件序列化和還原序列化期間，但不同於[ReadObject](#readobject)並[WriteObject](#writeobject)，它不會呼叫將序列化物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]  
  
 [!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]  
  
 [!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]  
  
 [!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]  
  
##  <a name="m_pdocument"></a>  CArchive::m_pDocument  
 根據預設，這個指標設定為 NULL`CDocument`可以設定為任何項目之使用者的`CArchive`想要的執行個體。  
  
```  
CDocument* m_pDocument;  
```  
  
### <a name="remarks"></a>備註  
 This 指標的常見用法是傳達正在序列化的所有物件的序列化程序的其他資訊。 做法是初始化與文件的指標 ( `CDocument`-衍生的類別)，要序列化、 文件中的物件，可以在必要時存取文件的方式。 也會使用這個指標`COleClientItem`在序列化期間的物件。  
  
 Framework 組*m_pDocument*使用者發出檔案時，正在序列化的文件開啟或儲存命令。 如果您將序列化的物件連結與嵌入 (OLE) 容器文件開啟舊檔] 或 [儲存以外的原因，您必須明確設定*m_pDocument*。 比方說，您會執行這項操作時序列化到剪貼簿的容器文件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]  
  
##  <a name="operator_lt_lt"></a>  CArchive::operator &lt;&lt;  
 儲存指定的物件或封存的基本型別。  
  
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
 A`CArchive`可讓多個插入運算子在單一行的參考。  
  
### <a name="remarks"></a>備註  
 上述的最後兩個版本是專為儲存 64 位元整數。  
  
 如果您在類別實作中，使用 IMPLEMENT_SERIAL 巨集，則針對多載插入運算子`CObject`呼叫受保護`WriteObject`。 接著，呼叫此函式，`Serialize`類別函式。  
  
 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)插入運算子 (<<) 支援診斷傾印和儲存至封存。  
  
### <a name="example"></a>範例  
 此範例示範如何使用`CArchive`插入運算子 << 具有**int**並**長**型別。  
  
 [!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]  
  
### <a name="example"></a>範例  
 2 本範例示範如何使用`CArchive`插入運算子 << 與`CStringT`型別。  
  
 [!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]  
  
##  <a name="operator_gt_gt"></a>  CArchive::operator &gt;&gt;  
 從封存中載入指定的物件或基本類型。  
  
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
 A`CArchive`可讓多個擷取運算子在單一行的參考。  
  
### <a name="remarks"></a>備註  
 上述的最後兩個版本會特別用來載入 64 位元整數。  
  
 如果您在類別實作中，使用 IMPLEMENT_SERIAL 巨集，則針對擷取運算子多載`CObject`呼叫受保護`ReadObject`函式 （非零的執行階段類別的指標）。 接著，呼叫此函式，`Serialize`類別函式。  
  
 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)引出運算子 (>>) 載入從封存的支援。  
  
### <a name="example"></a>範例  
 此範例示範如何使用`CArchive`擷取運算子 >> 具有**int**型別。  
  
 [!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]  
  
### <a name="example"></a>範例  
 此範例示範如何使用`CArchive`插入和擷取運算子 <\<和 >> 與`CStringT`型別。  
  
 [!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]  
  
##  <a name="read"></a>  Carchive:: Read  
 從封存中讀取指定的位元組數目。  
  
```  
UINT Read(void* lpBuf, UINT nMax);
```  
  
### <a name="parameters"></a>參數  
 *lpBuf*  
 以使用者提供的緩衝區，以接收從封存讀取的資料指標。  
  
 *nMax*  
 不帶正負號的整數，指定的位元組數目從封存讀取。  
  
### <a name="return-value"></a>傳回值  
 不帶正負號的整數，其中包含實際讀取的位元組數目。 如果傳回的值小於所要求的數目，已達到檔案結尾。 在檔案結尾條件上擲不回任何例外狀況。  
  
### <a name="remarks"></a>備註  
 封存不會解譯的位元組。  
  
 您可以使用`Read`成員函式，在您`Serialize`函式來讀取您物件中包含的一般結構。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]  
  
##  <a name="readclass"></a>  CArchive::ReadClass  
 呼叫此成員函式，來讀取先前儲存的類別參考[WriteClass](#writeclass)。  
  
```  
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,  
    UINT* pSchema = NULL,  
    DWORD* pObTag = NULL);
```  
  
### <a name="parameters"></a>參數  
 *pClassRefRequested*  
 指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)對應到要求的類別參考的結構。 可以是 NULL。  
  
 *pSchema*  
 先前儲存的執行階段類別的結構描述的指標。  
  
 *pObTag*  
 參考物件的唯一的標記數字。 在內部使用，藉由實作[ReadObject](#readobject)。 公開的進階程式設計*pObTag*通常應該是 NULL。  
  
### <a name="return-value"></a>傳回值  
 指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構。  
  
### <a name="remarks"></a>備註  
 如果*pClassRefRequested*不是 NULL，`ReadClass`驗證封存的類別資訊是與您的執行階段類別相容。 如果不相容，`ReadClass`將會擲回[CArchiveException](../../mfc/reference/carchiveexception-class.md)。  
  
 必須使用執行階段類別[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)並[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)，否則`ReadClass`將會擲回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 如果*pSchema*為 NULL，就可以擷取結構描述的預存的類別，藉由呼叫[CArchive::GetObjectSchema](#getobjectschema); 否則 **\** * * pSchema*將包含執行階段類別之前儲存的結構描述。  
  
 您可以使用[SerializeClass](#serializeclass)而不是`ReadClass`，處理讀取和寫入的類別參考。  
  
### <a name="example"></a>範例  
  範例，請參閱[CArchive::WriteClass](#writeclass)。  
  
##  <a name="readobject"></a>  CArchive::ReadObject  
 從封存讀取物件資料，並建構適當型別的物件。  
  
```  
CObject* ReadObject(const CRuntimeClass* pClass);
```  
  
### <a name="parameters"></a>參數  
 *pClass*  
 常數指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)對應至您要讀取之物件的結構。  
  
### <a name="return-value"></a>傳回值  
 A [CObject](../../mfc/reference/cobject-class.md)必須安全地轉換成正確的指標使用衍生類別[cobject:: Iskindof](../../mfc/reference/cobject-class.md#iskindof)。  
  
### <a name="remarks"></a>備註  
 通常會呼叫此函式`CArchive`擷取 ( **>>**) 的多載運算子[CObject](../../mfc/reference/cobject-class.md)指標。 `ReadObject`再轉而呼叫`Serialize`封存類別函式。  
  
 如果您提供非零*pClass*參數，來取得[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)巨集，則函式會驗證封存的物件的執行階段類別。 這是假設您已在類別的實作中使用 IMPLEMENT_SERIAL 巨集。  
  
### <a name="example"></a>範例  
  範例，請參閱[CArchive::WriteObject](#writeobject)。  
  
##  <a name="readstring"></a>  CArchive::ReadString  
 呼叫此成員函式的文字資料讀取到緩衝區相關聯的檔案從`CArchive`物件。  
  
```  
BOOL ReadString(CString& rString); 
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```  
  
### <a name="parameters"></a>參數  
 *rString*  
 參考[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，就會包含結果的字串之後它會讀取 CArchive 物件相關聯的檔案。  
  
 *lpsz*  
 指定的使用者提供的緩衝區，將會收到 null 結尾的文字字串的指標。  
  
 *nMax*  
 指定要讀取的字元數目上限。 應該有一個大小大於或等於*lpsz*緩衝區。  
  
### <a name="return-value"></a>傳回值  
 傳回布林值，如果成功，則為 TRUE 的版本中FALSE 否則。  
  
 在傳回的版本中`LPTSTR`，其中包含文字資料中; 緩衝區的指標如果已到達檔案結尾，則為 NULL。  
  
### <a name="remarks"></a>備註  
 使用此成員函式的版本中*nMax*參數，緩衝區會保留高達限制*nMax* -1 個字元。 歸位字元復位換行組停止讀取。 一律會移除結尾新行字元。 在任一情況下，會附加 null 字元 ('\0')。  
  
 [Carchive:: Read](#read)也會提供的文字模式的輸入，但它不會終止歸位字元復位換行組。  
  
### <a name="example"></a>範例  
  範例，請參閱[CArchive::WriteString](#writestring)。  
  
##  <a name="serializeclass"></a>  CArchive::SerializeClass  
 當您想要儲存及載入基底類別的版本資訊，請呼叫此成員函式。  
  
```  
void SerializeClass(const CRuntimeClass* pClassRef);
```  
  
### <a name="parameters"></a>參數  
 *pClassRef*  
 基底類別的執行階段類別物件的指標。  
  
### <a name="remarks"></a>備註  
 `SerializeClass` 讀取或寫入至類別，以參考`CArchive`物件，根據的方向`CArchive`。 使用`SerializeClass`代替[ReadClass](#readclass)並[WriteClass](#writeclass)作為便利的方式來序列化基底類別的物件;`SerializeClass`需要較少的程式碼和較少的參數。  
  
 像是`ReadClass`，`SerializeClass`驗證封存的類別資訊是與您的執行階段類別相容。 如果不相容，`SerializeClass`將會擲回[CArchiveException](../../mfc/reference/carchiveexception-class.md)。  
  
 必須使用執行階段類別[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)並[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)，否則`SerializeClass`將會擲回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 使用[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)巨集來擷取其值*pRuntimeClass*參數。 必須使用的基底類別[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)巨集。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]  
  
##  <a name="setloadparams"></a>  CArchive::SetLoadParams  
 呼叫`SetLoadParams`當您要讀取大量的`CObject`-從封存中衍生物件。  
  
```  
void SetLoadParams(UINT nGrowBy = 1024);
```  
  
### <a name="parameters"></a>參數  
 *nGrowBy*  
 如果是必要的大小增加配置的項目位置的數目下限。  
  
### <a name="remarks"></a>備註  
 `CArchive` 若要解決儲存在封存中的物件參考中使用負載陣列。 `SetLoadParams` 可讓您設定要載入陣列成長的大小。  
  
 您不能呼叫`SetLoadParams`載入的任何物件之後，或之後[MapObject](#mapobject)或是[ReadObject](#readobject)呼叫。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]  
  
##  <a name="setobjectschema"></a>  CArchive::SetObjectSchema  
 呼叫此成員函式設定封存物件中儲存的物件結構描述*nSchema*。  
  
```  
void SetObjectSchema(UINT nSchema);
```  
  
### <a name="parameters"></a>參數  
 *nSchema*  
 指定物件的結構描述。  
  
### <a name="remarks"></a>備註  
 下次呼叫[GetObjectSchema](#getobjectschema)會傳回值儲存在*nSchema*。  
  
 使用`SetObjectSchema`進行進階的版本控制; 比方說，當您想要強制執行特定版本，以便閱讀`Serialize`衍生類別的函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]  
  
##  <a name="setstoreparams"></a>  CArchive::SetStoreParams  
 使用`SetStoreParams`時儲存一大堆`CObject`-衍生的封存中的物件。  
  
```  
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```  
  
### <a name="parameters"></a>參數  
 *nHashSize*  
 將對應的介面指標的雜湊資料表大小。 應該是質數。  
  
 *nBlockSize*  
 指定的記憶體配置資料粒度擴充參數。 應該是 2 的為了達到最佳效能的乘冪。  
  
### <a name="remarks"></a>備註  
 `SetStoreParams` 可讓您設定的雜湊資料表大小和用來識別唯一的物件在序列化程序對應的區塊大小。  
  
 您不能呼叫`SetStoreParams`會儲存任何物件之後，或之後[MapObject](#mapobject)或是[WriteObject](#writeobject)呼叫。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]  
  
##  <a name="write"></a>  Carchive:: Write  
 將指定的位元組數目寫入至封存。  
  
```  
void Write(const void* lpBuf, INT nMax);
```  
  
### <a name="parameters"></a>參數  
 *lpBuf*  
 使用者提供的緩衝區，其中包含寫入至封存的資料指標。  
  
 *nMax*  
 整數，指定要寫入至封存的位元組數目。  
  
### <a name="remarks"></a>備註  
 封存不會格式化位元組。  
  
 您可以使用`Write`成員函式，在您`Serialize`函式撰寫一般結構，包含在您的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]  
  
##  <a name="writeclass"></a>  CArchive::WriteClass  
 使用`WriteClass`來存放在衍生類別的序列化期間的基底類別版本和類別資訊。  
  
```  
void WriteClass(const CRuntimeClass* pClassRef);
```  
  
### <a name="parameters"></a>參數  
 *pClassRef*  
 指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)對應到要求的類別參考的結構。  
  
### <a name="remarks"></a>備註  
 `WriteClass` 寫入的參考[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)的基底類別的`CArchive`。 使用[CArchive::ReadClass](#readclass)來擷取的參考。  
  
 `WriteClass` 驗證封存的類別資訊是與您的執行階段類別相容。 如果不相容，`WriteClass`將會擲回[CArchiveException](../../mfc/reference/carchiveexception-class.md)。  
  
 必須使用執行階段類別[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)並[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)，否則`WriteClass`將會擲回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 您可以使用[SerializeClass](#serializeclass)而不是`WriteClass`，處理讀取和寫入的類別參考。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]  
  
##  <a name="writeobject"></a>  CArchive::WriteObject  
 儲存指定`CObject`至封存。  
  
```  
void WriteObject(const CObject* pOb);
```  
  
### <a name="parameters"></a>參數  
 *pOb*  
 儲存物件的常數指標。  
  
### <a name="remarks"></a>備註  
 通常會呼叫此函式`CArchive`插入 ( **<<**) 的多載運算子`CObject`。 `WriteObject`再轉而呼叫`Serialize`封存類別函式。  
  
 您必須使用 IMPLEMENT_SERIAL 巨集來啟用封存。 `WriteObject` 寫入封存中的 ASCII 類別名稱。 這個類別名稱會在之後的載入程序期間進行驗證。 特殊的編碼配置可避免不必要的重複項目類別的多個物件的類別名稱。 此配置也可避免備援的儲存體做為目標的多個指標的物件。  
  
 編碼方式 （包括 ASCII 類別名稱存在） 的確切物件是實作詳細資料，並可能在未來變更的程式庫版本。  
  
> [!NOTE]
>  完成建立、 刪除和更新您的所有物件，再開始將其封存。 如果您混用封存物件修改，將會損毀您的封存。  
  
### <a name="example"></a>範例  
 如需此類別的定義`CAge`，範例，請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)。  
  
 [!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]  
  
##  <a name="writestring"></a>  CArchive::WriteString  
 使用此成員函式將資料從緩衝區寫入相關聯的檔案`CArchive`物件。  
  
```  
void WriteString(LPCTSTR lpsz);
```  
  
### <a name="parameters"></a>參數  
 *lpsz*  
 指定包含 null 結尾的文字字串之緩衝區的指標。  
  
### <a name="remarks"></a>備註  
 結束的 null 字元 ('\0') 不會寫入至檔案，也不新行字元自動會寫入。  
  
 `WriteString` 以回應數個條件，包括磁碟已滿狀況，擲回的例外狀況。  
  
 `Write` 也可供使用，但它可以而不是終止的 null 字元，將要求的位元組數目來寫入檔案。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFile 類別](../../mfc/reference/cfile-class.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [CSocket 類別](../../mfc/reference/csocket-class.md)   
 [CSocketFile 類別](../../mfc/reference/csocketfile-class.md)
