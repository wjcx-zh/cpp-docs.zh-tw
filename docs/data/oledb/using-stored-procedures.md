---
title: 使用預存程序 |Microsoft Docs
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
ms.openlocfilehash: fe62aff7e8828dcb17c04fc3e05eedc9eefe9d16
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337277"
---
# <a name="using-stored-procedures"></a>使用預存程序
預存程序是儲存在資料庫中的可執行物件。 呼叫預存程序是類似於叫用 SQL 命令。 在 資料來源 （而不是執行或準備用戶端應用程式中的陳述式） 上使用預存程序，可以提供幾項優點，包括較高的效能、 降低的網路負荷，以及改善的一致性和精確度。  
  
 預存程序可以有任意數目的 （包括零） 輸入或輸出參數，而且可以傳遞傳回值。 特定資料值，或使用參數標記，可以永久的程式碼參數值 (問號 '？ ')。  
  
> [!NOTE]
>  使用 Visual c + + 所建立的預存程序必須使用編譯的 CLR SQL Server`/clr:safe`編譯器選項。  
  
 OLE DB provider for SQL Server (SQLOLEDB) 支援下列預存程序用來傳回資料的機制：  
  
-   在程序中每個 SELECT 陳述式會產生結果集。  
  
-   此程序可以傳回透過輸出參數的資料。  
  
-   此程序可以有整數傳回碼。  
  
> [!NOTE]
>  您無法使用預存程序使用 OLE DB provider for Jet 因為該提供者不支援預存程序;只允許常數在查詢字串中。  
  
## <a name="see-also"></a>另請參閱  
 [使用 OLE DB 消費者範本](../../data/oledb/working-with-ole-db-consumer-templates.md)