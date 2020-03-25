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
ms.openlocfilehash: 0eac4f47c3d00c34c1aadaef18202a95f831ad82
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209089"
---
# <a name="schema--mfc-data-access"></a>結構描述 (MFC 資料存取)

資料庫結構描述說明資料庫中的資料表和資料庫檢視的目前結構。 一般情況下，精靈產生的程式碼會假設資料錄集所存取的資料表之結構描述將不會變更，但是資料庫類別可以處理某些結構描述變更，例如加入、重新排列或刪除未繫結的資料行。 如果某個資料表變更，您就必須以手動方式更新該資料表的資料錄集，然後重新編譯應用程式。

您也可以補充精靈產生的程式碼，以處理在編譯時期完全不知道其結構描述的資料庫。 如需詳細資訊，請參閱[記錄集：動態地系結資料行（ODBC）](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

## <a name="see-also"></a>另請參閱

[資料存取程式設計 (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[SQL](../data/odbc/sql.md)<br/>
[資料錄集 (ODBC)](../data/odbc/recordset-odbc.md)
