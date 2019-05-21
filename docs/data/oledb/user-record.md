---
title: 使用者資料錄
ms.date: 05/09/2019
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
ms.openlocfilehash: d6920a73f107f226cc31cb27fd15178f6d2f1c26
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525257"
---
# <a name="user-record"></a>使用者資料錄

> [!NOTE] 
> Visual Studio 2019 及更新版本中未提供 ATL OLE DB 提供者精靈。

使用者記錄會提供代表資料列集之資料行資料的程式碼和資料結構。 使用者記錄是在編譯時期或執行階段建立的。 當您使用 **ATL OLE DB 提供者精靈**建立提供者時，精靈會建立預設使用者記錄，看起來如下所示 (假設您指定 *MyProvider* 的提供者名稱 [簡短名稱])：

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

OLE DB 提供者範本會處理與用戶端互動的所有 OLE DB 特性。 若要取得回應所需的資料行資料，提供者會呼叫 `GetColumnInfo` 函式，您必須將該函式放在使用者記錄中。 您可以明確地覆寫使用者記錄中的 `GetColumnInfo`，例如，透過在 .h 檔案中宣告它，如下所示：

```cpp
template <class T>
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols) 
```

這相當於：

```cpp
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)
```

接著，在使用者記錄的 .cpp 檔案中實作 `GetColumnInfo`。

PROVIDER_COLUMN_MAP 巨集可協助建立 `GetColumnInfo` 函式：

- BEGIN_PROVIDER_COLUMN_MAP 會定義 `ATLCOLUMNINFO` 結構的函式原型和靜態陣列。

- PROVIDER_COLUMN_ENTRY 會定義並初始化單一 `ATLCOLUMNINFO`。

- END_PROVIDER_COLUMN_MAP 會關閉陣列和函式。 它也會將陣列元素計數放入 *pcCols* 參數中。

在執行階段建立使用者記錄時，`GetColumnInfo` 會使用 *pThis* 參數接收資料列集或命令執行個體的指標。 命令和資料列集必須支援 `IColumnsInfo` 介面，以便從這個指標取得資料行資訊。

`CommandClass` 和 `RowsetClass` 是使用使用者記錄的命令和資料列集。

如需有關如何覆寫使用者記錄中 `GetColumnInfo` 的更詳細範例，請參閱[動態決定傳回給消費者的資料行](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
