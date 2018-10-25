---
title: 將字串儲存在 OLE DB 提供者 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 75f845027e5c629fe61b8cca6ab3f23306aa57bf
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053223"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>將字串儲存於 OLE DB 提供者內

CustomRS.h，在 [ATL OLE DB 提供者精靈] 會建立預設使用者記錄，稱為`CWindowsFile`。 若要處理的兩個字串，請修改`CWindowsFile`或新增您自己的使用者記錄，如下列程式碼所示：

```cpp
////////////////////////////////////////////////////////////////////////
class CAgentMan:
   public WIN32_FIND_DATA
   DWORD dwBookmark;              // Add this
   TCHAR szCommand[256];          // Add this
   TCHAR szText[256];             // Add this
   TCHAR szCommand2[256];         // Add this
   TCHAR szText2[256];            // Add this

{
public:
BEGIN_PROVIDER_COLUMN_MAP()
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command"), 1, 256, GUID_NULL, CAgentMan, szCommand)
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text"), 2, 256, GUID_NULL, CAgentMan, szText)
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command2"), 3, 256, GUID_NULL, CAgentMan, szCommand2)
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text2"),4, 256, GUID_NULL, CAgentMan, szText2)
END_PROVIDER_COLUMN_MAP()
   bool operator==(const CAgentMan& am) // This is optional
   {
      return (lstrcmpi(cFileName, wf.cFileName) == 0);
   }
};
```

資料成員`szCommand`並`szText`代表兩個字串中，使用`szCommand2`和`szText2`提供額外的資料行，如有需要。 資料成員`dwBookmark`不需要使用這個簡單唯讀提供者，但稍後用來新增`IRowsetLocate`介面，請參閱[增強簡單唯讀只提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)。 `==`運算子會比較執行個體 （實作這個運算子是選擇性的）。

當這麼做時，您的提供者應該可以編譯及執行。 若要測試的提供者，您需要有比對功能的取用者。 [實作簡單消費者](../../data/oledb/implementing-a-simple-consumer.md)示範如何建立這類測試取用者。 提供者執行測試的取用者。 驗證，測試取用者的適當字串從提供者擷取當您按一下 [**執行**按鈕**測試消費者**] 對話方塊。

當您已成功測試您的提供者時，您可以藉由實作額外的介面增強其功能。 範例所示[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)。

## <a name="see-also"></a>另請參閱

[實作簡單唯讀提供者](../../data/oledb/implementing-the-simple-read-only-provider.md)