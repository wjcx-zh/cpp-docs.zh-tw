---
title: 資料來源：決定資料來源的結構描述 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
ms.openlocfilehash: 60ed77ec8870ba80832d4f8c73a8362062dc9c2a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213313"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>資料來源：決定資料來源的結構描述 (ODBC)

本主題適用於 MFC ODBC 類別。

若要在 `CRecordset` 物件中設定資料成員，您必須知道所連接之資料來源的架構。 判斷資料來源的架構牽涉到取得資料來源中的資料表清單、每個資料表中的資料行清單、每個資料行的資料類型，以及任何索引是否存在。

## <a name="see-also"></a>另請參閱

[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[資料來源：管理連接 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)
