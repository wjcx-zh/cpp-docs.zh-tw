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
ms.openlocfilehash: 2c0c1c71103384439d0b7b94f942e1b5a6d9e651
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536148"
---
# <a name="using-stored-procedures"></a>使用預存程序

預存程序是儲存在資料庫中的可執行物件。 呼叫預存程序是類似於叫用 SQL 命令。 在 資料來源 （而不是執行或準備用戶端應用程式中的陳述式） 上使用預存程序，可以提供幾項優點，包括較高的效能、 降低的網路負荷，以及改善的一致性和精確度。

預存程序可以有任意數目的 （包括零） 輸入或輸出參數，而且可以傳遞傳回值。 特定資料值，或使用參數標記，可以永久的程式碼參數值 (問號 '？ ')。

> [!NOTE]
>  使用 Visual c + + 所建立的預存程序必須使用編譯的 CLR SQL Server`/clr:safe`編譯器選項。

OLE DB provider for SQL Server (SQLOLEDB) 支援下列預存程序用來傳回資料的機制：

- 每隔**選取**程序中的陳述式會產生結果集。

- 此程序可以傳回透過輸出參數的資料。

- 此程序可以有整數傳回碼。

> [!NOTE]
> 您無法使用預存程序使用 OLE DB provider for Jet 因為該提供者不支援預存程序;只允許常數在查詢字串中。

## <a name="see-also"></a>另請參閱

[使用 OLE DB 消費者範本](../../data/oledb/working-with-ole-db-consumer-templates.md)