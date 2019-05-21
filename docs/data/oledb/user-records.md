---
title: 使用者資料錄
ms.date: 05/09/2019
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
ms.openlocfilehash: c9c1126f0e8248f31ac739bb1d939f811bda678d
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525291"
---
# <a name="user-records"></a>使用者資料錄

> [!NOTE]
> Visual Studio 2019 及更新版本中未提供 ATL OLE DB 消費者精靈。 您仍然可以手動加入功能。 如需詳細資訊，請參閱[未使用精靈建立消費者](creating-a-consumer-without-using-a-wizard.md)。

若要使用靜態存取子 (也就是衍生自 `CAccessor` 的存取子)，您的消費者必須具有使用者記錄。 使用者記錄是一個 C++ 類別，其中包含要處理輸入或輸出的資料元素。 **ATL OLE DB 消費者精靈**會為您的消費者產生使用者記錄。 您可以將方法加入至使用者記錄，以供選擇性的工作 (例如處理命令) 使用。

下列程式碼會顯示處理命令的範例記錄。 在使用者記錄中，BEGIN_COLUMN_MAP 表示從提供者傳遞給消費者的資料資料列集。 BEGIN_PARAM_MAP 代表一組命令參數。 這個範例會使用 [CCommand](../../data/oledb/ccommand-class.md) 類別來處理命令參數。 對應項目中的資料成員代表要針對類別的每個執行個體位移至一個連續的記憶體區塊。 COLUMN_ENTRY 巨集會對應至提供者端的 PROVIDER_COLUMN_ENTRY 巨集。

如需 COLUMN_MAP 和 PARAM_MAP 巨集的詳細資訊，請參閱 [OLE DB 消費者範本的巨集](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)。

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

當您使用 **ATL OLE DB 消費者精靈**來產生消費者時，您可以選擇使用 OLE DB 範本或 OLE DB 屬性。 所產生的程式碼在每個案例中都不一樣。 如需此程式碼的詳細資訊，請參閱[消費者精靈產生的類別](../../data/oledb/consumer-wizard-generated-classes.md)。

## <a name="user-record-support-for-multiple-accessors"></a>使用者記錄支援多重存取子

如需對您必須使用多重存取子的案例進行詳細討論，請參閱[在資料列集上使用多重存取子](../../data/oledb/using-multiple-accessors-on-a-rowset.md)。

下列範例顯示已修改資料記錄，以在資料列集上支援多重存取子。 它不會使用 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP，而是會針對每個存取子改用 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md) 和 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)。 BEGIN_ACCESSOR 巨集會指定存取子數目 (從零位移)，以及存取子是否為自動存取子。 自動存取子會呼叫 `GetData`，在對 [MoveNext](../../data/oledb/crowset-movenext.md) 的呼叫上自動擷取資料。 非自動存取子則會要求您明確地擷取資料。 如果您要繫結到大型資料欄位 (例如點陣圖影像)，而且您可能不想針對每個記錄擷取這類欄位，請使用非自動存取子。

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

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)