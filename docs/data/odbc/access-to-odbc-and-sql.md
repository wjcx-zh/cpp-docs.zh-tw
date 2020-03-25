---
title: 存取 ODBC 和 SQL
ms.date: 11/04/2016
helpviewer_keywords:
- API calls [C++], calling DAO or ODBC directly
- Windows API [C++], calling from MFC
- ODBC API functions [C++]
- ODBC API functions [C++], calling from MFC
- SQL [C++], calling ODBC API functions
- ODBC [C++], API functions
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
ms.openlocfilehash: 0b590ce9309cbbe95285001cc5befe70a1d1961f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213326"
---
# <a name="access-to-odbc-and-sql"></a>存取 ODBC 和 SQL

MFC 程式庫會封裝許多 Windows API 呼叫，但仍可讓您直接呼叫任何 Windows API 函式。 資料庫類別為您提供與 ODBC API 相同的彈性。 雖然資料庫類別會保護您免于 ODBC 的大部分複雜性，但您可以直接從程式中的任何位置呼叫 ODBC API 函式。

同樣地，資料庫類別會使您不需要使用[sql](../../data/odbc/sql.md)，但如果您想要的話，也可以直接使用 sql。 當您開啟記錄集時，您可以藉由傳遞自訂 SQL 語句（或設定 default 語句的部分）來自訂記錄集物件。 您也可以使用類別[CDatabase](../../mfc/reference/cdatabase-class.md)的[ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)成員函式，直接進行 SQL 呼叫。

如需詳細資訊，請參閱[odbc：直接呼叫 ODBC API](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)函式和[SQL：製作直接的 SQL 呼叫（ODBC）](../../data/odbc/sql-making-direct-sql-calls-odbc.md)。

## <a name="see-also"></a>另請參閱

[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)
