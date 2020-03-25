---
title: 定義預存程序
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
ms.openlocfilehash: 9bab086bf6982eae5779d3199cfd2ac2c8efe77f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211000"
---
# <a name="defining-stored-procedures"></a>定義預存程序

在呼叫預存程式之前，您必須先使用[DEFINE_COMMAND](../../data/oledb/define-command.md)宏來定義它。 當您定義命令時，請以問號（？）做為參數標記來表示參數：

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{INSERT {name, phone} INTO shippers (?,?)}"))
```

本主題的程式碼範例中使用的語法（使用大括弧等）是 SQL Server 特定的。 您在預存程式中使用的語法可能會根據您所使用的提供者而有所不同。

接下來，在參數對應中，指定您在命令中使用的參數，並依命令中出現的順序列出參數：

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param
END_PARAM_MAP()
```

先前的範例會定義預存程式。 通常，為了有效率地重複使用程式碼，資料庫會包含一組具有名稱的預先定義預存程式，例如 `Sales by Year` 或 `dt_adduserobject`。 您可以使用 SQL Server Enterprise Manager 來查看其定義。 您可以依照下列方式呼叫它們（的位置 *？* 參數取決於預存程式的介面）：

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }"))
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }"))
```

接下來，宣告命令類別：

```cpp
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>
```

最後，在 `OpenRowset` 中呼叫預存程式，如下所示：

```cpp
CSession m_session;

HRESULT OpenRowset()
{
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);
}
```

另請注意，您可以使用資料庫屬性來定義預存程式， [db_command](../../windows/db-command.md)如下所示：

```cpp
db_command("{ ? = CALL dbo.dt_adduserobject }")
```

## <a name="see-also"></a>另請參閱

[使用預存程序](../../data/oledb/using-stored-procedures.md)
