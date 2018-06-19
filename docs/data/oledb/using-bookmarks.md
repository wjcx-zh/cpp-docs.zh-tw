---
title: 使用書籤 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5aa16d5f2a3a02d0e9fd6bb3dd5de71494e81d4a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104483"
---
# <a name="using-bookmarks"></a>使用書籤
開啟資料列集之前，您必須告訴提供者想要使用書籤。 若要這樣做，請設定**DBPROP_BOOKMARKS**屬性**true**在您的屬性集。 提供者會擷取書籤做為資料行是零，因此您必須使用特殊的巨集`BOOKMARK_ENTRY`和`CBookmark`類別，如果您使用靜態存取子。 `CBookmark` 位置引數是以位元組為單位的書籤緩衝區的長度是範本類別。 所需的書籤緩衝區的長度，取決於提供者。 如果您使用的 ODBC OLE DB 提供者，如下列範例所示，緩衝區必須是 4 個位元組。  
  
```  
class CProducts  
{  
public:  
   CBookmark<4>   bookmark;  
  
   BEGIN_COLUMN_MAP(CProducts)  
      BOOKMARK_ENTRY(bookmark)  
   END_COLUMN_MAP()  
};  
  
CDBPropSet propset(DBPROPSET_ROWSET);  

propset.AddProperty(DBPROP_BOOKMARKS, true);  
  

CTable<CAccessor<CProducts>> product;  
product.Open(session, "Products", &propset);  
```  
  
 如果您使用`CDynamicAccessor`，在執行階段以動態方式配置的緩衝區。 在此情況下，您可以使用的特定的版本`CBookmark`，您沒有指定緩衝區長度。 使用函數`GetBookmark`從目前的記錄，擷取書籤，此程式碼範例所示：  
  
```  
CTable<CDynamicAccessor> product;  
CBookmark<>              bookmark;  
CDBPropSet propset(DBPROPSET_ROWSET);  
  

propset.AddProperty(DBPROP_BOOKMARKS, true);  

product.Open(session, "Products", &propset);  

product.MoveNext();  

product.GetBookmark(&bookmark);  
```  
  
 如需支援書籤的提供者資訊，請參閱[書籤的提供者支援](../../data/oledb/provider-support-for-bookmarks.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)