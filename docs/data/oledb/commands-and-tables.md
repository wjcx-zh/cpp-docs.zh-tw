---
title: "命令和資料表 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB consumer templates, table support
- CCommand class, OLE DB consumer templates
- commands [C++], OLE DB Consumer Templates
- CTable class
- CAccessorRowset class, command and table classes
- rowsets, accessing
- tables [C++], OLE DB Consumer Templates
- OLE DB consumer templates, command support
ms.assetid: 4bd3787b-6d26-40a9-be0c-083080537c12
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b5f849dc66746fe5740f47182a4fbacbc4d6c60d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="commands-and-tables"></a>命令和資料表
命令和資料表可讓您存取資料列集。也就是開啟資料列集、 執行命令和資料行繫結。 [CCommand](../../data/oledb/ccommand-class.md)和[CTable](../../data/oledb/ctable-class.md)類別具現化的命令和資料表的物件，分別。 這些類別衍生自[CAccessorRowset](../../data/oledb/caccessorrowset-class.md)如下圖所示。  
  
 ![CCommand 和 CTable](../../data/oledb/media/vccommandstables.gif "vccommandstables")  
命令和資料表類別  
  
 在上表中，`TAccessor`可以任何存取子類型列出[存取子類型](../../data/oledb/accessors-and-rowsets.md)。 *TRowset*可以任何資料列集型別列出[資料列集類型](../../data/oledb/accessors-and-rowsets.md)。 *TMultiple*指定結果類型 （單一或多個結果集）。  
  
 [ATL OLE DB 消費者精靈](../../atl/reference/atl-ole-db-consumer-wizard.md)可讓您指定是否要讓命令或資料表物件。  
  
-   您可以使用資料來源沒有命令，`CTable`類別。 您通常將它用於簡單的資料列集不指定任何參數，並不需要多重結果。 這個簡單的類別會開啟資料來源使用您指定的資料表名稱上的資料表。  
  
-   對於支援命令的資料來源，您可以使用`CCommand`類別。 若要執行命令時，呼叫[開啟](../../data/oledb/ccommand-open.md)於此類別。 或者，您可以呼叫`Prepare`準備您要多次執行命令。  
  
     **CCommand**有三個範本引數： 存取子類型、 資料列集型別，且結果型別 (`CNoMultipleResults`，根據預設，或`CMultipleResults`)。 如果您指定`CMultipleResults`、`CCommand`類別支援**IMultipleResults**介面，並處理多個資料列集。 [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832)範例示範如何處理多個結果。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)