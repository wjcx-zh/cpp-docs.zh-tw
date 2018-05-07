---
title: 存取 XML 資料 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data access [C++], XML data
- XML [C++], accessing data
- CXMLAccessor class, retrieving XML data
- data [C++], XML data access
- rowsets [C++], retrieving XML data
- CStreamRowset class, retrieving XML data
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f3abe00adee2a88d0414d688984232422a5bcfc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-xml-data"></a>存取 XML 資料
有兩種不同的方法，從資料來源擷取 XML 資料： 一個是使用[CStreamRowset](../../data/oledb/cstreamrowset-class.md)和其他用途[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)。  
  
|功能|CStreamRowset|CXMLAccessor|  
|-------------------|-------------------|------------------|  
|傳輸的資料量|同時從所有資料行和資料列擷取資料。|擷取所有資料行中的資料，但一次只有一個資料列。 您必須瀏覽資料列使用下列方法`MoveNext`。|  
|格式化字串|SQL Server 格式的 XML 字串，並將它傳送給取用者。|擷取原生格式 （提供者傳送的 Unicode 字串的要求） 的資料列集資料，並建立字串，包含 XML 格式的資料。|  
|控制格式設定|您有某種程度的控制權藉由設定某些 SQL Server 2000 特定屬性的 XML 字串格式化的方式。|您無法掌控所產生的 XML 字串的格式。|  
  
 雖然`CStreamRowset`提供多個整體有效率的方式，在 XML 格式，擷取資料的 SQL Server 2000 才支援。  
  
## <a name="retrieving-xml-data-using-cstreamrowset"></a>使用 CStreamRowset 擷取 XML 資料  
 您指定[CStreamRowset](../../data/oledb/cstreamrowset-class.md)中的資料列集類型為您`CCommand`或`CTable`宣告。 您可以使用它自己的存取子或沒有存取子，例如：  
  
```  
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;  
```  
  
 -或-  
  
```  
CCommand<CNoAccessor, CStreamRowset> myCmd;  
```  
  
 通常當您呼叫`CCommand::Open`(例如，指定`CRowset`為`TRowset`類別)，它會取得`IRowset`指標。 `ICommand::Execute` 傳回`IRowset`指標，它會儲存在`m_spRowset`隸屬`CRowset`物件。 這類方法`MoveFirst`， `MoveNext`，和`GetData`使用該指標來擷取資料。  
  
 相反地，當您呼叫`CCommand::Open`(但指定`CStreamRowset`為`TRowset`類別)，`ICommand::Execute`傳回`ISequentialStream`指標，它會儲存在`m_spStream`資料成員[CStreamRowset](../../data/oledb/cstreamrowset-class.md). 然後使用`Read`方法來擷取 XML 格式 （Unicode 字串） 資料。 例如:   
  
```  
myCmd.m_spStream->Read()  
```  
  
 SQL Server 2000 執行 XML 格式化，並傳回所有資料行和資料列集，以 XML 字串的所有資料列。  
  
 範例使用`Read`方法，請參閱中的 「 加入 XML 支援至消費者"[實作簡單消費者](../../data/oledb/implementing-a-simple-consumer.md)。  
  
> [!NOTE]
>  XML 支援使用`CStreamRowset`只適用於 SQL Server 2000，而且需要 SQL Server 2000 （安裝 MDAC） 的 OLE DB 提供者。  
  
## <a name="retrieving-xml-data-using-cxmlaccessor"></a>使用 CXMLAccessor 擷取 XML 資料  
 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)可讓您存取資料從資料來源，以字串資料時有不知道資料存放區的結構描述。 `CXMLAccessor` 運作方式類似`CDynamicStringAccessorW`不同之處在於前者會將轉換從資料存放區做為 XML 格式 （標記） 的資料存取的所有資料。 XML 標記名稱會儘可能密集地符合資料存放區的資料行名稱。  
  
 使用`CXMLAccessor`如同任何其他存取子類別，將它傳遞為範本參數，以`CCommand`或`CTable`:  
  
```  
CTable<CXMLAccessor, CRowset> rs;  
```  
  
 使用[GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md)一次擷取一個資料列的資料表的資料，以及巡覽資料列使用下列方法`MoveNext`，例如：  
  
```  
// Open data source, session, and rowset  
hr = rs.MoveFirst();  

while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )  
{  
    CStringW strRowData;  
    myCmd.GetXMLRowData(strRowData);  
  
    printf_s( "%S\n", strRowData );  
  
    hr = rs.MoveNext();  
}  
```  
  
 您可以使用[GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md)擷取為 XML 格式的字串資料的資料行 （資料類型） 資訊。  
  
## <a name="see-also"></a>另請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)