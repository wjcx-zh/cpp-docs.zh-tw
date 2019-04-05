---
title: 使用者資料錄
ms.date: 10/22/2018
f1_keywords:
- COLUMN_ENTRY_MAP
helpviewer_keywords:
- rowsets [C++], accessors
- COLUMN_ENTRY macro
- COLUMN_ENTRY_MAP macro
- user records, OLE DB consumer templates
- OLE DB consumer templates, user records
- CAccessor class, example
- BEGIN_ACCESSOR_MAP macro
- accessors [C++], rowsets
- accessors [C++], static
- BEGIN_ACCESSOR macro, example
ms.assetid: 2de9e5eb-53ce-42b1-80fa-57d46600a80c
ms.openlocfilehash: 5dd7be3eccd59dc1a5a0dc1cd6932ca1310627c0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041003"
---
# <a name="user-records"></a>使用者資料錄

若要使用的靜態存取子 (也就是存取子，衍生自`CAccessor`)，取用者必須有使用者記錄。 使用者資料錄是 c + + 類別，其中包含要處理輸入或輸出的資料元素。 **ATL OLE DB 消費者精靈**為取用者產生使用者記錄。 您可以將方法加入選擇性的工作，例如處理命令的使用者記錄。

下列程式碼顯示範例記錄處理命令。 在使用者記錄中，BEGIN_COLUMN_MAP 表示傳遞給取用者從提供者的資料列集。 BEGIN_PARAM_MAP 代表一組命令參數。 這個範例會使用[CCommand](../../data/oledb/ccommand-class.md)類別來處理命令參數。 對應項目中的資料成員代表一個連續的每個類別執行個體的記憶體區塊位移。 COLUMN_ENTRY 巨集對應至提供者端的 PROVIDER_COLUMN_ENTRY 巨集。

如需 COLUMN_MAP 和 PARAM_MAP 巨集的詳細資訊，請參閱[OLE DB 消費者樣板的巨集](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)。

```cpp
class CArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_COLUMN_MAP(CArtists)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
   COLUMN_ENTRY(3, m_nAge)
END_COLUMN_MAP()

// Parameter binding map
BEGIN_PARAM_MAP(CArtists)
   COLUMN_ENTRY(1, m_nAge)
END_PARAM_MAP()
};
```

## <a name="wizard-generated-user-records"></a>精靈產生的使用者記錄

如果您使用**ATL OLE DB 消費者精靈**產生取用者，您可以選擇使用 OLE DB 樣板或 OLE DB 屬性。 產生的程式碼是在每個案例不同。 如需有關此程式碼的詳細資訊，請參閱 <<c0> [ 消費者精靈產生的類別](../../data/oledb/consumer-wizard-generated-classes.md)。

## <a name="user-record-support-for-multiple-accessors"></a>使用者的多個存取子記錄的支援

的情況下，您需要使用多重存取子的詳細討論，請參閱 <<c0> [ 使用的資料列集上的多個存取子](../../data/oledb/using-multiple-accessors-on-a-rowset.md)。

下列範例顯示修改的資料列集上支援多個存取子的使用者記錄。 而不是 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP，它會使用[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)並[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)的每個存取子。 BEGIN_ACCESSOR 巨集指定存取子數目 （從零位移），以及存取子是 autoaccessor。 呼叫 Autoaccessors`GetData`來擷取資料，自動在呼叫[MoveNext](../../data/oledb/crowset-movenext.md)。 非自動存取子會要求您明確地擷取資料。 如果您要繫結到大型資料欄位 （例如點陣圖影像），您可能不想要擷取的每一筆記錄，請使用非自動存取子。

```cpp
class CMultiArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_ACCESSOR_MAP(CMultiArtists, 2)
   BEGIN_ACCESSOR(0, true)    // true specifies an auto accessor
    COLUMN_ENTRY(1, m_szFirstName)
    COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false)   // false specifies a manual accessor
    COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)