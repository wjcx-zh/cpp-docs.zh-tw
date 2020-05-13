---
title: db_command （c + + COM 屬性）
ms.date: 07/10/2018
f1_keywords:
- vc-attr.db_command
helpviewer_keywords:
- db_command attribute
ms.assetid: 714c3e15-85d7-408b-9a7c-88505c3e5d24
ms.openlocfilehash: 87043315def59bcd7cff706710d988cc0ed37876
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825426"
---
# <a name="db_command"></a>db_command

建立 OLE DB 命令。

## <a name="syntax"></a>語法

```cpp
[ db_command(command, name, source_name, hresult, bindings, bulk_fetch)
]
```

### <a name="parameters"></a>參數

*命令*<br/>
包含 OLE DB 命令文字的命令字串。 簡單範例如下︰

```cpp
[ db_command ( command = "Select * from Products" ) ]
```

*command* 語法如下：

> 系結參數區塊 1 \
> &nbsp;&nbsp;OLE DB 命令 \
> 系結參數區塊 2 \
> &nbsp;&nbsp;OLE DB 命令的接續 \
> 系結參數區塊 3 \
> ...

*「繫結參數區塊」* (binding parameter block) 定義如下︰

> **（\[ ** *bindtype* **]** *szVar1* szVar1 \[， *szVar2* szVar2 \[， *nVar3* nVar3 \[，...]]]**)**

其中：

- **(** 標示資料繫結區塊的開始。

- **\[***bindtype* **]** 是下列其中一個不區分大小寫的字串：

  - ** \[db_column]** 將每個成員變數系結至資料列集中的資料行。

  - ** \[bindto]**（與** \[db_column]** 相同）。

  - ** \[in]** 將成員變數系結為輸入參數。

  - ** \[out]** 將成員變數系結為輸出參數。

  - in、out] ** \[ **將成員變數系結為輸入/輸出參數。

- *szvarx 會*， *nVarX*會解析為目前範圍內的成員變數。

- **)** 標示資料繫結區塊的結束。

