---
title: "使用者資料錄 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY_MAP
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: faead3ec85fc799abd26613979f7611c9159cc9b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="user-records"></a>使用者資料錄
若要使用靜態存取子 (也就是存取子，衍生自**CAccessor)**，您取用者都必須有使用者記錄。 使用者資料錄是 c + + 類別，包含要處理輸入或輸出的資料元素。 ATL OLE DB 消費者精靈產生使用者記錄您的消費者。 您可以將方法加入至選擇性工作，例如處理命令的使用者記錄中。  
  
 下列程式碼顯示範例記錄處理命令。 在使用者記錄中，`BEGIN_COLUMN_MAP`表示資料資料列集提供者從傳遞至取用者。 `BEGIN_PARAM_MAP` 代表一組命令參數。 這個範例會使用[CCommand](../../data/oledb/ccommand-class.md)類別來處理命令參數。 資料成員中對應項目代表一個連續類別的每個執行個體的記憶體區塊位移。 `COLUMN_ENTRY`巨集對應至`PROVIDER_COLUMN_ENTRY`巨集提供者端。  
  
 如需有關**COLUMN_MAP**和**PARAM_MAP**巨集，請參閱[OLE DB 消費者樣板的巨集](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)。  
  
```  
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
  
## <a name="wizard-generated-user-records"></a>精靈產生的使用者資料錄  
 如果您使用 ATL OLE DB 消費者精靈產生消費者時，您可以選擇使用 OLE DB 樣板或 OLE DB 屬性。 產生的程式碼是在每個案例不同。 如需此程式碼的詳細資訊，請參閱[消費者精靈產生的類別](../../data/oledb/consumer-wizard-generated-classes.md)。  
  
## <a name="user-record-support-for-multiple-accessors"></a>使用者資料錄支援多個存取子  
 您要使用多重存取子的案例的詳細討論，請參閱[資料列集上使用多重存取子](../../data/oledb/using-multiple-accessors-on-a-rowset.md)。  
  
 下列範例修改為支援多個存取子資料列集上的使用者資料錄。 而不是`BEGIN_COLUMN_MAP`和`END_COLUMN_MAP`，它會使用[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)和[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)針對每個存取子。 `BEGIN_ACCESSOR`巨集指定存取子數目 （從零位移） 以及存取子是 autoaccessor。 Autoaccessors 呼叫`GetData`來擷取資料，會自動在呼叫[MoveNext](../../data/oledb/crowset-movenext.md)。 非自動存取子會要求您明確地擷取資料。 如果您要繫結可能不想要擷取每一筆記錄的大型資料欄位 （例如點陣圖影像），請使用非自動存取子。  
  
```  
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
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)