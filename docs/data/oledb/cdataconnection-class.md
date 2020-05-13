---
title: CDataConnection 類別
ms.date: 03/27/2019
f1_keywords:
- ATL::CDataConnection
- ATL.CDataConnection
- CDataConnection
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
- CDataConnection.Copy
- ATL.CDataConnection.Copy
- ATL::CDataConnection::Copy
- CDataConnection::Copy
- CDataConnection.Open
- ATL.CDataConnection.Open
- CDataConnection::Open
- ATL::CDataConnection::Open
- CDataConnection.OpenNewSession
- ATL.CDataConnection.OpenNewSession
- ATL::CDataConnection::OpenNewSession
- OpenNewSession
- CDataConnection::OpenNewSession
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
- CDataSource&
- CDataConnection.operatorCDataSource&
- operatorCDataSource&
- CDataConnection::operatorCDataSource&
- CDataSource*
- CDataConnection::operatorCDataSource*
- CDataConnection.operatorCDataSource*
- operatorCDataSource*
- CSession&
- CDataConnection::operatorCSession&
- CDataConnection.operatorCSession&
- operatorCSession&
- CDataConnection.operatorCSession*
- CDataConnection::operatorCSession*
- operatorCSession*
- CSession*
helpviewer_keywords:
- CDataConnection class
- CDataConnection class, constructor
- Copy method
- Open method
- OpenNewSession method
- BOOL operator
- operator bool
- BOOL operator
- operator bool
- CDataSource& operator
- operator & (CDataSource)
- CDataSource* operator
- operator * (CDataSource)
- operator CSession&
- CSession& operator
- operator CSession*
- CSession* operator
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
ms.openlocfilehash: fe954e218a099fa7956748904a4baa89f741c52f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368608"
---
# <a name="cdataconnection-class"></a>CDataConnection 類別

管理與數據源的連接。

## <a name="syntax"></a>語法

