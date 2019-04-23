---
title: 使用者資料錄
ms.date: 11/04/2016
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
ms.openlocfilehash: b37835f1a3161edd10f61f9b4e76cfb5f558e07b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038511"
---
# <a name="user-record"></a>使用者資料錄

使用者記錄會提供代表資料列集的資料行資料的程式碼和資料結構。 在編譯時期或執行階段，就可以建立使用者記錄。 當您建立使用提供者**ATL OLE DB 提供者精靈**，精靈會建立預設使用者記錄看起來像這樣 (假設您指定的提供者名稱 [簡短名稱] *MyProvider*):

```cpp
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

OLE DB 提供者範本處理互動與用戶端上的所有 OLE DB 詳細資料。 若要取得回應所需的資料行資料，提供者會呼叫`GetColumnInfo`函式，您必須將它放在使用者記錄中。 您可以明確覆寫`GetColumnInfo`在使用者記錄中，比方說，藉由宣告它的.h 檔案中如下所示：

```cpp
template <class T>
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols) 
```

這相當於：

```cpp
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)
```

然後，實作`GetColumnInfo`使用者記錄的.cpp 檔案中。

PROVIDER_COLUMN_MAP 巨集協助建立`GetColumnInfo`函式：

- BEGIN_PROVIDER_COLUMN_MAP 定義函式原型和靜態陣列`ATLCOLUMNINFO`結構。

- PROVIDER_COLUMN_ENTRY 定義和初始化單一`ATLCOLUMNINFO`。

- END_PROVIDER_COLUMN_MAP 關閉陣列和函式。 它也會為陣列項目計數*pcCols*參數。

在執行階段，建立使用者記錄時`GetColumnInfo`會使用*pThis*參數，以接收的資料列集或命令的執行個體的指標。 命令和資料列集必須支援`IColumnsInfo`介面，以便從這個指標進行的資料行資訊。

`CommandClass` 和`RowsetClass`是命令，並使用使用者資料錄的資料列集。

如需如何覆寫的更詳細的範例`GetColumnInfo`在使用者記錄中，請參閱[動態決定資料行傳回給消費者](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
