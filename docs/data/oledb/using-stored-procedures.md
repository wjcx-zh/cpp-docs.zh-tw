---
title: 使用預存程序
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
ms.openlocfilehash: 436c796b24b0fa498f2b3f45e848392635b22a34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376033"
---
# <a name="using-stored-procedures"></a>使用預存程序

預存程序是一種儲存在資料庫中的可執行物件。 調用儲存過程類似於調用 SQL 命令。 在數據源上使用儲存過程(而不是在用戶端應用程式中執行或準備語句)可以提供幾個優點,包括更高的性能、減少網路開銷以及提高一致性和準確性。

存儲過程可以具有任意數量的(包括零)輸入或輸出參數,並可以傳遞返回值。 可以將硬代碼參數值作為特定資料值,也可以使用參數標記(問號"?"

> [!NOTE]
> 使用 Visual C++創建的 CLR SQL`/clr:safe`Server 儲存過程 必須使用編譯器選項進行編譯。

SQL Server (SQLOLEDB) 的 OLE DB 提供程式支援儲存程序用於傳回資料的以下機制:

- 過程中的每個**SELECT**語句都會生成結果集。

- 程序可以透過輸出參數傳回資料。

- 程序可以有一個整數的傳回碼。

> [!NOTE]
> 不能將存儲過程與 Jet 的 OLE DB 提供程式一起使用,因為該提供程式不支援存儲過程;因此,該提供程式不支援"處理程式"。"這些過程"查詢字串中只允許常量。

## <a name="see-also"></a>另請參閱

[使用 OLE DB 使用者樣本](../../data/oledb/working-with-ole-db-consumer-templates.md)
