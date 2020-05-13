---
title: OLE DB 消費屬性 (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], database
- attributes [C++/CLI], data access
- databases [C++], attributes
- OLE DB consumers [C++], attributes
- database attributes [C++/CLI]
- attributes [C++/CLI], OLE DB consumer
ms.assetid: 017b591f-8f9a-42b4-84d5-cc42a21ab0cc
ms.openlocfilehash: a9147d80e87e23a754043a29eb3d15570e85aec0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377096"
---
# <a name="ole-db-consumer-attributes"></a>OLE DB 消費者屬性

OLE DB 使用者屬性基於[OLE DB 使用者範本](../../data/oledb/ole-db-consumer-templates-reference.md)注入代碼,以建立一個工作中的 OLE DB 消費者,執行諸如打開表、執行命令和存取資料等任務。

|屬性|描述|
|---------------|-----------------|
|[db_accessor](db-accessor.md)|在行集中綁定列,並將它們綁定到相應的訪問器映射。|
|[db_column](db-column.md)|將指定的列綁定到行集。|
|[db_command](db-command.md)|執行 OLE DB 命令。|
|[db_param](db-param.md)|將指定的成員變數與輸入或輸出參數關聯。|
|[db_source](db-source.md)|通過提供程式創建和封裝與數據源的連接。|
|[db_table](db-table.md)|打開 OLE 資料庫表。|

## <a name="see-also"></a>另請參閱

[依群組屬性](attributes-by-group.md)
