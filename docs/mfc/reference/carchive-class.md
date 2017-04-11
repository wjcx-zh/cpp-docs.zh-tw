---
title: "CArchive 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- I/O [MFC], archiving objects
- CArchive class
- serialization [C++], CArchive class
- storage [C++], CArchive class
- data storage [C++], CArchive class
ms.assetid: 9e950d23-b874-456e-ae4b-fe00781a7699
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 3269aa447502b9581dd1238fbe972bef3a0ccde4
ms.lasthandoff: 04/01/2017

---
# <a name="carchive-class"></a>CArchive 類別
可讓您將複雜的網路的物件儲存在永久二進位格式 （通常是磁碟儲存體），之後會刪除這些物件仍然存在。  
  
## <a name="syntax"></a>語法  
  
```  
class CArchive  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CArchive::CArchive](#carchive)|建立 `CArchive` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CArchive::Abort](#abort)|關閉封存，而不擲回例外狀況。|  
|[CArchive::Close](#close)|排清 security 的資料，並中斷`CFile`。|  
|[CArchive::Flush](#flush)|從封存緩衝區會排清 security 的資料。|  
|[CArchive::GetFile](#getfile)|取得`CFile`物件指標在此封存。|  
|[CArchive::GetObjectSchema](#getobjectschema)|從呼叫`Serialize`函式來判斷要還原序列化物件的版本。|  
|[CArchive::IsBufferEmpty](#isbufferempty)|判斷是否已在 Windows Sockets 期間清空緩衝區接收程序。|  
|[CArchive::IsLoading](#isloading)|判斷封存是否正在載入。|  
|[CArchive::IsStoring](#isstoring)|決定是否要儲存封存。|  
|[CArchive::MapObject](#mapobject)|將物件放在對應圖，不會序列化至檔案，但卻是可供參考的子物件。|  
|[Carchive:: Read](#read)|讀取未經處理位元組。|  
|[CArchive::ReadClass](#readclass)|讀取類別參考先前儲存的`WriteClass`。|  
|[CArchive::ReadObject](#readobject)|呼叫物件的`Serialize`載入的函式。|  
|[CArchive::ReadString](#readstring)|讀取單行文字。|  
|[CArchive::SerializeClass](#serializeclass)|讀取或寫入類別參考給`CArchive`物件的方向`CArchive`。|  
|[CArchive::SetLoadParams](#setloadparams)|設定負載陣列成長時的大小。 已載入任何物件之前，或之前必須先呼叫`MapObject`或`ReadObject`呼叫。|  
|[CArchive::SetObjectSchema](#setobjectschema)|設定儲存在保存物件的物件結構描述。|  
|[CArchive::SetStoreParams](#setstoreparams)|設定雜湊資料表大小和用來識別唯一的物件序列化程序期間在對應的區塊大小。|  
|[Carchive:: Write](#write)|寫入未經處理位元組。|  
|[CArchive::WriteClass](#writeclass)|寫入至參考`CRuntimeClass`至`CArchive`。|  
|[CArchive::WriteObject](#writeobject)|呼叫物件的`Serialize`儲存函式。|  
|[CArchive::WriteString](#writestring)|寫入單一文字行。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CArchive::operator&lt;&lt;](#operator_lt_lt)|儲存物件和封存的基本型別。|  
|[CArchive::operator&gt;&gt;](#operator_gt_gt)|從封存載入物件與基本類型。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CArchive::m_pDocument](#m_pdocument)||  
  
## <a name="remarks"></a>備註  
 `CArchive`沒有基底類別。  
  
 稍後您可以載入物件從永續性儲存體，reconstituting 它們在記憶體中。 此程序可確保資料持續性稱為 < 序列化 >。  
  
 您可以將做為一種二進位資料流的保存物件。 輸入/輸出資料流，例如封存與檔案相關聯，並允許緩衝處理的寫入和讀取資料以及從儲存體。 輸入/輸出資料流處理 ASCII 字元序列，但封存處理有效、 nonredundant 格式的二進位物件資料。  
  
 您必須建立[CFile](../../mfc/reference/cfile-class.md)物件建立之前`CArchive`物件。 此外，您必須確定封存的載入/儲存狀態是與檔案的開啟模式相容。 您僅限於一個作用中的封存，每個檔案。  
  
 當您建構`CArchive`物件，您將它附加至類別的物件`CFile`（或衍生的類別），表示已開啟的檔案。 您也可以指定封存是否將用於載入或儲存。 A`CArchive`物件可以處理，而不是只是基本類型的物件[CObject](../../mfc/reference/cobject-class.md)-衍生的類別針對序列化所設計。 可序列化類別通常有`Serialize`成員函式，並通常使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)巨集 類別底下所述`CObject`。  
  
 多載的擷取 ( **>>**)，以及插入 ( **<<**) 是方便封存程式設計介面，支援這兩種基本類型的運算子和`CObject`-衍生的類別。  
  
 `CArchive`也支援使用 MFC Windows Sockets 類別程式設計[CSocket](../../mfc/reference/csocket-class.md)和[CSocketFile](../../mfc/reference/csocketfile-class.md)。 [IsBufferEmpty](#isbufferempty)成員函式支援這種用法。  
  
 如需有關`CArchive`，請參閱文章[序列化](../../mfc/serialization-in-mfc.md)和[Windows Sockets︰ 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CArchive`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="abort"></a>CArchive::Abort  
 呼叫此函式可關閉封存，而不擲回例外狀況。  
  
