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
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供者, 使用者資料錄"
  - "資料錄, 使用者"
  - "資料列集, 使用者資料錄"
  - "使用者資料錄"
  - "使用者資料錄, 說明"
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用者資料錄
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用者資料錄可提供程式碼，以及可表示資料列集的資料行資料之資料結構。  使用者資料錄可在編譯時間或執行階段建立。  當使用 ATL OLE DB 提供者精靈建立提供者時，精靈會建立如下所示的預設使用者資料錄 \(假設您已指定 "MyProvider" 的提供者名稱 \[簡短名稱\]\)：  
  
```  
class CWindowsFile:  
   public WIN32_FIND_DATA  
{  
public:  
  
BEGIN_PROVIDER_COLUMN_MAP(CMyProviderWindowsFile)  
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)  
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)  
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)  
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)  
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)  
END_PROVIDER_COLUMN_MAP()  
  
};  
```  
  
 OLE DB 提供者樣板會處理所有與用戶端互動相關的 OLE DB 細節。  為了取得回應所需的資料行資料，提供者會呼叫必須先放在使用者資料錄的 `GetColumnInfo` 函式。  您可明確地覆寫使用者資料錄內的 `GetColumnInfo`，例如以下列方式將它宣告在 .h 檔：  
  
```  
template <class T>  
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols)   
```  
  
 這種做法相當於：  
  
```  
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)  
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)  
```  
  
 您也必須在使用者資料錄的 .cpp 檔內實作 `GetColumnInfo`。  
  
 PROVIDER\_COLUMN\_MAP 巨集可協助您建立 `GetColumnInfo` 函式：  
  
-   BEGIN\_PROVIDER\_COLUMN\_MAP 定義函式原型 \(Prototype\) 和 **ATLCOLUMNINFO** 結構的靜態陣列。  
  
-   PROVIDER\_COLUMN\_ENTRY 定義並初始化單一 **ATLCOLUMNINFO**。  
  
-   END\_PROVIDER\_COLUMN\_MAP 關閉陣列和函式。  它也會在 `pcCols` 參數內放置陣列元素計數。  
  
 當使用者資料錄於 Run Time 建立時，**GetColumnInfo**  會使用 `pThis` 參數來接收資料列集或命令執行個體的指標。  命令和資料列集必須支援 `IColumnsInfo` 介面，這樣才能從這個指標取得資料行資訊。  
  
 **CommandClass** 和 **RowsetClass** 為使用這個使用者資料錄的命令和資料列集。  
  
 如需覆寫使用者資料錄 `GetColumnInfo` 的詳細範例，請參閱[動態決定傳回給消費者的資料行](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。  
  
## 請參閱  
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)