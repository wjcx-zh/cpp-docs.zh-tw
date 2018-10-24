---
title: 命令和資料表 |Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 762623d6460404b4de85a45adaff7c5662bac258
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990006"
---
# <a name="commands-and-tables"></a>命令和資料表

命令和資料表可讓您存取資料列集;也就是開啟資料列集、 執行命令，並繫結資料行。 [CCommand](../../data/oledb/ccommand-class.md)並[CTable](../../data/oledb/ctable-class.md)類別具現化的命令和資料表的物件，分別。 這些類別衍生自[CAccessorRowset](../../data/oledb/caccessorrowset-class.md)如下圖所示。  
  
![CCommand 和 CTable](../../data/oledb/media/vccommandstables.gif "vccommandstables")  
命令和資料表類別  
  
在上表中，`TAccessor`可以任何存取子的型別列出[存取子類型](../../data/oledb/accessors-and-rowsets.md)。 `TRowset` 可以任何資料列集型別列出[資料列集類型](../../data/oledb/accessors-and-rowsets.md)。 `TMultiple` 指定結果型別 （單一或多個結果集）。  
  
[ATL OLE DB 消費者精靈](../../atl/reference/atl-ole-db-consumer-wizard.md)可讓您指定是否要讓命令或資料表的物件。  
  
- 針對資料來源，而不需要的命令，您可以使用`CTable`類別。 您通常將它用於簡單的資料列集未指定任何參數，而且需要多個結果。 這個簡單的類別會開啟使用您指定的資料表名稱的資料來源上的資料表。  
  
- 對於支援命令的資料來源，您可以使用`CCommand`類別。 若要執行命令時，呼叫[開啟](../../data/oledb/ccommand-open.md)這個類別上。 或者，您可以呼叫`Prepare`準備命令，您想要執行一次以上。  
  
     `CCommand` 有三個範本引數： 存取子類型、 資料列集類型，以及結果型別 (`CNoMultipleResults`，根據預設，或`CMultipleResults`)。 如果您指定`CMultipleResults`，則`CCommand`類別支援`IMultipleResults`介面，並會處理多個資料列集。 [DBVIEWER](https://github.com/Microsoft/VCSamples)範例示範如何處理多個結果。  
  
## <a name="see-also"></a>另請參閱  

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)