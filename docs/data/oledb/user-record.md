---
title: 使用者資料錄 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5c58807dac8ae320ee69c8e1a372fff5b9d3db02
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111051"
---
# <a name="user-record"></a>使用者資料錄
使用者資料錄提供代表資料列集的資料行資料的程式碼和資料結構。 在編譯時期或執行階段，就可以建立使用者資料錄。 當您建立使用 ATL OLE DB 提供者精靈提供者時，精靈會建立預設使用者記錄，看起來像這樣 （假設您指定"MyProvider"的提供者名稱 [簡短名稱]）：  
  
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
  
 OLE DB 提供者樣板處理用戶端之間的互動有關的所有 OLE DB 規格。 若要取得回應所需的資料行資料，提供者會呼叫`GetColumnInfo`函式，您必須將它放在使用者記錄中。 您可以明確覆寫`GetColumnInfo`使用者資料錄，比方說，藉由宣告它的.h 檔案中如下所示：  
  
```  
template <class T>  
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols)   
```  
  
 這相當於：  
  
```  
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)  
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)  
```  
  
 您也必須實作`GetColumnInfo`使用者資料錄的.cpp 檔案中。  
  
 PROVIDER_COLUMN_MAP 巨集協助建立`GetColumnInfo`函式：  
  
-   BEGIN_PROVIDER_COLUMN_MAP 定義函式原型和靜態陣列**ATLCOLUMNINFO**結構。  
  
-   PROVIDER_COLUMN_ENTRY 定義和初始化單一**ATLCOLUMNINFO**。  
  
-   END_PROVIDER_COLUMN_MAP 關閉陣列和函式。 它也會為陣列項目計數`pcCols`參數。  
  
 在執行階段，建立使用者資料錄時**GetColumnInfo**使用`pThis`參數，以接收的資料列集或命令的執行個體的指標。 命令和資料列集必須支援`IColumnsInfo`介面，以便可以從這個指標取得資料行資訊。  
  
 **CommandClass**和**RowsetClass**是命令，並使用使用者資料錄的資料列集。  
  
 如需如何覆寫的更詳細的範例`GetColumnInfo`使用者記錄，請參閱[動態決定資料行傳回給消費者](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)