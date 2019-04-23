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
ms.openlocfilehash: 9e589f00ec0512794d14accc6bb33c0e7adbd378
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59035409"
---
# <a name="recordset-performing-a-join-odbc"></a>資料錄集：執行聯結 (ODBC)

本主題適用於 MFC ODBC 類別。

## <a name="what-a-join-is"></a>什麼是聯結

聯結作業，常見的資料存取工作，可讓您從使用單一資料錄集物件的多個資料表的資料搭配使用。 聯結兩個或多個資料表產生的資料錄集可以包含的每個資料表，資料行，但會顯示為您的應用程式的單一資料表。 有時聯結會使用所有資料表，但有時 SQL 的所有資料行**選取**內聯結子句使用只有部分中的每個資料表的資料行。 資料庫類別支援唯讀的聯結，但不是能更新聯結。

若要選取包含資料行聯結資料表的記錄，您需要下列項目：

- 資料表清單，其中包含的所有聯結的資料表名稱。

- 資料行清單，其中包含所有參與的資料行的名稱。 具有相同名稱但來自不同資料表的資料行被限定資料表名稱。

- 篩選 (SQL**其中**子句)，指定在其聯結資料表的資料行。 此篩選會採用格式"Table1.KeyCol = Table2.KeyCol 」 及實際完成聯結。

您也可以納入方程式的資料行的多個配對，以 SQL 關鍵字加入每一組相同的方式加入兩個以上的資料表**AND**。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：宣告的類別，預先定義的查詢 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)<br/>
[資料錄集：宣告的類別 (ODBC) 的資料表](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[資料錄集：重新查詢資料錄集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)