```cpp
class CDataConnection
```

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[CData 連線](#cdataconnection)|建構函式。 實例化和初始化`CDataConnection`物件。|
|[複製](#copy)|建立現有資料連接的複本。|
|[開啟](#open)|使用初始化字串打開與數據源的連接。|
|[開啟新工作階段](#opennewsession)|在當前連接上打開新作業階段。|

### <a name="operators"></a>操作員

|||
|-|-|
|[運營商 BOOL](#op_bool)|確定當前會話是否打開。|
|[運算子布爾](#op_bool_ole)|確定當前會話是否打開。|
|[運算子 CDataSource&](#op_cdata_amp)|返回對包含`CDataSource`物件的引用。|
|[運算子 CDataSource*](#op_cdata_star)|將指標傳回至包含的 `CDataSource` 物件。|
|[運算子 CSession&](#op_csession_amp)|返回對包含`CSession`物件的引用。|
|[operator CSession*](#op_csession_star)|將指標傳回至包含的 `CSession` 物件。|

## <a name="remarks"></a>備註

`CDataConnection`是建立用戶端的有用類,因為它封裝了必要的物件(資料源和會話)以及連接到資料來源時需要執行的一些工作

如果沒有`CDataConnection``CDataSource`,您必須創建物件,呼叫其[OpenFrom 初始化String](../../data/oledb/cdatasource-openfrominitializationstring.md)方法,然後創建[CSession](../../data/oledb/csession-class.md)物件的實例,呼叫其[Open](../../data/oledb/csession-open.md)方法`Open`,然後創建[CCommand](../../data/oledb/ccommand-class.md)物件 並呼叫其 * 方法。

使用`CDataConnection`時,您只需建立連接物件,傳遞初始化字串,然後使用該連接打開命令。 如果您計劃重複使用與資料庫的連接,最好保持連接打開狀態,並提供`CDataConnection`一種方便的方法。

> [!NOTE]
> 如果要建立需要處理多個工作階段的資料庫應用程式,則需要使用[OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)。

## <a name="cdataconnectioncdataconnection"></a><a name="cdataconnection"></a>CData連線::CData連線

實例化和初始化`CDataConnection`物件。

### <a name="syntax"></a>語法

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>參數

*Ds*<br/>
[在]對現有數據連接的引用。

### <a name="remarks"></a>備註

第一個覆蓋將創建`CDataConnection`具有預設設置的新物件。

第二個重寫將創建`CDataConnection`一個新物件,其設置與指定的數據連接物件等效。

## <a name="cdataconnectioncopy"></a><a name="copy"></a>CData連線:: 複製

建立現有資料連接的複本。

### <a name="syntax"></a>語法

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>參數

*Ds*<br/>
[在]對現有要複製的數據連接的引用。

## <a name="cdataconnectionopen"></a><a name="open"></a>CData連線:開啟

使用初始化字串打開與數據源的連接。

### <a name="syntax"></a>語法

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>參數

*什因特斯特林*<br/>
[在]資料來源初始化字串。

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="cdataconnectionopennewsession"></a><a name="opennewsession"></a>CData連線::開啟新工作階段

使用當前連接物件的數據源打開新會話。

### <a name="syntax"></a>語法

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>參數

*工作階段*<br/>
[進出]對新會話物件的引用。

### <a name="remarks"></a>備註

新會話使用當前連接物件的包含數據源物件作為其父物件,並可以訪問與數據源相同的所有資訊。

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="cdataconnectionoperator-bool"></a><a name="op_bool"></a>CData連線::操作員BOOL

確定當前會話是否打開。

### <a name="syntax"></a>語法

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>備註

返回**BOOL** (MFC 類型def) 值。 **TRUE**表示當前會話處於打開狀態;**FALSE**表示當前會話已關閉。

## <a name="cdataconnectionoperator-bool-ole-db"></a><a name="op_bool_ole"></a>CData連線::操作員布爾(OLE DB)

確定當前會話是否打開。

### <a name="syntax"></a>語法

```cpp
operator bool() throw();
```

### <a name="remarks"></a>備註

返回**bool(C++** 資料類型)值。 **true**表示當前會話處於打開狀態;**false**表示當前會話已關閉。

## <a name="cdataconnectionoperator-cdatasourceamp"></a><a name="op_cdata_amp"></a>CData連接::運營商CDataSource&amp;

返回對包含`CDataSource`物件的引用。

### <a name="syntax"></a>語法

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>備註

此運算元傳回對包含`CDataSource`物件的引用,允許您傳遞`CDataConnection``CDataSource`預期引用的物件。

### <a name="example"></a>範例

如果您有一個`func`函數(如下所示),可以`CDataSource`引用引用,則可以`CDataSource&`使用`CDataConnection`傳遞 物件。

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="cdataconnectionoperator-cdatasource"></a><a name="op_cdata_star"></a>CData連接::操作員 CDataSource*

將指標傳回至包含的 `CDataSource` 物件。

### <a name="syntax"></a>語法

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>備註

這個運算子會將指標傳回至包含的 `CDataSource` 物件，讓您傳遞需要 `CDataConnection` 指標的 `CDataSource` 物件。

有關使用範例,請參閱[運算符 CDataSource&。](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)

## <a name="cdataconnectionoperator-csessionamp"></a><a name="op_csession_amp"></a>CData連接::操作員工作階段&amp;

返回對包含`CSession`物件的引用。

### <a name="syntax"></a>語法

```cpp
operator const CSession&();
```

### <a name="remarks"></a>備註

此運算元傳回對包含`CSession`物件的引用,允許您傳遞`CDataConnection``CSession`預期引用的物件。

### <a name="example"></a>範例

如果您有一個`func`函數(如下所示),可以`CSession`引用引用,則可以`CSession&`使用`CDataConnection`傳遞 物件。

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="cdataconnectionoperator-csession"></a><a name="op_csession_star"></a>CData連接::操作員會話*

將指標傳回至包含的 `CSession` 物件。

### <a name="syntax"></a>語法

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>備註

這個運算子會將指標傳回至包含的 `CSession` 物件，讓您傳遞需要 `CDataConnection` 指標的 `CSession` 物件。

### <a name="example"></a>範例

有關使用範例,請參閱[運算符 CSession&。](../../data/oledb/cdataconnection-operator-csession-amp.md)

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
