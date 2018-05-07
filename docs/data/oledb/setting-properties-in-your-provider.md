---
title: 在您的提供者中設定屬性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5d43e452d0fffcb4dc6eddcae722f8056dbd39dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="setting-properties-in-your-provider"></a>在提供者內設定屬性
找到想要的內容屬性群組和屬性識別碼。 如需詳細資訊，請參閱[OLE DB 屬性](https://msdn.microsoft.com/en-us/library/ms722734.aspx)中*OLE DB 程式設計人員參考*。  
  
 在精靈所產生的提供者程式碼，尋找對應至屬性群組的屬性對應。 屬性群組的名稱通常會對應至物件的名稱。 命令和資料列集屬性可以在命令或資料列集。資料來源物件中可以找到資料來源初始化屬性。  
  
 在屬性對應中，加入[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)巨集。 PROPERTY_INFO_ENTRY_EX 採用四個參數：  
  
-   屬性對應至識別碼屬性。 您必須從屬性名稱的前面移除前七個字元 ("DBPROP_")。 例如，如果您想要新增**dbprop_maxrows 時**，傳遞`MAXROWS`做為第一個項目。 如果這是自訂的屬性，傳遞完整的 GUID 名稱 (例如， `DBMYPROP_MYPROPERTY`)。  
  
-   Variant 類型的屬性 (在[OLE DB 屬性](https://msdn.microsoft.com/en-us/library/ms722734.aspx)中*OLE DB 程式設計人員參考*)。 輸入**VT_** 類型 (例如`VT_BOOL`或`VT_I2`) 對應到資料類型。  
  
-   旗標以指出屬性是否可讀取且可寫入以及它所屬的群組。 例如，下列程式碼表示屬於群組資料列集的讀/寫屬性：  
  
    ```  
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE  
    ```  
  
-   屬性的基底值。 這可能是**VARIANT_FALSE**布林輸入或零的整數類型，例如。 屬性會有此值，除非加以變更。  
  
    > [!NOTE]
    >  連接或鏈結至其他內容，例如書籤或更新某些屬性。 當取用者會將一個屬性設定為 true 時，可能也設定了另一個屬性。 OLE DB 提供者範本可支援此方法透過[cutlprops:: Onpropertychanged](../../data/oledb/cutlprops-onpropertychanged.md)。  
  
## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Microsoft OLE DB 提供者所忽略的屬性  
 Microsoft OLE DB 提供者會忽略下列 OLE DB 屬性：  
  
-   **Dbprop_maxrows 時**只適用於唯讀提供者 （也就是其中 DBPROP_IRowsetChange 和 DBPROP_IRowsetUpdate 是 false）; 否則會不支援這個屬性。  
  
-   **DBPROP_MAXPENDINGROWS**會被忽略; 提供者指定它自己的限制。  
  
-   **DBPROP_MAXOPENROWS**會被忽略; 提供者指定它自己的限制。  
  
-   **DBPROP_CANHOLDROWS**會被忽略; 提供者指定它自己的限制。  
  
## <a name="see-also"></a>另請參閱  
 [使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)