```  
void Abort ();
```  
  
### <a name="remarks"></a>備註  
 **CArchive**解構函式通常會呼叫**關閉**，這會清除任何未儲存的資料至相關聯`CFile`物件。 這可能會造成例外狀況。  
  
 當攔截這些例外狀況時，最好在其中使用**中止**，如此 destructing`CArchive`物件並不會進一步例外狀況。 當例外狀況處理、`CArchive::Abort`不會擲回例外狀況失敗因為不同的是[CArchive::Close](#close)，**中止**忽略失敗。  
  
 如果您使用**新**配置`CArchive`在堆積的物件，然後您必須關閉檔案後予以刪除。  
  
### <a name="example"></a>範例  
  請參閱範例的[CArchive::WriteClass](#writeclass)。  
  
##  <a name="carchive"></a>CArchive::CArchive  
 建構`CArchive`物件，並指定是否會使用用於載入或儲存物件。  
  
```  
CArchive(
    CFile* pFile,  
    UINT nMode,  
    int nBufSize = 4096,  
    void* lpBuf = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pFile`  
 指標`CFile`是最終的來源或目的地的持續性資料的物件。  
  
 `nMode`  
 指定物件是否會從載入或儲存至封存的旗標。 `nMode`參數必須要有下列值之一︰  
  
- **CArchive::load**載入從封存的資料。 只需要`CFile`讀取權限。  
  
- **CArchive::store**將資料儲存至封存。 需要`CFile`寫入權限。  
  
- **CArchive::bNoFlushOnDelete**可防止自動呼叫封存`Flush`封存解構函式呼叫時。 如果您設定此旗標時，您必須負責明確呼叫**關閉**解構函式呼叫之前。 如果不這麼做，您的資料將會損毀。  
  
 `nBufSize`  
 指定的內部檔案緩衝區大小，以位元組為單位的整數。 請注意，預設緩衝區大小是 4,096 個位元組。 如果您定期封存大型物件，您會改善效能，如果您使用較大的緩衝區大小是檔案的緩衝區大小的倍數。  
  
 `lpBuf`  
 使用者提供的緩衝區大小的選擇性指標`nBufSize`。 如果您未指定這個參數，封存會配置從本機堆積緩衝區並釋出其物件終結時。 封存後仍沒有可用的使用者提供的緩衝區。  
  
### <a name="remarks"></a>備註  
 建立封存之後，您無法變更此規格。  
  
 您不能使用`CFile`變更檔案的狀態，直到您關閉封存的作業。 任何這類作業將會損害封存的完整性。 您也可以取得從封存的檔案物件在序列化期間，隨時存取檔案指標的位置[GetFile](#getfile)成員函式，然後使用[CFile::GetPosition](../../mfc/reference/cfile-class.md#getposition)函式。 您應該呼叫[CArchive::Flush](#flush)取得檔案指標的位置之前。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization # 12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]  
  
##  <a name="close"></a>CArchive::Close  
 排清緩衝區中剩餘的任何資料，關閉封存，並中斷封存檔案。  
  
```  
void Close();
```  
  
### <a name="remarks"></a>備註  
 不允許的封存上任何進一步的作業。 關閉封存之後，您可以建立在同一個檔案的另一個封存，或您可以關閉檔案。  
  
 成員函式**關閉**可確保所有資料從封存都傳送至檔案，且它會讓封存無法使用。 若要完成從檔案傳輸到儲存體中，您必須先使用[CFile::Close](../../mfc/reference/cfile-class.md#close)然後摧毀`CFile`物件。  
  
### <a name="example"></a>範例  
  請參閱範例的[CArchive::WriteString](#writestring)。  
  
##  <a name="flush"></a>CArchive::Flush  
 強制封存緩衝區寫入檔案中剩餘的任何資料。  
  
```  
void Flush();
```  
  
### <a name="remarks"></a>備註  
 成員函式`Flush`可確保所有資料從 封存都傳送檔案。 您必須呼叫[CFile::Close](../../mfc/reference/cfile-class.md#close)完成從檔案傳輸到儲存媒體。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization # 13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]  
  
##  <a name="getfile"></a>CArchive::GetFile  
 取得`CFile`物件指標在此封存。  
  
```  
CFile* GetFile() const;  
```  
  
### <a name="return-value"></a>傳回值  
 常數指標`CFile`使用中的物件。  
  
### <a name="remarks"></a>備註  
 您必須清除之前使用封存`GetFile`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization # 14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]  
  
##  <a name="getobjectschema"></a>CArchive::GetObjectSchema  
 呼叫此函式從`Serialize`函式來判斷物件目前正在還原序列化的版本。  
  
```  
UINT GetObjectSchema();
```  
  
### <a name="return-value"></a>傳回值  
 在還原序列化期間，正在讀取物件的版本。  
  
### <a name="remarks"></a>備註  
 呼叫此函式時才有效`CArchive`正在載入物件 ( [CArchive::IsLoading](#isloading)傳回非零)。 它應該是中的第一個呼叫`Serialize`函式和呼叫一次。 傳回值 ( **UINT**)-1 表示是未知的版本號碼。  
  
 A `CObject`-可能會使用衍生的類別**VERSIONABLE_SCHEMA**結合 (使用位元`OR`) 本身的結構描述版本 (在`IMPLEMENT_SERIAL`巨集) 來建立 「 可控制版本物件，」 也就是物件的`Serialize`成員函式可以讀取多個版本。 預設 framework 功能 (不含**VERSIONABLE_SCHEMA**) 是版本不相符時擲回例外狀況。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization # 15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]  
  
##  <a name="isbufferempty"></a>CArchive::IsBufferEmpty  
 呼叫此成員函式，以判斷保存物件的內部緩衝區是否為空白。  
  
```  
BOOL IsBufferEmpty() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果封存的緩衝區是空的則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 此函式提供給支援與 MFC Windows Sockets 類別程式設計`CSocketFile`。 您不需要將它用於與相關聯的封存`CFile`物件。  
  
 使用的原因`IsBufferEmpty`與相關聯的封存`CSocketFile`物件是封存的緩衝區可能包含一個以上的訊息或記錄。 之後接收一個訊息，您應該使用`IsBufferEmpty`控制迴圈會繼續接收資料，直到緩衝區是空的。 如需詳細資訊，請參閱[接收](../../mfc/reference/casyncsocket-class.md#receive)類別成員函式`CAsyncSocket`，其示範如何使用`IsBufferEmpty`。  
  
 如需詳細資訊，請參閱[Windows Sockets︰ 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
##  <a name="isloading"></a>CArchive::IsLoading  
 判斷封存是否正在載入資料。  
  
```  
BOOL IsLoading() const;  
```  
  
### <a name="return-value"></a>傳回值  
 封存目前正用於載入; 如果為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 此成員函式會呼叫`Serialize`封存類別的函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization # 16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]  
  
##  <a name="isstoring"></a>CArchive::IsStoring  
 判斷封存是否正在儲存資料。  
  
```  
BOOL IsStoring() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果封存目前正用於儲存; 非零，否則便是 0。  
  
### <a name="remarks"></a>備註  
 此成員函式會呼叫`Serialize`封存類別的函式。  
  
 如果`IsStoring`保存的狀態為非零，則其`IsLoading`狀態為 0，反之亦然。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization # 17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]  
  
##  <a name="mapobject"></a>CArchive::MapObject  
 呼叫此成員函式置於不會真的序列化至檔案，對應的物件，但卻是可供參考的子物件。  
  
```  
void MapObject(const CObject* pOb);
```  
  
### <a name="parameters"></a>參數  
 `pOb`  
 要儲存之物件的常數指標。  
  
### <a name="remarks"></a>備註  
 例如，您可能不會序列化文件，但您會將序列化文件部分的項目。 藉由呼叫`MapObject`，您允許這些項目或子物件，參考文件。 此外，序列化的子項目可以序列化其`m_pDocument`返回指標。  
  
 您可以呼叫`MapObject`當您要儲存並載入從`CArchive`物件。 `MapObject`將指定的物件加入至所維護的內部資料結構`CArchive`物件在序列化和還原序列化，但不同於[ReadObject](#readobject)和[WriteObject](#writeobject)**，**未呼叫序列化的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization # 18](../../mfc/codesnippet/cpp/carchive-class_7.h)]  
  
 [!code-cpp[NVC_MFCSerialization # 19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]  
  
 [!code-cpp[NVC_MFCSerialization # 20](../../mfc/codesnippet/cpp/carchive-class_9.h)]  
  
 [!code-cpp[NVC_MFCSerialization # 21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]  
  
##  <a name="m_pdocument"></a>CArchive::m_pDocument  
 設定為**NULL**根據預設，此指標**CDocument**可以為任何項目設定的使用者`CArchive`想執行個體。  
  
```  
CDocument* m_pDocument;  
```  
  
### <a name="remarks"></a>備註  
 This 指標的常見用法是，傳遞要序列化的所有物件的序列化程序的其他資訊。 這藉由初始化與文件指標 ( **CDocument**-衍生的類別)，要序列化，如有必要的文件中的物件可以存取文件的方式。 此指標也會使用`COleClientItem`序列化期間的物件。  
  
 Framework 集`m_pDocument`使用者發出檔案時，正在序列化文件開啟或儲存命令。 如果您要序列化的物件連結與嵌入 (OLE) 容器文件開啟舊檔] 或 [儲存以外的原因，您必須明確設定`m_pDocument`。 例如，您需要執行此動作時序列化到剪貼簿容器文件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization # 35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]  
  
##  <a name="operator_lt_lt"></a>CArchive::operator&lt;&lt;  
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
 最後兩個以上的版本是特別針對儲存 64 位元整數。  
  
 如果您使用`IMPLEMENT_SERIAL`巨集，在您類別的實作，則為多載插入運算子`CObject`呼叫受保護**WriteObject**。 此函式，接著呼叫`Serialize`函式的類別。  
  
 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)插入運算子 (<) supports diagnostic dumping and storing to an archive. supports="" diagnostic="" dumping="" and="" storing="" to="" an=""></) supports diagnostic dumping and storing to an archive.>  
  
### <a name="example"></a>範例  
 這個範例示範如何使用`CArchive`插入運算子< with="" the="">`int`和`long`型別。  
  
 [!code-cpp[NVC_MFCSerialization # 31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]  
  
### <a name="example"></a>範例  
 2 本範例示範如何使用`CArchive`插入運算子< with="" the="">`CStringT`型別。  
  
 [!code-cpp[NVC_MFCSerialization # 32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]  
  
##  <a name="operator_gt_gt"></a>CArchive::operator&gt;&gt;  
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
 最後兩個以上的版本是特別針對載入 64 位元整數。  
  
 如果您使用`IMPLEMENT_SERIAL`巨集，在您類別的實作，然後擷取運算子多載`CObject`呼叫受保護**ReadObject**函式 （非零的執行階段類別的指標）。 此函式，接著呼叫`Serialize`函式的類別。  
  
 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)引出運算子 (>) 支援從封存的載入。  
  
### <a name="example"></a>範例  
 這個範例示範如何使用`CArchive`引出運算子 >> 與`int`型別。  
  
 [!code-cpp[NVC_MFCSerialization # 33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]  
  
### <a name="example"></a>範例  
 這個範例示範如何使用`CArchive`插入和擷取運算子\<和 >> 與`CStringT`型別。  
  
 [!code-cpp[NVC_MFCSerialization # 34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]  
  
##  <a name="read"></a>Carchive:: Read  
 從封存中讀取指定的位元組數目。  
  
```  
UINT Read(void* lpBuf, UINT nMax);
```  
  
### <a name="parameters"></a>參數  
 `lpBuf`  
 從封存讀取使用者提供的緩衝區，以接收資料的指標。  
  
 `nMax`  
 不帶正負號的整數，指定的位元組數目從封存讀取。  
  
### <a name="return-value"></a>傳回值  
 不帶正負號的整數，其中包含實際讀取的位元組數目。 如果傳回的值小於要求的數目，已達到檔案結尾。 檔案結尾條件會擲不回任何例外狀況。  
  
### <a name="remarks"></a>備註  
 封存不會解譯的位元組。  
  
 您可以使用**讀取**成員函式內您`Serialize`函式來讀取您的物件中所包含的一般結構。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization # 24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]  
  
##  <a name="readclass"></a>CArchive::ReadClass  
 呼叫此成員函式讀取之前儲存與類別參考[WriteClass](#writeclass)。  
  
```  
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,  
    UINT* pSchema = NULL,  
    DWORD* pObTag = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pClassRefRequested`  
 指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)對應到要求的類別參考的結構。 可以是**NULL**。  
  
 `pSchema`  
 結構描述之前儲存的執行階段類別的指標。  
  
 `pObTag`  
 指的是物件的唯一的標記數目。 供內部使用的實作[ReadObject](#readobject)。 公開的進階程式設計; 僅限`pObTag`通常應該是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構。  
  
### <a name="remarks"></a>備註  
 如果`pClassRefRequested`不**NULL**，`ReadClass`驗證封存的類別資訊是否相容於執行階段類別。 如果不相容，`ReadClass`將會擲回[CArchiveException](../../mfc/reference/carchiveexception-class.md)。  
  
 執行階段類別必須使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)，否則`ReadClass`將會擲回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 如果`pSchema`是**NULL**，結構描述的預存的類別可以藉由呼叫擷取[CArchive::GetObjectSchema](#getobjectschema)，否則**\*** `pSchema`會包含執行階段類別之前儲存的結構描述。  
  
 您可以使用[SerializeClass](#serializeclass)而不是`ReadClass`，處理進行讀取和寫入的類別參考。  
  
### <a name="example"></a>範例  
  請參閱範例的[CArchive::WriteClass](#writeclass)。  
  
##  <a name="readobject"></a>CArchive::ReadObject  
 從封存讀取物件資料，並建構適當類型的物件。  
  
```  
CObject* ReadObject(const CRuntimeClass* pClass);
```  
  
### <a name="parameters"></a>參數  
 `pClass`  
 常數指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)對應至您要讀取之物件的結構。  
  
### <a name="return-value"></a>傳回值  
 A [CObject](../../mfc/reference/cobject-class.md)必須安全地轉換成正確的指標使用衍生類別[cobject:: Iskindof](../../mfc/reference/cobject-class.md#iskindof)。  
  
### <a name="remarks"></a>備註  
 通常會呼叫此函式`CArchive`擷取 ( **>>**) 的多載運算子[CObject](../../mfc/reference/cobject-class.md)指標。 **ReadObject**，又呼叫`Serialize`封存類別函式。  
  
 如果您提供非零`pClass`參數，藉由取得[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)巨集，則此函式會驗證封存的物件的執行階段類別。 這是假設您已經使用`IMPLEMENT_SERIAL`類別的實作中的巨集。  
  
### <a name="example"></a>範例  
  請參閱範例的[CArchive::WriteObject](#writeobject)。  
  
##  <a name="readstring"></a>CArchive::ReadString  
 呼叫此成員函式相關聯的檔案中的緩衝區所讀取的文字資料`CArchive`物件。  
  
```  
BOOL ReadString(CString& rString); 
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```  
  
### <a name="parameters"></a>參數  
 `rString`  
 若要參考[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，就會在讀取從 CArchive 物件相關聯的檔案之後，包含結果的字串。  
  
 `lpsz`  
 指定使用者提供的緩衝區會接收以 null 結尾的文字字串的指標。  
  
 `nMax`  
 指定要讀取的字元數目上限。 應該有一個大小大於或等於*lpsz*緩衝區。  
  
### <a name="return-value"></a>傳回值  
 傳回的版本中**BOOL**， **TRUE**如果登錄成功。**FALSE**否則。  
  
 傳回的版本中`LPTSTR`，包含文字資料的緩衝區的指標**NULL**如果已到達檔案結尾。  
  
### <a name="remarks"></a>備註  
 成員函式的版本中`nMax`參數時，緩衝區會儲存高達限制為`nMax`-1 個字元。 停止讀取歸位字元傳回換行字元組。 一律會移除尾端新行字元。 在任一情況下，會附加 null 字元 ('\0')。  
  
 [Carchive:: Read](#read)也會提供的文字模式的輸入，但它不會終止歸位字元傳回換行字元組。  
  
### <a name="example"></a>範例  
  請參閱範例的[CArchive::WriteString](#writestring)。  
  
##  <a name="serializeclass"></a>CArchive::SerializeClass  
 當您想要儲存並載入基底類別的版本資訊，請呼叫此成員函式。  
  
```  
void SerializeClass(const CRuntimeClass* pClassRef);
```  
  
### <a name="parameters"></a>參數  
 `pClassRef`  
 基底類別的執行階段類別物件的指標。  
  
### <a name="remarks"></a>備註  
 `SerializeClass`讀取或寫入至類別，以參考`CArchive`物件，視方向而定`CArchive`。 使用`SerializeClass`取代[ReadClass](#readclass)和[WriteClass](#writeclass)作為便利的方式來序列化基底類別物件。`SerializeClass`需要較少程式碼和較少的參數。  
  
 像`ReadClass`，`SerializeClass`驗證封存的類別資訊是否相容於執行階段類別。 如果不相容，`SerializeClass`將會擲回[CArchiveException](../../mfc/reference/carchiveexception-class.md)。  
  
 執行階段類別必須使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)，否則`SerializeClass`將會擲回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 使用[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)巨集，以擷取其值`pRuntimeClass`參數。 您必須使用基底類別[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)巨集。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization # 25](../../mfc/codesnippet/cpp/carchive-class_17.h)]  
  
##  <a name="setloadparams"></a>CArchive::SetLoadParams  
 呼叫`SetLoadParams`當您要讀取大量的`CObject`-從封存衍生物件。  
  
```  
void SetLoadParams(UINT nGrowBy = 1024);
```  
  
### <a name="parameters"></a>參數  
 `nGrowBy`  
 如果是必要的大小增加配置項目位置最小數目。  
  
### <a name="remarks"></a>備註  
 `CArchive`您可以使用負載陣列來解析物件儲存在封存中的參考。 `SetLoadParams`可讓您設定的負載陣列成長的大小。  
  
 您必須呼叫`SetLoadParams`載入的任何物件之後，或之後[MapObject](#mapobject)或[ReadObject](#readobject)呼叫。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization # 26](../../mfc/codesnippet/cpp/carchive-class_18.h)]  
  
##  <a name="setobjectschema"></a>CArchive::SetObjectSchema  
 呼叫此成員函式，來設定物件結構描述儲存在封存物件`nSchema`。  
  
```  
void SetObjectSchema(UINT nSchema);
```  
  
### <a name="parameters"></a>參數  
 `nSchema`  
 指定物件的結構描述。  
  
### <a name="remarks"></a>備註  
 下次呼叫[GetObjectSchema](#getobjectschema)會傳回值儲存在`nSchema`。  
  
 使用`SetObjectSchema`進行進階的版本控制; 比方說，當您想要強制執行特定版本中讀取`Serialize`衍生類別的函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization # 27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]  
  
##  <a name="setstoreparams"></a>CArchive::SetStoreParams  
 使用`SetStoreParams`時儲存大量的`CObject`-衍生封存中的物件。  
  
```  
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```  
  
### <a name="parameters"></a>參數  
 *nHashSize*  
 將對應的介面指標的雜湊資料表大小。 應該是質數。  
  
 `nBlockSize`  
 指定的記憶體配置資料粒度來擴充參數。 應該是 2 的為了達到最佳效能的乘冪。  
  
### <a name="remarks"></a>備註  
 `SetStoreParams`可讓您設定的雜湊資料表大小，以及用來識別唯一的物件序列化程序期間在對應的區塊大小。  
  
 您必須呼叫`SetStoreParams`儲存任何物件後，或之後[MapObject](#mapobject)或[WriteObject](#writeobject)呼叫。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization # 26](../../mfc/codesnippet/cpp/carchive-class_18.h)]  
  
##  <a name="write"></a>Carchive:: Write  
 將指定的位元組數目寫入至封存。  
  
```  
void Write(const void* lpBuf, INT nMax);
```  
  
### <a name="parameters"></a>參數  
 `lpBuf`  
 使用者提供的緩衝區，其中包含要寫入至封存的資料指標。  
  
 `nMax`  
 指定要寫入至封存的位元組數目的整數。  
  
### <a name="remarks"></a>備註  
 封存不會格式化位元組。  
  
 您可以使用**寫入**成員函式內您`Serialize`函式撰寫一般結構包含在您的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization # 23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]  
  
##  <a name="writeclass"></a>CArchive::WriteClass  
 使用`WriteClass`來存放在衍生類別的序列化期間的基底類別版本和類別資訊。  
  
```  
void WriteClass(const CRuntimeClass* pClassRef);
```  
  
### <a name="parameters"></a>參數  
 `pClassRef`  
 指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)對應到要求的類別參考的結構。  
  
### <a name="remarks"></a>備註  
 `WriteClass`寫入至參考[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)基底類別`CArchive`。 使用[CArchive::ReadClass](#readclass)來擷取的參照。  
  
 `WriteClass`確認已封存的類別資訊與執行階段類別相容。 如果不相容，`WriteClass`將會擲回[CArchiveException](../../mfc/reference/carchiveexception-class.md)。  
  
 執行階段類別必須使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)，否則`WriteClass`將會擲回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 您可以使用[SerializeClass](#serializeclass)而不是`WriteClass`，處理進行讀取和寫入的類別參考。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization # 28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]  
  
##  <a name="writeobject"></a>CArchive::WriteObject  
 儲存指定`CObject`到封存。  
  
```  
void WriteObject(const CObject* pOb);
```  
  
### <a name="parameters"></a>參數  
 `pOb`  
 要儲存之物件的常數指標。  
  
### <a name="remarks"></a>備註  
 通常會呼叫此函式`CArchive`插入 ( **<<**) 的多載運算子`CObject`。 **WriteObject**，又呼叫`Serialize`封存類別函式。  
  
 您必須使用`IMPLEMENT_SERIAL`巨集，以啟用封存。 **WriteObject**寫入封存 ASCII 類別名稱。 這個類別名稱會在載入程序之後的期間進行驗證。 特殊的編碼配置會防止不必要的重複類別的多個物件的類別名稱。 這個配置也會防止備援儲存體做為目標的多個指標的物件。  
  
 完全編碼方式 （包括 ASCII 類別名稱存在） 的物件是實作細節，並可能在未來變更的程式庫版本。  
  
> [!NOTE]
>  完成建立、 刪除和封存它們之前，更新所有的物件。 如果您混用封存物件修改，將會損毀您的封存。  
  
### <a name="example"></a>範例  
 如需此類別的定義`CAge`，請參閱範例的[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)。  
  
 [!code-cpp[NVC_MFCSerialization # 29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]  
  
##  <a name="writestring"></a>CArchive::WriteString  
 使用此成員函式將資料從緩衝區寫入檔案與相關聯`CArchive`物件。  
  
```  
void WriteString(LPCTSTR lpsz);
```  
  
### <a name="parameters"></a>參數  
 `lpsz`  
 指定包含 null 結尾的文字字串之緩衝區的指標。  
  
### <a name="remarks"></a>備註  
 結束的 null 字元 ('\0') 不會寫入檔案。也不新行字元自動會寫入。  
  
 `WriteString`擲回例外狀況以回應數個條件，包括磁碟已滿的情況。  
  
 **寫入**也可供使用，但而不是終止 null 字元，它必須將要求的位元組數目寫入檔案。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization # 30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFile 類別](../../mfc/reference/cfile-class.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [CSocket 類別](../../mfc/reference/csocket-class.md)   
 [CSocketFile 類別](../../mfc/reference/csocketfile-class.md)

