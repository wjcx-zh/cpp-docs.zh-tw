---
title: 資料錄集：執行聯結 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- joins [C++], in recordsets
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- filters [C++], join conditions for recordsets
- ODBC recordsets [C++], joins
- recordsets [C++], joining tables
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
ms.openlocfilehash: 7e8d42f2b96911cd57aca7c132b53ed7c10162be
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212793"
---
# <a name="recordset-performing-a-join-odbc"></a>資料錄集：執行聯結 (ODBC)

本主題適用於 MFC ODBC 類別。

## <a name="what-a-join-is"></a>什麼是聯結

聯結作業是一種常見的資料存取工作，可讓您使用單一記錄集物件來處理來自多個資料表的資料。 聯結兩個或多個資料表會產生一個記錄集，其中包含每個資料表的資料行，但會顯示為應用程式的單一資料表。 有時聯結會使用所有資料表中的所有資料行，但有時聯結中的 SQL **SELECT**子句只會使用每個資料表中的部分資料行。 資料庫類別支援唯讀聯結，但無法更新加入。

若要選取包含聯結資料表中之資料行的記錄，您需要下列專案：

- 包含所有聯結資料表名稱的資料表清單。

- 包含所有參與資料行名稱的資料行清單。 具有相同名稱但來自不同資料表的資料行是以資料表名稱來限定。

- 篩選準則（SQL **WHERE**子句），指定資料表聯結所在的資料行。 此篩選器會採用 "Table1. KeyCol = Table2. KeyCol" 格式，並實際完成聯結。

您可以用相同的方式聯結兩個以上的資料表，方法是讓多對資料行相等，每個配對都會以 SQL 關鍵字**和**聯結。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：宣告預先定義查詢的類別 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)<br/>
[資料錄集：宣告資料表的類別 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[資料錄集：重新查詢資料錄集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)
