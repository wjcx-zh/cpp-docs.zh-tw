---
title: "使用書籤 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "書籤, OLE DB"
  - "OLE DB 提供者樣板, 書籤"
  - "OLE DB 提供者, 書籤支援"
  - "資料列集, 書籤"
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用書籤
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在您開啟資料列之前，您必須通知提供者您要使用書籤。  若要達成這個目的，請在屬性集 \(Property Set\) 中將 **DBPROP\_BOOKMARKS** 屬性設定為 **true**。  提供者會將書籤擷取為資料行零，所以如果使用靜態存取子 \(Accessor\)，就必須使用特殊巨集 `BOOKMARK_ENTRY` 和 `CBookmark` 類別。  `CBookmark` 是樣板類別，此類別的引數為書籤緩衝區的長度 \(以位元組為單位\)。  書籤所需的緩衝區長度依據不同提供者而有所差異。  如果您正在使用 ODBC OLE DB 提供者 \(如下列範例所示\)，該緩衝區必須是 4 個位元組。  
  
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
  
CTable<CAccessor<CProducts> > product;  
product.Open(session, "Products", &propset);  
```  
  
 如果您使用的是 `CDynamicAccessor`，Run Time 時才會動態地配置暫存區。  在這種情況下，您可以使用不需指定暫存區長度之特殊化版本 `CBookmark`。  依照下列程式碼範例，使用 `GetBookmark` 函式從目前資料錄擷取書籤：  
  
```  
CTable<CDynamicAccessor> product;  
CBookmark<>              bookmark;  
CDBPropSet propset(DBPROPSET_ROWSET);  
  
propset.AddProperty(DBPROP_BOOKMARKS, true);  
product.Open(session, "Products", &propset);  
product.MoveNext();  
product.GetBookmark(&bookmark);  
```  
  
 如需支援提供者書籤的詳細資訊，請參閱[提供者書籤支援](../../data/oledb/provider-support-for-bookmarks.md)。  
  
## 請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)