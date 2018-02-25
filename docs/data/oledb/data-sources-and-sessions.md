---
title: "資料來源和工作階段 |Microsoft 文件"
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
- data sources [C++], OLE DB
- connections [C++], data source
- OLE DB consumer templates [C++], data sources
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f294ab4fc8777dd6d9776958d9e6e16278efb02c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="data-sources-and-sessions"></a>資料來源和工作階段
下圖顯示連接和存取資料來源支援的類別。 每個類別為基礎的標準 OLE DB 元件實作。  
  
 ![資料來源和工作階段類別](../../data/oledb/media/vcdatasourcesessionclasses.gif "vcdatasourcesessionclasses")  
資料來源與工作階段類別  
  
 類別包括：  
  
-   [CDataSource](../../data/oledb/cdatasource-class.md)這個類別具現化的資料來源物件，以建立和管理透過 OLE DB 提供者的資料來源的連接。 資料來源取得資訊，例如資料來源地址和驗證資訊的連接字串的形式。  
  
     它也值得注意的是，協助程式類別[CEnumerator](../../data/oledb/cenumerator-class.md)常用來取得一份可用的提供者登錄在系統上建立任何連接之前。 這可讓您選取的提供者做為資料來源。 例如，**資料連結屬性**對話方塊會使用這個類別提供者清單填入上**提供者** 索引標籤。它相當於**SQLBrowseConnect**或**SQLDriverConnect**函式。  
  
-   [CSession](../../data/oledb/csession-class.md)這個類別具現化的工作階段物件，表示單一的存取工作階段資料來源。 不過，您可以在資料來源上建立多個工作階段。 每個工作階段，您可以建立資料來源存取資料的資料列集、 命令及其他物件。 工作階段會處理交易。  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)