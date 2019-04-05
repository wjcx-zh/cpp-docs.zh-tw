---
title: 使用書籤
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
ms.openlocfilehash: 579e67151858904e877a34bf30467e3cb97fe2c4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028489"
---
# <a name="using-bookmarks"></a>使用書籤

開啟資料列集之前，您必須告訴提供者想要使用書籤。 若要這樣做，請設定`DBPROP_BOOKMARKS`屬性，以 **，則為 true**在您的屬性集。 提供者會擷取書籤做為資料行的零，因此您必須使用特殊的巨集 BOOKMARK_ENTRY 和`CBookmark`類別，如果您使用靜態存取子。 `CBookmark` 是範本類別，其中的引數是以位元組為單位的書籤緩衝區的長度。 所需的書籤緩衝區的長度取決於提供者。 如果您使用的 ODBC OLE DB 提供者，如下列範例所示，緩衝區必須是 4 個位元組。

```cpp
class CProducts
{
public:
   CBookmark<4> bookmark;

   BEGIN_COLUMN_MAP(CProducts)
      BOOKMARK_ENTRY(bookmark)
   END_COLUMN_MAP()
};
```

然後，使用下列程式碼：

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_BOOKMARKS, true);

CTable<CAccessor<CProducts>> product;
CSession session;
product.Open(session, "Products", &propset);
```

如果您使用`CDynamicAccessor`，在執行階段動態設定緩衝區。 在此情況下，您可以使用特製化的版本`CBookmark`不指定緩衝區長度。 使用函式`GetBookmark`書籤擷取目前的記錄，此程式碼範例所示：

```cpp
CTable<CDynamicAccessor> product;
CBookmark<> bookmark;
CDBPropSet propset(DBPROPSET_ROWSET);
CSession session;

propset.AddProperty(DBPROP_BOOKMARKS, true);
product.Open(session, "Products", &propset);
product.MoveNext();
product.GetBookmark(&bookmark);
```

如需支援書籤的提供者資訊，請參閱[書籤的提供者支援](../../data/oledb/provider-support-for-bookmarks.md)。

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)