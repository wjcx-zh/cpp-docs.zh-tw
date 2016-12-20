---
title: "使用者資料錄 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COLUMN_ENTRY_MAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "存取子 [C++], 資料列集"
  - "存取子 [C++], static"
  - "BEGIN_ACCESSOR 巨集, 範例"
  - "BEGIN_ACCESSOR_MAP 巨集"
  - "CAccessor 類別, 範例"
  - "COLUMN_ENTRY 巨集"
  - "COLUMN_ENTRY_MAP 巨集"
  - "OLE DB 消費者樣板, 使用者資料錄"
  - "資料列集 [C++], 存取子"
  - "使用者資料錄, OLE DB 消費者樣板"
ms.assetid: 2de9e5eb-53ce-42b1-80fa-57d46600a80c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用者資料錄
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要使用靜態存取子 \(即是衍生自 **CAccessor** 的存取子\)，您的消費者必須有使用者資料錄。  使用者資料錄是一個 C\+\+ 類別，包含了處理輸入或輸出的資料項目。  ATL OLE DB 消費者精靈會替您的消費者產生使用者資料錄。  您可以將方法加入至使用者資料錄，以進行處理命令這類的選擇性工作。  
  
 下列程式碼顯示了一個可以處理命令的範例資料錄。  在使用者資料錄中，`BEGIN_COLUMN_MAP` 表示由提供者傳遞至消費者的資料列集。  `BEGIN_PARAM_MAP` 則表示一組命令參數。  這個範例使用了 [CCommand](../../data/oledb/ccommand-class.md) 類別來處理命令參數。  對應項中的資料成員會將位移 \(Offset\) 表示成類別的每個執行個體 \(Instance\) 之連續記憶體區塊。  `COLUMN_ENTRY` 巨集會對應至提供者端的 `PROVIDER_COLUMN_ENTRY` 巨集。  
  
 如需 **COLUMN\_MAP** 和 **PARAM\_MAP** 巨集的詳細資訊，請參閱 [OLE DB 消費者樣板巨集](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)。  
  
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
  
## 精靈產生的使用者資料錄  
 如果您要使用 ATL OLE DB 消費者精靈來產生消費者，請選擇使用 OLE DB 樣板或 OLE DB 屬性。  在每個情況中所產生的程式碼都不同。  如需此程式碼的詳細資訊，請參閱[消費者精靈產生的類別](../../data/oledb/consumer-wizard-generated-classes.md)。  
  
## 多重存取子的使用者資料錄支援  
 如需使用多重存取子所需的詳細案例探討，請參閱[在資料列集上使用多重存取子](../../data/oledb/using-multiple-accessors-on-a-rowset.md)。  
  
 下列範例顯示了一個為支援在資料列集的多重存取子而做了修改的使用者資料錄。  此處每個存取子使用的不是 `BEGIN_COLUMN_MAP` 和 `END_COLUMN_MAP`，而是 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md) 和 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)。  `BEGIN_ACCESSOR` 巨集可以指定存取子編號 \(距離零的位移\) 和存取子是否為自動存取子。  自動存取子會自動地在 [MoveNext](../../data/oledb/crowset-movenext.md) 呼叫時，呼叫 `GetData` 來擷取資料。  非自動存取子會要求您明確地擷取資料。  如果您正在繫結不想從中擷取每一筆資料的大型資料欄位 \(例如點陣圖影像\)，請使用非自動存取子。  
  
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
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)