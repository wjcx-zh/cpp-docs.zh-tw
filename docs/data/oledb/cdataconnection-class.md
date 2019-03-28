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
ms.openlocfilehash: 769dfc99f431cb5ba803075e28176713f9bd7092
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565502"
---
# <a name="cdataconnection-class"></a>CDataConnection 類別

管理與資料來源的連線。

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
|[CDataConnection](#cdataconnection)|建構函式。 具現化並初始化`CDataConnection`物件。|
|[複製](#copy)|建立一份現有的資料連接。|
|[開啟](#open)|開啟使用初始化字串的資料來源的連接。|
|[OpenNewSession](#opennewsession)|開啟新的工作階段，在目前的連線。|

### <a name="operators"></a>運算子

|||
|-|-|
|[運算子 BOOL](#op_bool)|判斷目前的工作階段是否為開啟。|
|[operator bool](#op_bool_ole)|判斷目前的工作階段是否為開啟。|
|[CDataSource 運算子 （& s)](#op_cdata_amp)|傳回包含之的參考`CDataSource`物件。|
|[operator CDataSource*](#op_cdata_star)|將指標傳回至包含的 `CDataSource` 物件。|
|[運算子 Csession& （& s)](#op_csession_amp)|傳回包含之的參考`CSession`物件。|
|[運算子 CSession *](#op_csession_star)|將指標傳回至包含的 `CSession` 物件。|

## <a name="remarks"></a>備註

`CDataConnection` 是有用的類別，來建立用戶端，因為它會封裝所需的物件 （資料來源和工作階段） 和一些您需要連接到資料來源時所執行

不含`CDataConnection`，您必須建立`CDataSource`物件，請呼叫其[OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md)方法，然後建立的執行個體[CSession](../../data/oledb/csession-class.md)物件，請呼叫其[開啟](../../data/oledb/csession-open.md)方法，然後建立[CCommand](../../data/oledb/ccommand-class.md)物件，然後呼叫其`Open`* 方法。

使用`CDataConnection`，您只需要建立連線物件，將它傳遞初始字串，然後使用該連接開啟的命令。 如果您計劃重複使用資料庫的連接，它是個不錯的主意，若要讓連線保持開啟，並`CDataConnection`提供便利的方式，若要這麼做。

> [!NOTE]
>  如果您要建立的資料庫應用程式需要處理多個工作階段，您必須使用[OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)。

## <a name="cdataconnection"></a> Cdataconnection:: Cdataconnection

具現化並初始化`CDataConnection`物件。

### <a name="syntax"></a>語法

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>參數

*ds*<br/>
[in]對現有的資料連接的參考。

### <a name="remarks"></a>備註

建立新的第一個覆寫`CDataConnection`物件使用預設設定。

建立新的第二個覆寫`CDataConnection`設定相當於您所指定的資料連線物件的物件。

## <a name="copy"></a> CDataConnection::Copy

建立一份現有的資料連接。

### <a name="syntax"></a>語法

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>參數

*ds*<br/>
[in]若要複製現有的資料連接的參考。

## <a name="open"></a> Cdataconnection:: Open

開啟使用初始化字串的資料來源的連接。

### <a name="syntax"></a>語法

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>參數

*szInitString*<br/>
[in]資料來源初始化字串。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

## <a name="opennewsession"></a> CDataConnection::OpenNewSession

開啟新的工作階段會使用目前的連接物件的資料來源。

### <a name="syntax"></a>語法

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>參數

*session*<br/>
[輸入/輸出]新的工作階段物件的參考。

### <a name="remarks"></a>備註

新的工作階段為其父代，會使用目前的連接物件包含的資料來源物件，並可存取所有資料來源相同的資訊。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

## <a name="op_bool"></a> Cdataconnection:: Operator BOOL

判斷目前的工作階段是否為開啟。

### <a name="syntax"></a>語法

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>備註

傳回**BOOL** (MFC typedef) 值。 **TRUE**表示目前的工作階段已開啟;**FALSE**表示目前的工作階段已關閉。

## <a name="op_bool_ole"></a> Cdataconnection:: Operator bool (OLE DB)

判斷目前的工作階段是否為開啟。

### <a name="syntax"></a>語法

```cpp
operator bool() throw();
```

### <a name="remarks"></a>備註

傳回**bool** （c + + 資料類型） 值。 **true**表示目前的工作階段已開啟;**false**表示目前的工作階段已關閉。

## <a name="op_cdata_amp"></a> Cdataconnection:: Operator CDataSource&amp;

傳回包含之的參考`CDataSource`物件。

### <a name="syntax"></a>語法

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>備註

這個運算子會傳回至包含參照`CDataSource`物件，可讓您傳遞`CDataConnection`物件，`CDataSource`預期參考。

### <a name="example"></a>範例

如果您有一個函式 (例如`func`下方) 採用`CDataSource`參考，您可以使用`CDataSource&`傳遞`CDataConnection`物件。

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="op_cdata_star"></a> Cdataconnection:: Operator CDataSource *

將指標傳回至包含的 `CDataSource` 物件。

### <a name="syntax"></a>語法

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>備註

這個運算子會將指標傳回至包含的 `CDataSource` 物件，讓您傳遞需要 `CDataConnection` 指標的 `CDataSource` 物件。

請參閱[運算子 CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)如需使用範例。

## <a name="op_csession_amp"></a> Cdataconnection:: Operator CSession&amp;

傳回包含之的參考`CSession`物件。

### <a name="syntax"></a>語法

```cpp
operator const CSession&();
```

### <a name="remarks"></a>備註

這個運算子會傳回至包含參照`CSession`物件，可讓您傳遞`CDataConnection`物件，`CSession`預期參考。

### <a name="example"></a>範例

如果您有一個函式 (例如`func`下方) 採用`CSession`參考，您可以使用`CSession&`傳遞`CDataConnection`物件。

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="op_csession_star"></a> CDataConnection::operator CSession*

將指標傳回至包含的 `CSession` 物件。

### <a name="syntax"></a>語法

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>備註

這個運算子會將指標傳回至包含的 `CSession` 物件，讓您傳遞需要 `CDataConnection` 指標的 `CSession` 物件。

### <a name="example"></a>範例

請參閱[運算子 Csession& &](../../data/oledb/cdataconnection-operator-csession-amp.md)如需使用範例。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)