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
ms.openlocfilehash: c456f4bf5891f550fcd9523fa376333d66e079a6
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509098"
---
# <a name="cdataconnection-class"></a>CDataConnection 類別

管理與資料來源的連接。

## <a name="syntax"></a>Syntax

```cpp
class CDataConnection
```

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|-|-|
|[CDataConnection](#cdataconnection)|建構函式。 具現化並初始化 `CDataConnection` 物件。|
|[複製](#copy)|建立現有資料連線的複本。|
|[開啟](#open)|使用初始化字串開啟與資料來源的連接。|
|[OpenNewSession](#opennewsession)|在目前的連接上開啟新的會話。|

### <a name="operators"></a>運算子

| 名稱 | 描述 |
|-|-|
|[運算子 BOOL](#op_bool)|判斷目前的會話是否為開啟。|
|[運算子 bool](#op_bool_ole)|判斷目前的會話是否為開啟。|
|[運算子 CDataSource&](#op_cdata_amp)|傳回包含物件的參考 `CDataSource` 。|
|[operator CDataSource *](#op_cdata_star)|將指標傳回至包含的 `CDataSource` 物件。|
|[運算子 CSession&](#op_csession_amp)|傳回包含物件的參考 `CSession` 。|
|[operator CSession*](#op_csession_star)|將指標傳回至包含的 `CSession` 物件。|

## <a name="remarks"></a>備註

`CDataConnection` 是用來建立用戶端的實用類別，因為它會封裝必要的物件 (資料來源和會話) ，以及連接到資料來源時所需執行的一些工作。

`CDataConnection`如果沒有，您就必須建立 `CDataSource` 物件、呼叫其[OpenFromInitializationString](./cdatasource-class.md#openfrominitializationstring)方法，然後建立[CSession](../../data/oledb/csession-class.md)物件的實例，呼叫其[Open](./csession-class.md#open)方法，然後建立[CCommand](../../data/oledb/ccommand-class.md)物件，並呼叫其 `Open` * 方法。

使用時 `CDataConnection` ，您只需要建立連線物件、將初始化字串傳遞給它，然後使用該連接來開啟命令。 如果您打算重複使用與資料庫的連接，最好讓連線保持開啟，並 `CDataConnection` 提供便利的方式來進行這項作業。

> [!NOTE]
> 如果您要建立需要處理多個會話的資料庫應用程式，您將需要使用 [OpenNewSession](#opennewsession)。

## <a name="cdataconnectioncdataconnection"></a><a name="cdataconnection"></a> CDataConnection：： CDataConnection

具現化並初始化 `CDataConnection` 物件。

### <a name="syntax"></a>語法

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>參數

*Ds*<br/>
在現有資料連線的參考。

### <a name="remarks"></a>備註

第一個覆寫會 `CDataConnection` 以預設設定建立新的物件。

第二個覆寫會建立新的 `CDataConnection` 物件，其設定等於您指定的資料連線物件。

## <a name="cdataconnectioncopy"></a><a name="copy"></a> CDataConnection：： Copy

建立現有資料連線的複本。

### <a name="syntax"></a>語法

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>參數

*Ds*<br/>
在要複製之現有資料連線的參考。

## <a name="cdataconnectionopen"></a><a name="open"></a> CDataConnection：： Open

使用初始化字串開啟與資料來源的連接。

### <a name="syntax"></a>語法

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>參數

*szInitString*<br/>
在資料來源的初始化字串。

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="cdataconnectionopennewsession"></a><a name="opennewsession"></a> CDataConnection：： OpenNewSession

使用目前的連線物件的資料來源，開啟新的會話。

### <a name="syntax"></a>語法

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>參數

*會話*<br/>
[in/out]新會話物件的參考。

### <a name="remarks"></a>備註

新的會話會使用目前連線物件的包含資料來源物件做為其父系，並且可以存取所有與資料來源相同的資訊。

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="cdataconnectionoperator-bool"></a><a name="op_bool"></a> CDataConnection：： operator BOOL

判斷目前的會話是否為開啟。

### <a name="syntax"></a>語法

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>備註

傳回 **BOOL** (MFC typedef) 值。 **TRUE** 表示目前的會話為開啟狀態; **FALSE** 表示目前的會話已關閉。

## <a name="cdataconnectionoperator-bool-ole-db"></a><a name="op_bool_ole"></a> CDataConnection：： operator bool (OLE DB) 

判斷目前的會話是否為開啟。

### <a name="syntax"></a>語法

```cpp
operator bool() throw();
```

### <a name="remarks"></a>備註

傳回 **`bool`** (c + + 資料類型) 值。 **`true`** 表示目前的會話已開啟; **`false`** 表示目前的會話已關閉。

## <a name="cdataconnectionoperator-cdatasourceamp"></a><a name="op_cdata_amp"></a> CDataConnection：： operator CDataSource&amp;

傳回包含物件的參考 `CDataSource` 。

### <a name="syntax"></a>語法

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>備註

這個運算子會傳回包含物件的參考 `CDataSource` ，讓您傳遞 `CDataConnection` `CDataSource` 需要參考的物件。

### <a name="example"></a>範例

如果您的函式 (如下所示 `func`) 接受 `CDataSource` 參考，則可以改用 `CDataSource&` 來傳遞 `CDataConnection` 物件。

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="cdataconnectionoperator-cdatasource"></a><a name="op_cdata_star"></a> CDataConnection：： operator CDataSource *

將指標傳回至包含的 `CDataSource` 物件。

### <a name="syntax"></a>語法

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>備註

這個運算子會將指標傳回至包含的 `CDataSource` 物件，讓您傳遞需要 `CDataConnection` 指標的 `CDataSource` 物件。

如需使用方式範例，請參閱 [運算子 CDataSource&](#op_cdata_amp) 。

## <a name="cdataconnectionoperator-csessionamp"></a><a name="op_csession_amp"></a> CDataConnection：： operator CSession&amp;

傳回包含物件的參考 `CSession` 。

### <a name="syntax"></a>語法

```cpp
operator const CSession&();
```

### <a name="remarks"></a>備註

這個運算子會傳回包含物件的參考 `CSession` ，讓您傳遞 `CDataConnection` `CSession` 需要參考的物件。

### <a name="example"></a>範例

如果您的函式 (如下所示 `func`) 接受 `CSession` 參考，則可以改用 `CSession&` 來傳遞 `CDataConnection` 物件。

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="cdataconnectionoperator-csession"></a><a name="op_csession_star"></a> CDataConnection：： operator CSession *

將指標傳回至包含的 `CSession` 物件。

### <a name="syntax"></a>語法

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>備註

這個運算子會將指標傳回至包含的 `CSession` 物件，讓您傳遞需要 `CDataConnection` 指標的 `CSession` 物件。

### <a name="example"></a>範例

如需使用方式範例，請參閱 [運算子 CSession&](#op_csession_amp) 。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
