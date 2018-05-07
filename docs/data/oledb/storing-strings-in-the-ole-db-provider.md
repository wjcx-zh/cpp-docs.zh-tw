---
title: 將字串儲存在 OLE DB 提供者 |Microsoft 文件
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
ms.openlocfilehash: a5ba289e7e53ba1bcaca550ba84c2d871d215306
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="storing-strings-in-the-ole-db-provider"></a>將字串儲存於 OLE DB 提供者內
MyProviderRS.h，在 ATL OLE DB 提供者精靈會建立稱為 「 預設使用者記錄`CWindowsFile`。 若要處理的兩個字串，請修改`CWindowsFile`或加入您自己的使用者記錄，如下列程式碼所示：  
  
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
  
 資料成員`szCommand`和`szText`兩個字串，代表與`szCommand2`和`szText2`必要時提供額外的資料行。 資料成員`dwBookmark`不需要使用這個簡單唯讀提供者，但稍後用來新增`IRowsetLocate`介面，請參閱 <<c4> [ 增強簡單唯讀只提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)。 `==`運算子會比較執行個體 （實作這個運算子是選擇性的）。  
  
 完成此動作後，您的提供者應該準備好要編譯及執行。 若要測試提供者，您需要取用者的比對功能。 [實作簡單消費者](../../data/oledb/implementing-a-simple-consumer.md)示範如何建立這類測試取用者。 提供者執行測試的取用者。 驗證，測試取用者正確的字串從提供者擷取當您按一下**執行**按鈕**測試消費者** 對話方塊。  
  
 當您已成功測試您的提供者時，您可以藉由實作額外的介面增強其功能。 範例所示[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)。  
  
## <a name="see-also"></a>另請參閱  
 [實作簡單唯讀提供者](../../data/oledb/implementing-the-simple-read-only-provider.md)