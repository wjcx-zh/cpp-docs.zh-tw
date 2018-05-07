---
title: 使用預存程序 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e5b49daa44fc8c88316134915945ad7ee01bb81a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-stored-procedures"></a>使用預存程序
預存程序是儲存在資料庫中的可執行物件。 呼叫預存程序是類似於叫用 SQL 命令。 可以使用預存程序 （而不是執行或準備用戶端應用程式中的陳述式） 的資料來源上提供幾項優點，包括較高的效能、 降低的網路負荷，並改善的一致性和精確度。  
  
 預存程序可以有任意數目的 （包括零） 輸入或輸出參數，也可以傳遞傳回值。 您可以在特定資料值，或使用參數標記的參數值可能是硬 (問號 '？ ')。  
  
> [!NOTE]
>  使用 Visual c + + 所建立的預存程序必須使用編譯的 CLR SQL Server **/clr: safe**編譯器選項。  
  
 OLE DB provider for SQL Server (SQLOLEDB) 支援預存程序傳回的資料會使用下列機制：  
  
-   程序中的每個 SELECT 陳述式會產生結果集。  
  
-   此程序可以傳回輸出參數的資料。  
  
-   程序可以有整數傳回碼。  
  
> [!NOTE]
>  您無法使用預存程序與 OLE DB provider for Jet 因為該提供者不支援預存程序。只允許常數查詢字串中。  
  
## <a name="see-also"></a>另請參閱  
 [使用 OLE DB 消費者範本](../../data/oledb/working-with-ole-db-consumer-templates.md)