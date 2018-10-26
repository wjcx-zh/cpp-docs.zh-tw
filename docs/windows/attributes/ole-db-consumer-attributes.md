---
title: OLE DB 消費者屬性 (c + + COM) |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], database
- attributes [C++/CLI], data access
- databases [C++], attributes
- OLE DB consumers [C++], attributes
- database attributes [C++/CLI]
- attributes [C++/CLI], OLE DB consumer
ms.assetid: 017b591f-8f9a-42b4-84d5-cc42a21ab0cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19c3e441ff4130d30f3aeb7957c5af85576fb9e1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065859"
---
# <a name="ole-db-consumer-attributes"></a>OLE DB 消費者屬性
OLE DB 消費者屬性插入程式碼，根據[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-reference.md)，以建立使用 OLE DB 取用者會執行工作，例如開啟資料表，執行命令，以及存取資料。

|屬性|描述|
|---------------|-----------------|
|[db_accessor](db-accessor.md)|繫結的資料列集資料行，並將它們繫結至對應的存取子對應。|
|[db_column](db-column.md)|將指定的資料行的資料列集繫結。|
|[db_command](db-command.md)|執行 OLE DB 命令。|
|[db_param](db-param.md)|關聯的輸入或輸出參數中指定的成員變數。|
|[db_source](db-source.md)|建立並封裝的連接，透過提供者，資料來源。|
|[db_table](db-table.md)|開啟 OLE DB 資料表。|

## <a name="see-also"></a>另請參閱

[依群組分類的屬性](attributes-by-group.md)