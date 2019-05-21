---
title: 將字串儲存於 OLE DB 提供者內
ms.date: 05/09/2019
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
ms.openlocfilehash: f0ae4a3718858c4de5417aaf5a4f9bc0c0ba9984
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525346"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>將字串儲存於 OLE DB 提供者內

> [!NOTE] 
> Visual Studio 2019 及更新版本中未提供 ATL OLE DB 提供者精靈。


在 *Custom*RS.h 中，[ATL OLE DB 提供者精靈] 會建立一個預設的使用者記錄，稱為 `CWindowsFile`。 若要處理兩個字串，請修改 `CWindowsFile`，如下列程式碼所示：

```cpp
////////////////////////////////////////////////////////////////////////
class CCustomWindowsFile:
   public WIN32_FIND_DATA
{
public:
DWORD dwBookmark;
static const int iSize = 256;    // Add this
TCHAR szCommand[iSize];          // Add this
TCHAR szText[iSize];             // Add this
TCHAR szCommand2[iSize];         // Add this
TCHAR szText2[iSize];            // Add this

BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)

   PROVIDER_COLUMN_ENTRY_STR("Command", 6, szCommand)    // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text", 7, szText)          // Add this
   PROVIDER_COLUMN_ENTRY_STR("Command2", 8, szCommand2)  // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text2", 9, szText2)        // Add this
END_PROVIDER_COLUMN_MAP()

   bool operator==(const CCustomWindowsFile& am) // This is optional
   {
      return (lstrcmpi(cFileName, am.cFileName) == 0);
   }
};
```

資料成員 `szCommand` 和 `szText` 代表兩個字串，其中 `szCommand2` 和 `szText2` 包含額外的資料行 (如有需要)。 這個簡單的唯讀提供者不需要資料成員 `dwBookmark`，但稍後可用來新增 `IRowsetLocate` 介面；請參閱[增強簡單的唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)。 `==` 運算子會比較執行個體 (實作此運算子是選擇性的)。

當這麼做時，您可以新增[將字串讀入 OLE DB 提供者內](../../data/oledb/reading-strings-into-the-ole-db-provider.md)的功能。

## <a name="see-also"></a>另請參閱

[實作簡單唯讀提供者](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
