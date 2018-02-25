---
title: "OLE DB 架構設計問題 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2cfb6b8ff4941aff1271662c27dddd509b023c55
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ole-db-architectural-design-issues"></a>OLE DB 架構設計問題
啟動 OLE DB 應用程式之前，您應該考慮下列問題：  
  
 **您將使用何種程式設計實作來撰寫您的 OLE DB 應用程式？**  
 Microsoft 提供數個程式庫，以完成這項作業： OLE DB 樣板程式庫、 OLE DB 屬性和 OLE DB SDK 中的原始 OLE DB 介面。 此外，還有精靈可幫助您撰寫您的程式。 這些實作中所述[OLE DB 樣板、 屬性和其他實作](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md)。  
  
 **您需要撰寫您自己的提供者嗎？**  
 大部分的開發人員不需要撰寫自己的提供者。 Microsoft 提供數個提供者。 每當您建立資料連線 （例如，當您將加入您專案中使用 ATL OLE DB 消費者精靈的取用者），**資料連結屬性**對話方塊會列出所有可用的提供者註冊您的系統上。 如果其中一個提供者是適用於您自己的資料存放區和資料存取應用程式，最簡單的做法是使用下列其中一種。 不過，如果您的資料存放區不符合其中一個類別，您必須建立自己的提供者。 建立提供者的相關資訊，請參閱[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)。  
  
 **您需要使用您的消費者的支援層級？**  
 部分取用者可以是非常基本;當其他人可能會很複雜。 屬性會指定 OLE DB 物件的功能。 當您使用 ATL OLE DB 消費者精靈建立消費者或資料庫提供者精靈來建立提供者時，它會設定適當的物件屬性，以提供您一組標準的功能。 不過，如果精靈產生的取用者或提供者類別不支援所需的所有他們這麼做，您需要在類別的介面，請參閱[OLE DB 樣板程式庫](../../data/oledb/ole-db-templates.md)。 這些介面包裝原始的 OLE DB 介面，提供額外的實作，讓您使用起來更容易為您。  
  
 例如，如果您想要更新資料列集中的資料，但忘記使用精靈建立消費者時指定此，您可以指定功能事後藉由設定**DBPROP_IRowsetChange**和**DBPROP_UPDATABILITY**命令物件上的屬性。 然後，資料列集建立時，它會使`IRowsetChange`介面。  
  
 **您有舊版的程式碼使用其他資料存取技術 （ADO、 ODBC 或 DAO） 嗎？**  
 提供技術 （例如 ADO 元件使用 OLE DB 元件和 ODBC 程式碼移轉至 OLE DB） 的可能組合，涵蓋所有情況下是超出範圍的 Visual c + + 文件。 不過，許多文章涵蓋各種案例，有下列 Microsoft 網站：  
  
-   [Microsoft 說明和支援](http://go.microsoft.com/fwlink/p/?linkid=148218)  
  
-   [Microsoft 資料存取技術文件概觀](http://go.microsoft.com/fwlink/p/?linkid=148217)  
  
-   [Visual Studio 方案中心](http://go.microsoft.com/fwlink/p/?linkid=148215)  
  
-   [搜尋 Microsoft.com](http://search.microsoft.com/)  
  
 當您執行搜尋時，輸入關鍵字的組合最適合您的案例。例如： 如果您使用 ADO 物件具有 OLE DB 提供者，再試一次的布林值搜尋與**ADO 和 「 OLE DB 」**。 如果您想要將舊版的 DAO 程式碼移轉到 ODBC，選取 「 所有文字 」，並指定字串，例如**移轉 DAO**。  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 程式設計](../../data/oledb/ole-db-programming.md)   
 [OLE DB 程式設計概觀](../../data/oledb/ole-db-programming-overview.md)