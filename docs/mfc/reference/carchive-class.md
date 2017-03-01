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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 501b365678a45148aabe638ff341f3ae995e4ab5
ms.lasthandoff: 02/24/2017

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
  
|名稱|說明|  
|----------|-----------------|  
|[CArchive::Abort](#abort)|關閉封存檔，而不擲回例外狀況。|  
|[CArchive::Close](#close)|清除未寫入的資料，並中斷`CFile`。|  
|[CArchive::Flush](#flush)|從封存緩衝區清除未寫入的資料。|  
|[CArchive::GetFile](#getfile)|取得`CFile`此封存檔的物件指標。|  
|[CArchive::GetObjectSchema](#getobjectschema)|從呼叫`Serialize`函式來判斷正在還原序列化物件的版本。|  
|[CArchive::IsBufferEmpty](#isbufferempty)|判斷是否已在 Windows Sockets 期間清空緩衝區接收程序。|  
|[CArchive::IsLoading](#isloading)|判斷是否正在載入封存。|  
|[CArchive::IsStoring](#isstoring)|決定是否要儲存封存。|  
|[CArchive::MapObject](#mapobject)|將物件放在對應，不會序列化至檔案，但卻是可供參考的子物件。|  
|[Carchive:: Read](#read)|讀取未經處理位元組。|  
|[CArchive::ReadClass](#readclass)|讀取以先前儲存的類別參考`WriteClass`。|  
|[CArchive::ReadObject](#readobject)|呼叫物件的`Serialize`載入的函式。|  
|[CArchive::ReadString](#readstring)|讀取一行文字。|  
|[CArchive::SerializeClass](#serializeclass)|讀取或寫入類別參考給`CArchive`物件的方向根據`CArchive`。|  
|[CArchive::SetLoadParams](#setloadparams)|設定負載陣列成長時的大小。 已載入任何物件之前，或之前必須先呼叫`MapObject`或`ReadObject`呼叫。|  
|[CArchive::SetObjectSchema](#setobjectschema)|設定儲存在保存物件的物件結構描述。|  
|[CArchive::SetStoreParams](#setstoreparams)|設定雜湊資料表大小和用來識別唯一的物件在序列化程序對應的區塊大小。|  
|[Carchive:: Write](#write)|寫入未經處理位元組。|  
|[CArchive::WriteClass](#writeclass)|寫入至參考`CRuntimeClass`到`CArchive`。|  
|[CArchive::WriteObject](#writeobject)|呼叫物件的`Serialize`儲存函式。|  
|[CArchive::WriteString](#writestring)|寫入一行文字。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CArchive::operator&lt;&lt;](#operator_lt_lt)|儲存物件和封存的基本型別。|  
|[CArchive::operator&gt;&gt;](#operator_gt_gt)|從封存載入物件和基本型別。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CArchive::m_pDocument](#m_pdocument)||  
  
## <a name="remarks"></a>備註  
 `CArchive`沒有基底類別。  
  
 稍後您可以載入物件從永續性儲存體，reconstituting 它們在記憶體中。 此程序可確保資料永續性稱為 「 序列化 」。  
  
 您可以將封存物件的二進位資料流。 如同輸入/輸出資料流中，封存會與檔案相關聯，而且允許的緩衝處理的寫入和讀取的資料儲存體的出入。 輸入/輸出資料流處理 ASCII 字元序列，但保存處理有效、 nonredundant 格式的二進位物件資料。  
  
 您必須建立[CFile](../../mfc/reference/cfile-class.md)物件才能建立`CArchive`物件。 此外，您必須確定封存的負載/存放區的狀態是與檔案的開啟模式相容。 您僅限於一個作用中的封存每個檔案。  
  
 當您建構`CArchive`物件，將它附加到類別的物件`CFile`（或衍生的類別），代表開啟的檔案。 您也可以指定封存是否將用於載入或儲存。 A`CArchive`基本型別不僅的物件，物件可以處理[CObject](../../mfc/reference/cobject-class.md)-衍生類別序列化而設計。 可序列化的類別通常有`Serialize`成員函式，並且通常使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)巨集 類別底下所述`CObject`。  
  
 多載的擷取 ( ** >> **) 和插入 ( ** << **) 是方便封存程式設計介面，支援這兩種基本類型的運算子和`CObject`-衍生的類別。  
  
 `CArchive`也支援使用 MFC Windows Sockets 類別的程式設計[CSocket](../../mfc/reference/csocket-class.md)和[CSocketFile](../../mfc/reference/csocketfile-class.md)。 [IsBufferEmpty](#isbufferempty)成員函式支援這種用法。  
  
 如需有關`CArchive`，請參閱文章[序列化](../../mfc/serialization-in-mfc.md)和[Windows Sockets︰ 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CArchive`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="a-nameaborta--carchiveabort"></a><a name="abort"></a>CArchive::Abort  
 呼叫此函式來關閉封存，而不擲回例外狀況。  
  
```  
void Abort ();
```  
  
### <a name="remarks"></a>備註  
 **CArchive**解構函式通常會呼叫**關閉**，這會清除任何尚未儲存的資料至相關聯`CFile`物件。 這會造成例外狀況。  
  
 當攔截這些例外狀況時，最好在其中使用**中止**，好讓 destructing`CArchive`物件不會造成進一步的例外狀況。 當例外狀況處理、`CArchive::Abort`不會擲回例外狀況失敗因為不同的是[CArchive::Close](#close)，**中止**忽略失敗。  
  
 如果您使用**新**配置`CArchive`您必須在關閉檔案後刪除該物件在堆積上。  
  
### <a name="example"></a>範例  
  請參閱範例[CArchive::WriteClass](#writeclass)。  
  
##  <a name="a-namecarchivea--carchivecarchive"></a><a name="carchive"></a>CArchive::CArchive  
 建構`CArchive`物件，並指定是否將使用以載入或儲存物件。  
  
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
 指定的物件會從載入或儲存至封存的旗標。 `nMode`參數都必須有下列值之一︰  
  
- **CArchive::load**從封存中載入資料。 只需要`CFile`的讀取權限。  
  
- **CArchive::store**將資料儲存至封存。 需要`CFile`的寫入權限。  
  
- **CArchive::bNoFlushOnDelete**防止自動呼叫封存`Flush`封存解構函式呼叫時。 如果您設定此旗標，您必須負責明確呼叫**關閉**解構函式呼叫之前。 如果不這麼做，您的資料將會損毀。  
  
 `nBufSize`  
 整數，指定內部檔案緩衝區的大小 （位元組）。 請注意，預設緩衝區大小是 4096 個位元組。 如果您定期備份大型物件，您將會改善效能，如果您使用較大的緩衝區大小是檔案緩衝區大小的倍數。  
  
 `lpBuf`  
 使用者提供的緩衝區大小的選擇性指標`nBufSize`。 如果未指定此參數，封存會配置緩衝區，以從本機堆積和終結物件時，會釋放它。 封存後仍沒有可用的使用者提供的緩衝區。  
  
### <a name="remarks"></a>備註  
 您已建立封存之後，您無法變更此規格。  
  
 您不能使用`CFile`更改檔案的狀態，直到您關閉封存作業。 這項操作將損害封存的完整性。 您也可以取得從封存的檔案物件在序列化期間，隨時存取檔案指標位置的[GetFile](#getfile)成員函式，然後使用[CFile::GetPosition](../../mfc/reference/cfile-class.md#getposition)函式。 您應該呼叫[CArchive::Flush](#flush)之前取得的檔案指標的位置。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization #&12;](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]  
  
##  <a name="a-nameclosea--carchiveclose"></a><a name="close"></a>CArchive::Close  
 清除任何緩衝區中剩餘的資料、 關閉封存，並中斷封存檔案。  
  
```  
void Close();
```  
  
### <a name="remarks"></a>備註  
 不允許的封存上任何進一步的作業。 關閉封存之後，您可以建立在同一個檔案的另一個封存檔，或您可以關閉檔案。  
  
 成員函式**關閉**可確保所有資料從封存都傳送到檔案，且它會讓封存無法使用。 若要完成從檔案傳輸至儲存媒體中，您必須先使用[CFile::Close](../../mfc/reference/cfile-class.md#close)然後損毀`CFile`物件。  
  
### <a name="example"></a>範例  
  請參閱範例[CArchive::WriteString](#writestring)。  
  
##  <a name="a-nameflusha--carchiveflush"></a><a name="flush"></a>CArchive::Flush  
 強制寫入檔案的封存緩衝區中剩餘的任何資料。  
  
```  
void Flush();
```  
  
### <a name="remarks"></a>備註  
 成員函式`Flush`可確保所有資料從封存都傳送到檔案。 您必須呼叫[CFile::Close](../../mfc/reference/cfile-class.md#close)完成檔案傳輸至儲存媒體。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization #&13;](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]  
  
##  <a name="a-namegetfilea--carchivegetfile"></a><a name="getfile"></a>CArchive::GetFile  
 取得`CFile`此封存檔的物件指標。  
  
```  
CFile* GetFile() const;  
```  
  
### <a name="return-value"></a>傳回值  
 常數指標`CFile`使用中的物件。  
  
### <a name="remarks"></a>備註  
 您必須清除之前使用封存`GetFile`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization #&14;](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]  
  
##  <a name="a-namegetobjectschemaa--carchivegetobjectschema"></a><a name="getobjectschema"></a>CArchive::GetObjectSchema  
 呼叫此函式，從`Serialize`函式來判斷目前正在還原序列化物件的版本。  
  
```  
UINT GetObjectSchema();
```  
  
### <a name="return-value"></a>傳回值  
 還原序列化期間，物件所讀取的版本。  
  
### <a name="remarks"></a>備註  
 呼叫此函式時，才有效`CArchive`載入物件 ( [CArchive::IsLoading](#isloading)傳回非零值)。 它應該是在第一次呼叫`Serialize`函式和被呼叫一次。 傳回值 ( **UINT**)-1 表示版本號碼不明。  
  
 A `CObject`-衍生的類別可以使用**VERSIONABLE_SCHEMA**結合 (使用位元`OR`) 本身的結構描述版本 (在`IMPLEMENT_SERIAL`巨集) 來建立 「 可控制版本的物件 」 也就是物件的`Serialize`成員函式可以讀取多個版本。 預設的架構功能 (不含**VERSIONABLE_SCHEMA**) 是版本不相符時所擲回例外狀況。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization #&15;](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]  
  
##  <a name="a-nameisbufferemptya--carchiveisbufferempty"></a><a name="isbufferempty"></a>CArchive::IsBufferEmpty  
 呼叫此成員函式，以判斷保存物件的內部緩衝區是否為空白。  
  
```  
BOOL IsBufferEmpty() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果封存的緩衝區是空的。否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式提供給支援程式設計與 MFC Windows Sockets 類別`CSocketFile`。 您不需要將它用於與相關聯的封存`CFile`物件。  
  
 使用的理由`IsBufferEmpty`與相關聯的封存`CSocketFile`物件是封存的緩衝區可能包含多個訊息或記錄。 之後收到一則訊息，您應使用`IsBufferEmpty`來控制迴圈，它會繼續接收資料，直到緩衝區是空的。 如需詳細資訊，請參閱[接收](../../mfc/reference/casyncsocket-class.md#receive)類別成員函式`CAsyncSocket`，以了解如何使用`IsBufferEmpty`。  
  
 如需詳細資訊，請參閱[Windows Sockets︰ 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
##  <a name="a-nameisloadinga--carchiveisloading"></a><a name="isloading"></a>CArchive::IsLoading  
 判斷是否載入保存資料。  
  
```  
BOOL IsLoading() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果目前正在載入; 使用封存為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式會呼叫`Serialize`封存類別的函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization #&16;](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]  
  
##  <a name="a-nameisstoringa--carchiveisstoring"></a><a name="isstoring"></a>CArchive::IsStoring  
 決定是否保存正在儲存資料。  
  
```  
BOOL IsStoring() const;  
```  
  
### <a name="return-value"></a>傳回值  
 保存目前正在使用儲存; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式會呼叫`Serialize`封存類別的函式。  
  
 如果`IsStoring`保存的狀態為非零值，則其`IsLoading`狀態為 0，反之亦然。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization #&17;](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]  
  
##  <a name="a-namemapobjecta--carchivemapobject"></a><a name="mapobject"></a>CArchive::MapObject  
 呼叫此成員函式，讓物件的對應，其實不會序列化至檔案，但可供參考的子物件。  
  
```  
void MapObject(const CObject* pOb);
```  
  
### <a name="parameters"></a>參數  
 `pOb`  
 所儲存之物件的常數指標。  
  
### <a name="remarks"></a>備註  
 例如，您可能不會序列化文件，但您會將序列化文件的項目。 藉由呼叫`MapObject`，您允許這些項目或子物件，以參考文件。 此外，序列化的子項目可以序列化其`m_pDocument`返回指標。  
  
 您可以呼叫`MapObject`當您要存放區，並從載入`CArchive`物件。 `MapObject`將指定的物件所維護的內部資料結構`CArchive`物件序列化和還原序列化期間，但不同於[ReadObject](#readobject)和[WriteObject](#writeobject)**，**不會呼叫序列化的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization #&18;](../../mfc/codesnippet/cpp/carchive-class_7.h)]  
  
 [!code-cpp[NVC_MFCSerialization #&19;](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]  
  
 [!code-cpp[NVC_MFCSerialization #&20;](../../mfc/codesnippet/cpp/carchive-class_9.h)]  
  
 [!code-cpp[NVC_MFCSerialization #&21;](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]  
  
##  <a name="a-namempdocumenta--carchivempdocument"></a><a name="m_pdocument"></a>CArchive::m_pDocument  
 設定為**NULL**根據預設，此指標**CDocument**可以到任何項目設定的使用者`CArchive`想執行個體。  
  
```  
CDocument* m_pDocument;  
```  
  
### <a name="remarks"></a>備註  
 This 指標的常見用法是，傳遞到所有正在序列化的物件序列化程序的其他資訊。 這藉由初始化與文件的指標 ( **CDocument**-衍生的類別) 的序列化，如有必要的文件中的物件可以存取文件的方式。 這個指標也會使用`COleClientItem`在序列化期間的物件。  
  
 Framework 集`m_pDocument`文件序列化當使用者提出檔案開啟或儲存命令。 如果您要序列化的物件連結與嵌入 (OLE) 容器文件開啟舊檔] 或 [儲存以外的原因，您必須明確設定`m_pDocument`。 比方說，這樣當序列化至剪貼簿容器文件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization #&35;](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]  
  
##  <a name="a-nameoperatorltlta--carchiveoperator-ltlt"></a><a name="operator_lt_lt"></a>CArchive::operator&lt;&lt;  
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
 A`CArchive`可讓多個插入運算子，在同一行的參考。  
  
### <a name="remarks"></a>備註  
 最後兩個以上的版本是專為儲存 64 位元整數。  
  
 如果您使用`IMPLEMENT_SERIAL`巨集，在您類別的實作，則為多載插入運算子`CObject`呼叫受保護**WriteObject**。 這個函式，接著呼叫`Serialize`類別函式。  
  
 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)插入運算子 (<) supports diagnostic dumping and storing to an archive. supports="" diagnostic="" dumping="" and="" storing="" to="" an=""></) supports diagnostic dumping and storing to an archive.>  
  
### <a name="example"></a>範例  
 這個範例示範如何使用`CArchive`插入運算子< with="" the="">`int`和`long`型別。  
  
 [!code-cpp[NVC_MFCSerialization #&31;](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]  
  
### <a name="example"></a>範例  
 2 這個範例示範如何使用`CArchive`插入運算子< with="" the="">`CStringT`型別。  
  
 [!code-cpp[NVC_MFCSerialization #&32;](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]  
  
##  <a name="a-nameoperatorgtgta--carchiveoperator-gtgt"></a><a name="operator_gt_gt"></a>CArchive::operator&gt;&gt;  
 從封存載入指定的一或多個基本型別。  
  
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
 A`CArchive`可讓多個擷取運算子在同一行的參考。  
  
### <a name="remarks"></a>備註  
 最後兩個以上的版本是專為載入 64 位元整數。  
  
 如果您使用`IMPLEMENT_SERIAL`巨集，在類別實作中，然後擷取運算子多載的`CObject`呼叫受保護**ReadObject**函式 （非零的執行階段類別的指標）。 這個函式，接著呼叫`Serialize`類別函式。  
  
 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)引出運算子 (>) 可支援從封存載入。  
  
### <a name="example"></a>範例  
 這個範例示範如何使用`CArchive`引出運算子 >> 與`int`型別。  
  
 [!code-cpp[NVC_MFCSerialization #&33;](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]  
  
### <a name="example"></a>範例  
 這個範例示範如何使用`CArchive`插入和擷取運算子\<和 >> 與`CStringT`型別。  
  
 [!code-cpp[NVC_MFCSerialization #&34;](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]  
  
##  <a name="a-namereada--carchiveread"></a><a name="read"></a>Carchive:: Read  
 從封存中讀取指定的位元組數目。  
  
```  
UINT Read(void* lpBuf, UINT nMax);
```  
  
### <a name="parameters"></a>參數  
 `lpBuf`  
 從封存讀取使用者提供的緩衝區所要接收資料的指標。  
  
 `nMax`  
 不帶正負號的整數，指定的位元組數目從封存中讀取。  
  
### <a name="return-value"></a>傳回值  
 不帶正負號的整數，其中包含實際讀取的位元組數目。 如果傳回的值小於所要求的數目，已達到檔案結尾。 檔案結尾的條件會擲不回任何例外狀況。  
  
### <a name="remarks"></a>備註  
 封存不會解譯的位元組。  
  
 您可以使用**讀取**成員函式內您`Serialize`函式來讀取您的物件中所包含的一般結構。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization #&24;](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]  
  
##  <a name="a-namereadclassa--carchivereadclass"></a><a name="readclass"></a>CArchive::ReadClass  
 呼叫此成員函式，來讀取先前儲存的類別參考[WriteClass](#writeclass)。  
  
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
 結構描述的預存的執行階段類別的指標。  
  
 `pObTag`  
 物件的唯一標籤指的是數字。 實作會在內部利用[ReadObject](#readobject)。 如需進階程式設計僅公開`pObTag`通常應該是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構。  
  
### <a name="remarks"></a>備註  
 如果`pClassRefRequested`不**NULL**，`ReadClass`確認封存的類別資訊是與執行階段類別。 如果不相容，`ReadClass`將會擲回[CArchiveException](../../mfc/reference/carchiveexception-class.md)。  
  
 必須使用執行階段類別[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)，否則`ReadClass`將會擲回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 如果`pSchema`是**NULL**，可以擷取結構描述的預存的類別，藉由呼叫[CArchive::GetObjectSchema](#getobjectschema)，否則** \* ** `pSchema`將包含執行階段類別之前儲存的結構描述。  
  
 您可以使用[SerializeClass](#serializeclass)而不是`ReadClass`，以處理讀取和寫入的類別參考。  
  
### <a name="example"></a>範例  
  請參閱範例[CArchive::WriteClass](#writeclass)。  
  
##  <a name="a-namereadobjecta--carchivereadobject"></a><a name="readobject"></a>CArchive::ReadObject  
 從封存讀取物件資料，並建構適當型別的物件。  
  
```  
CObject* ReadObject(const CRuntimeClass* pClass);
```  
  
### <a name="parameters"></a>參數  
 `pClass`  
 常數指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)對應至您要讀取之物件的結構。  
  
### <a name="return-value"></a>傳回值  
 A [CObject](../../mfc/reference/cobject-class.md)必須安全地轉換成正確的指標使用衍生類別[cobject:: Iskindof](../../mfc/reference/cobject-class.md#iskindof)。  
  
### <a name="remarks"></a>備註  
 此函式通常會呼叫`CArchive`擷取 ( ** >> **) 運算子多載的[CObject](../../mfc/reference/cobject-class.md)指標。 **ReadObject**，轉而呼叫`Serialize`封存類別函式。  
  
 如果您提供非零`pClass`參數，藉由取得[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)巨集，則函式會驗證保存物件的執行階段類別。 這是假設您已使用`IMPLEMENT_SERIAL`類別的實作中的巨集。  
  
### <a name="example"></a>範例  
  請參閱範例[CArchive::WriteObject](#writeobject)。  
  
##  <a name="a-namereadstringa--carchivereadstring"></a><a name="readstring"></a>CArchive::ReadString  
 呼叫此成員函式相關聯的檔案從緩衝區讀取文字資料`CArchive`物件。  
  
```  
BOOL ReadString(CString& rString); 
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```  
  
### <a name="parameters"></a>參數  
 `rString`  
 參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)讀取從 CArchive 物件相關聯的檔案之後將包含結果字串。  
  
 `lpsz`  
 指定的使用者提供的緩衝區，將會收到 null 結尾的文字字串的指標。  
  
 `nMax`  
 指定要讀取的字元數目上限。 應該有一個大小大於或等於*lpsz*緩衝區。  
  
### <a name="return-value"></a>傳回值  
 傳回的版本中**BOOL**， **TRUE**如果登錄成功。**FALSE**否則。  
  
 傳回的版本中`LPTSTR`，包含文字資料; 緩衝區的指標**NULL**如果已到達檔案結尾。  
  
### <a name="remarks"></a>備註  
 成員函式版本`nMax`參數時，緩衝區會保留高達的限制`nMax`-1 個字元。 歸位字元復位換行組停止讀取。 尾端新行字元會永遠移除。 在任一情況下，會附加 null 字元 ('\0')。  
  
 [Carchive:: Read](#read)時也可以使用文字模式的輸入，但它不會終止歸位字元復位換行組。  
  
### <a name="example"></a>範例  
  請參閱範例[CArchive::WriteString](#writestring)。  
  
##  <a name="a-nameserializeclassa--carchiveserializeclass"></a><a name="serializeclass"></a>CArchive::SerializeClass  
 當您想要儲存並載入基底類別的版本資訊，請呼叫此成員函式。  
  
```  
void SerializeClass(const CRuntimeClass* pClassRef);
```  
  
### <a name="parameters"></a>參數  
 `pClassRef`  
 基底類別的執行階段類別物件的指標。  
  
### <a name="remarks"></a>備註  
 `SerializeClass`讀取或寫入至類別，以參考`CArchive`物件，視方向而定`CArchive`。 使用`SerializeClass`取代[ReadClass](#readclass)和[WriteClass](#writeclass)做的便利方式來序列化基底類別物件。`SerializeClass`需要較少的程式碼和較少的參數。  
  
 像`ReadClass`，`SerializeClass`確認封存的類別資訊是與執行階段類別。 如果不相容，`SerializeClass`將會擲回[CArchiveException](../../mfc/reference/carchiveexception-class.md)。  
  
 必須使用執行階段類別[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)，否則`SerializeClass`將會擲回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 使用[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)巨集，以擷取其值`pRuntimeClass`參數。 基底類別必須有使用[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)巨集。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization #&25;](../../mfc/codesnippet/cpp/carchive-class_17.h)]  
  
##  <a name="a-namesetloadparamsa--carchivesetloadparams"></a><a name="setloadparams"></a>CArchive::SetLoadParams  
 呼叫`SetLoadParams`當您要讀取大量的`CObject`-從封存衍生物件。  
  
```  
void SetLoadParams(UINT nGrowBy = 1024);
```  
  
### <a name="parameters"></a>參數  
 `nGrowBy`  
 配置大小增加時所需的項目位置的最小數目。  
  
### <a name="remarks"></a>備註  
 `CArchive`使用負載陣列來解析參考儲存在封存中的物件。 `SetLoadParams`可讓您設定的負載陣列成長的大小。  
  
 您不呼叫`SetLoadParams`載入任何物件之後，或之後[MapObject](#mapobject)或[ReadObject](#readobject)呼叫。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization #&26;](../../mfc/codesnippet/cpp/carchive-class_18.h)]  
  
##  <a name="a-namesetobjectschemaa--carchivesetobjectschema"></a><a name="setobjectschema"></a>CArchive::SetObjectSchema  
 呼叫此成員函式設定儲存在保存物件的物件結構描述`nSchema`。  
  
```  
void SetObjectSchema(UINT nSchema);
```  
  
### <a name="parameters"></a>參數  
 `nSchema`  
 指定物件的結構描述。  
  
### <a name="remarks"></a>備註  
 下次呼叫[GetObjectSchema](#getobjectschema)會傳回值儲存在`nSchema`。  
  
 使用`SetObjectSchema`進行進階的版本控制; 例如，當您想要強制中讀取的特定版本`Serialize`衍生類別的函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization #&27;](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]  
  
##  <a name="a-namesetstoreparamsa--carchivesetstoreparams"></a><a name="setstoreparams"></a>CArchive::SetStoreParams  
 使用`SetStoreParams`時儲存大量的`CObject`-衍生封存檔中的物件。  
  
```  
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```  
  
### <a name="parameters"></a>參數  
 *nHashSize*  
 將對應的介面指標的雜湊資料表大小。 應該是質數。  
  
 `nBlockSize`  
 指定的記憶體配置資料粒度來擴充參數。 應該是 2 的為了達到最佳效能的乘冪。  
  
### <a name="remarks"></a>備註  
 `SetStoreParams`可讓您設定的雜湊資料表大小和用來識別唯一的物件在序列化程序對應的區塊大小。  
  
 您不呼叫`SetStoreParams`儲存任何物件之後，或之後[MapObject](#mapobject)或[WriteObject](#writeobject)呼叫。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization #&26;](../../mfc/codesnippet/cpp/carchive-class_18.h)]  
  
##  <a name="a-namewritea--carchivewrite"></a><a name="write"></a>Carchive:: Write  
 指定的位元組數目寫入封存。  
  
```  
void Write(const void* lpBuf, INT nMax);
```  
  
### <a name="parameters"></a>參數  
 `lpBuf`  
 使用者提供的緩衝區，其中包含要寫入至封存的資料指標。  
  
 `nMax`  
 整數，指定要寫入至封存的位元組數目。  
  
### <a name="remarks"></a>備註  
 封存不會格式化位元組。  
  
 您可以使用**撰寫**成員函式內您`Serialize`函式撰寫一般結構包含在您的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization #&23;](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]  
  
##  <a name="a-namewriteclassa--carchivewriteclass"></a><a name="writeclass"></a>CArchive::WriteClass  
 使用`WriteClass`來儲存在衍生類別的序列化期間的基底類別版本和類別資訊。  
  
```  
void WriteClass(const CRuntimeClass* pClassRef);
```  
  
### <a name="parameters"></a>參數  
 `pClassRef`  
 指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)對應到要求的類別參考的結構。  
  
### <a name="remarks"></a>備註  
 `WriteClass`寫入至參考[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)基底類別的`CArchive`。 使用[CArchive::ReadClass](#readclass)擷取參考。  
  
 `WriteClass`確認已封存的類別資訊適用於執行階段類別。 如果不相容，`WriteClass`將會擲回[CArchiveException](../../mfc/reference/carchiveexception-class.md)。  
  
 必須使用執行階段類別[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)，否則`WriteClass`將會擲回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 您可以使用[SerializeClass](#serializeclass)而不是`WriteClass`，以處理讀取和寫入的類別參考。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization #&28;](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]  
  
##  <a name="a-namewriteobjecta--carchivewriteobject"></a><a name="writeobject"></a>CArchive::WriteObject  
 儲存指定`CObject`封存。  
  
```  
void WriteObject(const CObject* pOb);
```  
  
### <a name="parameters"></a>參數  
 `pOb`  
 所儲存之物件的常數指標。  
  
### <a name="remarks"></a>備註  
 此函式通常會呼叫`CArchive`插入 ( ** << **) 運算子多載的`CObject`。 **WriteObject**，轉而呼叫`Serialize`封存類別函式。  
  
 您必須使用`IMPLEMENT_SERIAL`巨集，以啟用封存。 **WriteObject**寫入封存 ASCII 類別名稱。 這個類別名稱會在載入過程中稍後進行驗證。 特殊的編碼配置可避免不必要的重複多個物件之類別的類別名稱。 此配置也可避免多餘的儲存體做為目標的多個指標的物件。  
  
 編碼方式 （包括 ASCII 類別名稱的目前狀態） 的物件是實作細節，並無法變更在未來版本的程式庫。  
  
> [!NOTE]
>  建立、 刪除和更新您的物件開始封存檔案之前完成。 如果您混用封存物件修改，將會損毀您的封存。  
  
### <a name="example"></a>範例  
 如需類別的定義`CAge`，請參閱範例[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)。  
  
 [!code-cpp[NVC_MFCSerialization #&29;](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]  
  
##  <a name="a-namewritestringa--carchivewritestring"></a><a name="writestring"></a>CArchive::WriteString  
 使用此成員函式將資料從緩衝區寫入相關聯的檔案`CArchive`物件。  
  
```  
void WriteString(LPCTSTR lpsz);
```  
  
### <a name="parameters"></a>參數  
 `lpsz`  
 指定包含 null 結尾的文字字串之緩衝區的指標。  
  
### <a name="remarks"></a>備註  
 結束的 null 字元 ('\0') 不會寫入檔案。也新行字元會自動寫入。  
  
 `WriteString`回應數個條件，包括磁碟已滿狀況會擲回例外狀況。  
  
 **撰寫**也可供使用，但它可以而不是終止 null 字元，請將要求的位元組數目來寫入檔案。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSerialization #&30;](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFile 類別](../../mfc/reference/cfile-class.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [CSocket 類別](../../mfc/reference/csocket-class.md)   
 [CSocketFile 類別](../../mfc/reference/csocketfile-class.md)

