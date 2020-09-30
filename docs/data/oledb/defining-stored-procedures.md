---
title: 定義預存程序
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
ms.openlocfilehash: 47f68bcf5c62aa54cc5ee60de166e1085f5a3fc5
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500933"
---
# <a name="defining-stored-procedures"></a>定義預存程序

在呼叫預存程式之前，您必須先使用 [DEFINE_COMMAND](./macros-and-global-functions-for-ole-db-consumer-templates.md#define_command) 宏來定義它。 當您定義命令時，請以問號 (？ ) 作為參數標記來表示參數：

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{INSERT {name, phone} INTO shippers (?,?)}"))
```

使用大括弧的語法 (，因此本主題的程式碼範例中所使用的) 是 SQL Server 特有的。 您在預存程式中使用的語法可能會根據您所使用的提供者而有所不同。

接下來，在參數對應中，指定您在命令中使用的參數，並依命令出現順序列出參數：

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param
END_PARAM_MAP()
```

先前的範例會定義預存程式。 通常，為了有效率地重複使用程式碼，資料庫會包含一組預先定義的預存程式，其名稱如 `Sales by Year` 或 `dt_adduserobject` 。 您可以使用 SQL Server Enterprise Manager 來查看其定義。 您可以依照下列方式呼叫它們 (的位置 *？* 參數取決於預存程式的介面) ：

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }"))
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }"))
```

接下來，宣告命令類別：

```cpp
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>
```

最後，呼叫中的預存程式，如下所示 `OpenRowset` ：

```cpp
CSession m_session;

HRESULT OpenRowset()
{
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);
}
```

另請注意，您可以使用資料庫屬性 [db_command](../../windows/attributes/db-command.md) 定義預存程式，如下所示：

```cpp
db_command("{ ? = CALL dbo.dt_adduserobject }")
```

## <a name="see-also"></a>另請參閱

[使用預存程式](../../data/oledb/using-stored-procedures.md)
