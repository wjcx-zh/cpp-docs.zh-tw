---
title: 資料來源： 決定資料來源 (ODBC) 的結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b5ba9789226e54c9607e85caaa5e8af3f157f02d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052633"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>資料來源：決定資料來源的結構描述 (ODBC)

本主題適用於 MFC ODBC 類別。

若要設定中的資料成員您`CRecordset`物件時，您需要知道您要連接的資料來源的結構描述。 判斷資料來源的結構描述，牽涉到取得的資料來源中的資料表清單，每個資料表中的資料行，每個資料行的資料類型的清單，以及任何存在的索引。

## <a name="see-also"></a>另請參閱

[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[資料來源：管理連接 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)