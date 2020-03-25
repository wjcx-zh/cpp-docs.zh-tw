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
ms.openlocfilehash: a7e97781d245e236c57942db15d61080d6418cfa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209270"
---
# <a name="using-stored-procedures"></a>使用預存程序

預存程序是一種儲存在資料庫中的可執行物件。 呼叫預存程式類似于叫用 SQL 命令。 在資料來源上使用預存程式（而不是在用戶端應用程式中執行或準備語句）可提供幾項優點，包括更高的效能、降低的網路額外負荷，以及改良的一致性和正確性。

預存程式可以有任意數目的（包括零）輸入或輸出參數，而且可以傳遞傳回值。 您可以將參數值硬式編碼為特定資料值，或使用參數標記（問號 '？ '）。

> [!NOTE]
>  CLR SQL Server 使用 Visual C++建立的預存程式必須使用 `/clr:safe` 編譯器選項來編譯。

SQL Server （SQLOLEDB）的 OLE DB 提供者支援下列預存程式用來傳回資料的機制：

- 程式中的每個**SELECT**語句都會產生結果集。

- 程序可以透過輸出參數傳回資料。

- 程序可以有一個整數的傳回碼。

> [!NOTE]
> 您無法使用預存程式搭配 OLE DB provider for Jet，因為該提供者不支援預存程式;查詢字串中只允許常數。

## <a name="see-also"></a>另請參閱

[使用 OLE DB 消費者範本](../../data/oledb/working-with-ole-db-consumer-templates.md)