如果命令字串包含一或多個規範（例如\[in]、 \[out] 或\[in/out）， **db_command**會建立參數對應。

如果命令字串包含一或多個參數，例如\[db_column] 或\[bindto]， **db_command**會產生資料列集和存取子對應來服務這些系結的變數。 如需詳細資訊，請參閱 [db_accessor](db-accessor.md) 。

> [!NOTE]
> \[*bindtype*]在類別層級使用**db_command**時，語法和系*結參數無效*。

以下是繫結參數區塊的一些範例。 下列範例會將 `m_au_fname` 和 `m_au_lname` 資料成員分別繫結至 pubs 資料庫中 authors 資料表的 `au_fname` 和 `au_lname` 資料行：

```cpp
TCHAR m_au_fname[21];
TCHAR m_au_lname[41];
TCHAR m_state[3] = 'CA';

[db_command (command = "SELECT au_fname([bindto]m_au_fname), au_lname([bindto]m_au_lname) " \
   "FROM dbo.authors " \
   "WHERE state = ?([in]m_state)")
]
```

*name*<br/>
選擇性您用來處理資料列集的控制碼名稱。 如果您指定 *name*，則 **db_command** 會產生具有所指定 *name*的類別，以用來周遊資料列集或執行多個動作查詢。 如果您未指定 *name*，則不可能會將多個資料列的結果傳回給使用者。

*source_name*<br/>
選擇性已`CSession`套用`db_source`屬性之類別的變數或實例，此命令會在其上執行。 請參閱 [db_source](db-source.md)。

**db_command** 會確認用於 *source_name* 的變數有效，因此指定的變數應該在函式或全域範圍中。

*hresult*<br/>
選擇性識別將接收此資料庫命令之 HRESULT 的變數。 如果變數不存在，則屬性會自動予以插入。

*關係*<br/>
選擇性可讓您將系結參數與 OLE DB 命令隔開。

如果您指定系結的值， **db_command**將會剖析相關聯的*值，而且*不\[會剖析*bindtype*] 參數。 這種用法可讓您使用 OLE DB 提供者語法。 若要停用剖析，但不搭配`Bindings=""`系結參數，請指定。

如果您沒有指定系*結的值，* **db_command**將會剖析系結參數區塊，尋找 '**（**'，後面接著**\[** _bindtype_**]** 方括弧，後面接著一或多個先前宣告的 c + + 成員變數，後面接著 '**）**'。 產生的命令中會移除括弧之間的所有文字，並且會使用這些參數來建構此命令的資料行和參數繫結。

*bulk_fetch*<br/>
選擇性整數值，指定要提取的資料列數目。

預設值為 1，指定單一資料列擷取 (資料列集的類型會是 [CRowset](../../data/oledb/crowset-class.md))。

大於 1 的值指定大量資料列擷取。 大量資料列擷取指的是大量資料列集可以擷取多個資料列處理代碼 (資料列集的類型會是 [CBulkRowset](../../data/oledb/cbulkrowset-class.md) ，並且呼叫具有所指定數目的資料列的 `SetRows` )。

如果 *bulk_fetch* 小於 1，則 `SetRows` 會傳回零。

## <a name="remarks"></a>備註

**db_command** 會建立 OLE DB 消費者用來執行命令的 [CCommand](../../data/oledb/ccommand-class.md) 物件。

您可以搭配使用 **db_command** 與類別或函式範圍；主要差異在於 `CCommand` 物件的範圍。 使用函式範圍時，繫結這類資料會終止於函式結尾。 類別和函式範圍使用方式都牽涉到 OLE DB 取用`CCommand<>`者樣板類別，但函式和類別案例的範本引數不同。 在函式`Accessor`案例中，會對包含區域變數的進行系結，而類別使用方式會將衍生類別`CAccessor`推斷為引數。 當成類別屬性使用時， **db_command** 是與 **db_column**搭配運作。

**db_command** 可以用來執行不傳回結果集的命令。

當取用者屬性提供者將此屬性套用至類別時，編譯器會將類別重新\_命名為*YourClassName*存取子，其中*YourClassName*是您為類別提供的名稱，而編譯器也會建立名為*YourClassName*的類別， \_其衍生自*YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。

## <a name="example"></a>範例

此範例所定義的命令會從狀態資料行符合 'CA' 的表格中選取第一個和最後一個名稱。 **db_command** 會建立和讀取可呼叫精靈所產生的函式 (例如 [OpenAll and CloseAll](../../data/oledb/consumer-wizard-generated-methods.md)) 以及 `CRowset` 成員函式 (例如 [MoveNext](../../data/oledb/crowset-movenext.md)) 的資料列集。

請注意，此程式碼需要您提供連接至 pubs 資料庫的連接字串。 如需如何在開發環境中執行這項操作的詳細資訊，請參閱[如何：連接到資料庫和流覽現有的物件](/sql/ssdt/how-to-connect-to-a-database-and-browse-existing-objects)和[加入新的連接](/visualstudio/data-tools/add-new-connections)。

```cpp
// db_command.h
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

#pragma once

[  db_source(L"your connection string"), db_command(L" \
      SELECT au_lname, au_fname \
      FROM dbo.authors \
      WHERE state = 'CA'")  ]

struct CAuthors {
   // In order to fix several issues with some providers, the code below may bind
   // columns in a different order than reported by the provider

   DBSTATUS m_dwau_lnameStatus;
   DBSTATUS m_dwau_fnameStatus;
   DBLENGTH m_dwau_lnameLength;
   DBLENGTH m_dwau_fnameLength;

   [ db_column("au_lname", status="m_dwau_lnameStatus", length="m_dwau_lnameLength") ] TCHAR m_au_lname[41];
   [ db_column("au_fname", status="m_dwau_fnameStatus", length="m_dwau_fnameLength") ] TCHAR m_au_fname[21];

   [ db_param("7", paramtype="DBPARAMIO_INPUT") ] TCHAR m_state[3];

   void GetRowsetProperties(CDBPropSet* pPropSet) {
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   }
};
```

## <a name="example"></a>範例

```cpp
// db_command.cpp
// compile with: /c
#include "db_command.h"

int main(int argc, _TCHAR* argv[]) {
   HRESULT hr = CoInitialize(NULL);

   // Instantiate rowset
   CAuthors rs;

   // Open rowset and move to first row
   strcpy_s(rs.m_state, sizeof(rs.m_state), _T("CA"));
   hr = rs.OpenAll();
   hr = rs.MoveFirst();

   // Iterate through the rowset
   while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET ) {
      // Print out the column information for each row
      printf("First Name: %s, Last Name: %s\n", rs.m_au_fname, rs.m_au_lname);
      hr = rs.MoveNext();
   }

   rs.CloseAll();
   CoUninitialize();
}
```

## <a name="example"></a>範例

此範例會在資料來源類別 `db_source` 上使用 `CMySource`，並在命令類別 `db_command` 和 `CCommand1` 上使用 `CCommand2`。

```cpp
// db_command_2.cpp
// compile with: /c
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>
// class usage for both db_source and db_command

[  db_source(L"your connection string"), db_command(L" \
      SELECT au_lname, au_fname \
      FROM dbo.authors \
      WHERE state = 'CA'")  ]
struct CMySource {
   HRESULT OpenDataSource() {
      return S_OK;
   }
};

[db_command(command = "SELECT * FROM Products")]
class CCommand1 {};

[db_command(command = "SELECT FNAME, LNAME FROM Customers")]
class CCommand2 {};

int main() {
   CMySource s;
   HRESULT hr = s.OpenDataSource();
   if (SUCCEEDED(hr)) {
      CCommand1 c1;
      hr = c1.Open(s);

      CCommand2 c2;
      hr = c2.Open(s);
   }

   s.CloseDataSource();
}
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**class**、 **struct**、member、method、local|
|**可重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>請參閱

[OLE DB 取用者屬性](ole-db-consumer-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)
