---
title: OLE DB 程式設計概觀 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fdeca20ad97a09f9d5862fa43be680a2f907405f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ole-db-programming-overview"></a>OLE DB 程式設計概觀
OLE DB 是一種高效能、 以 COM 為基礎的資料庫技術。 它提供存取資料，不論它會儲存的表單的常見方式。 在一般商務的情況下，大量的資訊會儲存在公司資料庫外部。 循序編製索引的檔案、 個人資料庫 （例如存取）、 試算表 （例如 Excel)、 專案計劃應用程式 （例如專案） 和 （例如 Outlook) 的電子郵件 （例如 FAT 或 NTFS） 的檔案系統中找到這項資訊。 OLE DB 可讓您以相同的方式，存取任何種類的資料存放區，只要資料存放區有 OLE DB 提供者。
  
 OLE DB 可讓您開發應用程式存取不同資料來源，無論或不是 DBMS。 OLE DB 通用存取可讓使用適當的 DBMS 功能支援給定的資料來源的 COM 介面。 COM 可減少不必要的重複的服務，並不只在資料來源之間也在其他應用程式之間的互通性最大化。  
  
## <a name="benefits-of-com"></a>COM 的優點  
 這是 COM 的運作方式。 OLE DB 是一組 COM 介面。 透過一組一致的介面中存取資料，您可以將資料庫組織成合作元件的矩陣。  
  
 COM 規格為基礎，OLE DB 定義的可延伸和可維護的集合的因素，並將封裝的 DBMS 功能一致、 可重複使用部分的介面。 這些介面會定義 DBMS 元件，例如資料列的容器，查詢處理器和交易協調器，啟用各種資訊來源的統一交易式存取的界限。  
 
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 程式設計](../../data/oledb/ole-db-programming.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 範本](../../data/oledb/ole-db-templates.md)