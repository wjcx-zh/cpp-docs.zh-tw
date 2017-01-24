---
title: "將字串儲存於 OLE DB 提供者內 | Microsoft Docs"
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
  - "使用者資料錄, 編輯"
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將字串儲存於 OLE DB 提供者內
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 MyProviderRS.h 中，ATL OLE DB 提供者精靈會建立名為 `CWindowsFile` 的預設使用者資料錄。  若要處理這兩個字串，您可修改 `CWindowsFile` 或加入自己的使用者資料錄，程式碼如下所示：  
  
```  
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
  
 資料成員 `szCommand` 和 `szText` 代表兩個字串，若有需要，`szCommand2` 和 `szText2` 亦將提供其他的資料行。  這個簡單唯讀提供者並不需要 `dwBookmark` 資料成員，不過稍後在加入 `IRowsetLocate` 介面時將會使用到，請參閱[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)。  `==` 運算子可比較執行個體 \(是否實作此運算子是選擇性的\)。  
  
 完成之後，提供者即可開始編譯和執行。  若要測試提供者，您需要具有功能相符的消費者。  [實作簡單消費者](../../data/oledb/implementing-a-simple-consumer.md)會說明如何建立這類的測試消費者。  同時執行測試消費者和提供者。  當您按一下 \[測試消費者\] 對話方塊中的 \[執行\] 按鈕時，會驗證測試消費者可從提供者內擷取正確的字串。  
  
 當您已成功測試提供者後，可能會想藉由實作其他介面來增強功能。  範例顯示在[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)中。  
  
## 請參閱  
 [實作簡單唯讀提供者](../../data/oledb/implementing-the-simple-read-only-provider.md)