---
title: 結構描述 (MFC 資料存取)
ms.date: 11/04/2016
helpviewer_keywords:
- structures [C++], database
- databases [C++], schema
- database schema [C++], about database schemas
- database schema [C++]
- schemas [C++], database
- structures [C++]
ms.assetid: 7d17e35f-1ccf-4853-b915-5b8c7a45b9ee
ms.openlocfilehash: cc333ee987ed0c6cba6cb11730d8f940e49d525d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039029"
---
# <a name="schema--mfc-data-access"></a>結構描述 (MFC 資料存取)

資料庫結構描述說明資料庫中的資料表和資料庫檢視的目前結構。 一般情況下，精靈產生的程式碼會假設資料錄集所存取的資料表之結構描述將不會變更，但是資料庫類別可以處理某些結構描述變更，例如加入、重新排列或刪除未繫結的資料行。 如果某個資料表變更，您就必須以手動方式更新該資料表的資料錄集，然後重新編譯應用程式。

您也可以補充精靈產生的程式碼，以處理在編譯時期完全不知道其結構描述的資料庫。 如需詳細資訊，請參閱[資料錄集：動態繫結資料行 (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

## <a name="see-also"></a>另請參閱

[Data Access Programming (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[SQL](../data/odbc/sql.md)<br/>
[資料錄集 (ODBC)](../data/odbc/recordset-odbc.md)