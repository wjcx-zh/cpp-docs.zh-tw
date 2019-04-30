---
title: 資料來源：判斷資料來源 (ODBC) 的結構描述
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
ms.openlocfilehash: c419a3ac2d870e6a85675492ee6c9b726427a0e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395972"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>資料來源：判斷資料來源 (ODBC) 的結構描述

本主題適用於 MFC ODBC 類別。

若要設定中的資料成員您`CRecordset`物件時，您需要知道您要連接的資料來源的結構描述。 判斷資料來源的結構描述，牽涉到取得的資料來源中的資料表清單，每個資料表中的資料行，每個資料行的資料類型的清單，以及任何存在的索引。

## <a name="see-also"></a>另請參閱

[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[資料來源：管理連線 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)