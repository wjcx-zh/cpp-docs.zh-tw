---
title: 存取 ODBC 和 SQL |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- API calls [C++], calling DAO or ODBC directly
- Windows API [C++], calling from MFC
- ODBC API functions [C++]
- ODBC API functions [C++], calling from MFC
- SQL [C++], calling ODBC API functions
- ODBC [C++], API functions
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4635d482a08c486c1cf3259ae642fd82eb4bae82
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055940"
---
# <a name="access-to-odbc-and-sql"></a>存取 ODBC 和 SQL

Microsoft Foundation Class Library 封裝許多 Windows API 呼叫，並仍可讓您直接呼叫任何的 Windows API 函式。 資料庫類別會提供關於 ODBC API 相同的彈性。 雖然資料庫類別避免從 ODBC 的複雜問題，您可以直接從任何地方呼叫 ODBC API 函式在程式中。

同樣地，資料庫類別免除您不必太多其他作業[SQL](../../data/odbc/sql.md)，但是您可以使用 SQL 直接如果您想要。 您可以自訂資料錄集物件，藉由傳遞自訂的 SQL 陳述式 （或設定預設的陳述式的一部分） 當您開啟資料錄集。 您也可以直接使用的 SQL 呼叫[ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)類別成員函式[CDatabase](../../mfc/reference/cdatabase-class.md)。

如需詳細資訊，請參閱 < [ODBC： 直接呼叫 ODBC API 函式](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)並[SQL： 製作直接 SQL 呼叫 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)。

## <a name="see-also"></a>另請參閱

[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)